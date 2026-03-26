# 🗺️ LeetCode 코딩테스트 로드맵 (2026.03.26 ~ 04.30)

> **목표**: 중견기업 이상 코딩테스트 통과  
> **기간**: 3/26(목) ~ 4/30(목) — 평일 1독, 주말 복기  
> **하루 시간**: 2시간  
> **전략**: 모르면 답 봐서라도 원리 이해 → 4월 말까지 핵심 Medium 2독 완성

---

## 📌 하루 루틴 (평일 2시간 고정)

| 블록 | 시간 | 내용 |
|------|------|------|
| A | 0~10분 | 어제 푼 문제 1개 **안 보고 재작성** (패턴 이름 말하기) |
| B | 10~30분 | 오늘 문제 1 — **10분 파악/접근법** → **10분 시도** |
| C | 30~50분 | 오늘 문제 1 — 안 풀리면 **답 확인 후 재작성 + 원리 메모** |
| D | 50~90분 | 오늘 문제 2 — B/C와 동일하게 진행 |
| E | 90~120분 | **복잡도 정리 + 핵심 1줄 패턴 노트 작성** |

> **10분 파악 체크리스트**  
> 1. 입력/출력 타입 확인  
> 2. 제약 조건 (배열 크기, 값 범위)  
> 3. 어떤 패턴인지 이름 말하기 (Hash Map? Two Pointers? BFS?)  
> 4. 시간복잡도 목표 설정 (O(n)? O(n log n)?)

---

## 📌 주말 복기 루틴 (2시간)

| 블록 | 시간 | 내용 |
|------|------|------|
| A | 0~60분 | 그 주 **못 풀었던 문제 / 헷갈렸던 문제** 안 보고 재풀기 |
| B | 60~90분 | 그 주 **Easy 문제** 5분 안에 풀리는지 확인 |
| C | 90~120분 | 주간 패턴 노트 정리 + 다음 주 문제 미리 파악 |

---

## 🗓️ WEEK 1 (3/26 ~ 3/28) — Hash Map / Array / Stack 기초

> **목표**: Easy 5개 + Medium 4개 / Map·Set이 만능 도구라는 감각 체득

---

### 3/26 (목) — Hash Map Easy + Medium

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~50분 | 242 | Valid Anagram | Hash Map | Easy | https://leetcode.com/problems/valid-anagram/ |
| 50~120분 | 49 | Group Anagrams | Hash Map | Medium | https://leetcode.com/problems/group-anagrams/ |

**핵심 패턴**

```
Valid Anagram    → 문자 빈도수 Map 비교
Group Anagrams  → 정렬된 문자열을 key로 Map 그룹핑
                  map.set(sorted, [...map.get(sorted), word])
```

**복기 체크**
- [ ] Valid Anagram: 빈도수 Map 안 보고 재작성
- [ ] Group Anagrams: `sorted = s.split('').sort().join('')` 키 생성 방식 기억

---

### 3/27 (금) — Hash Map / Hash Set Medium

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~60분 | 347 | Top K Frequent Elements | Hash + Bucket | Medium | https://leetcode.com/problems/top-k-frequent-elements/ |
| 60~120분 | 128 | Longest Consecutive Sequence | Hash Set | Medium | https://leetcode.com/problems/longest-consecutive-sequence/ |

**핵심 패턴**

```
Top K Frequent  → 빈도수 Map → 버킷 정렬 (index = 빈도수)
                  bucket[freq].push(num)
Longest Consec  → Set 구성 → num-1이 없는 것만 시작점으로 판별
                  if (!set.has(num - 1)) → 시작점
```

**복기 체크**
- [ ] Top K: 버킷 배열 역방향 순회로 상위 K개 뽑기
- [ ] Longest: 왜 시작점(num-1 없는 것)만 탐색하는지 설명 가능한가

---

### 3/28 (토) — Week 1 복기

| 시간 | 내용 |
|------|------|
| 0~15분 | 242 Valid Anagram — 안 보고 재작성 |
| 15~40분 | 49 Group Anagrams — 안 보고 재작성 |
| 40~65분 | 347 Top K Frequent — 안 보고 재작성 |
| 65~90분 | 128 Longest Consecutive — 안 보고 재작성 |
| 90~120분 | 패턴 노트 정리 + 다음 주 문제 미리 파악 |

**주간 패턴 노트**

```
Hash Map 핵심 공식:
  빈도수: freq.set(x, (freq.get(x) || 0) + 1)
  그룹핑: map.set(key, [...(map.get(key) || []), val])

Hash Set 핵심 공식:
  중복 제거: new Set(arr)
  시작점 판별: !set.has(num - 1)
```

---

## 🗓️ WEEK 2 (3/30 ~ 4/3) — Array / Two Pointers / Sliding Window

> **목표**: 10문제 / "포인터 2개면 된다"는 직관 + Sliding Window 감각 체득

---

### 3/30 (월) — Array Medium

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~60분 | 238 | Product of Array Except Self | Array | Medium | https://leetcode.com/problems/product-of-array-except-self/ |
| 60~120분 | 56 | Merge Intervals | Array | Medium | https://leetcode.com/problems/merge-intervals/ |

**핵심 패턴**

```
Product Except Self → 좌우 누적곱
  left[i]  = nums * ... * nums[i-1]
  right[i] = nums[i+1] * ... * nums[n-1]
  result[i] = left[i] * right[i]

Merge Intervals → 정렬 후 병합
  sort by start → 겹치면 end = Math.max(end, cur.end)
```

**복기 체크**
- [ ] Product: 나눗셈 없이 좌우 누적곱으로 O(n) 달성
- [ ] Merge: 정렬 후 prev.end >= cur.start 조건으로 병합

---

### 3/31 (화) — Two Pointers

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~60분 | 15 | 3Sum | Two Pointers | Medium | https://leetcode.com/problems/3sum/ |
| 60~120분 | 11 | Container With Most Water | Two Pointers | Medium | https://leetcode.com/problems/container-with-most-water/ |

**핵심 패턴**

```
3Sum             → 정렬 → i 고정 → left/right 수렴
                   중복 스킵: if (i > 0 && nums[i] === nums[i-1]) continue

Container Water  → 양끝에서 좁히기
                   짧은 쪽 포인터 이동 (긴 쪽 이동하면 넓이가 절대 안 커짐)
```

**복기 체크**
- [ ] 3Sum: 중복 스킵 조건 정확히 쓸 수 있는가
- [ ] Container: 왜 짧은 쪽을 이동하는지 설명 가능한가

---

### 4/1 (수) — Sliding Window

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~60분 | 3 | Longest Substring Without Repeating | Sliding Window | Medium | https://leetcode.com/problems/longest-substring-without-repeating-characters/ |
| 60~120분 | 567 | Permutation in String | Sliding Window | Medium | https://leetcode.com/problems/permutation-in-string/ |

**핵심 패턴**

```
Longest Substr  → Set + 가변 윈도우
                  중복 발견 시 left 이동하며 Set에서 제거

Permutation     → 고정 크기 윈도우 (s1.length)
                  빈도수 배열 비교
```

**복기 체크**
- [ ] Longest: Set 대신 Map으로 index 저장 → 더 빠른 left 점프 방식도 익히기
- [ ] Permutation: 고정 윈도우에서 빈도수 배열 비교 패턴

---

### 4/2 (목) — Sliding Window 심화

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~60분 | 424 | Longest Repeating Character Replacement | Sliding Window | Medium | https://leetcode.com/problems/longest-repeating-character-replacement/ |
| 60~120분 | 209 | Minimum Size Subarray Sum | Sliding Window | Medium | https://leetcode.com/problems/minimum-size-subarray-sum/ |

**핵심 패턴**

```
Char Replacement → 가변 윈도우 + 최대빈도 추적
                   (right - left + 1) - maxFreq <= k 이면 윈도우 유지

Min Size Subarray → 가변 윈도우 축소
                    sum >= target 이면 left 이동하며 최소 길이 갱신
```

**복기 체크**
- [ ] Char Replacement: `maxFreq`를 감소시키지 않아도 되는 이유 설명
- [ ] Min Size: 왜 가변 윈도우 축소 패턴인지 설명

---

### 4/3 (금) — Hard 도전 (답 봐도 OK, 원리 이해에 집중)

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~70분 | 42 | Trapping Rain Water | Two Pointers | Hard | https://leetcode.com/problems/trapping-rain-water/ |
| 70~120분 | 76 | Minimum Window Substring | Sliding Window | Hard | https://leetcode.com/problems/minimum-window-substring/ |

**핵심 패턴**

```
Trapping Rain   → 좌우 최대높이 추적
                  water += Math.min(maxLeft, maxRight) - height[i]

Min Window Sub  → 가변 윈도우 + 빈도수 Map + formed 카운터
                  모든 문자 충족 시 left 이동하며 최소 윈도우 갱신
```

**복기 체크**
- [ ] Trapping: 왜 min(maxLeft, maxRight)인지 설명
- [ ] Min Window: formed 카운터 패턴 이해

---

### 4/4 (토) — Week 2 복기

| 시간 | 내용 |
|------|------|
| 0~20분 | 15 3Sum — 안 보고 재작성 |
| 20~40분 | 3 Longest Substring — 안 보고 재작성 |
| 40~60분 | 238 Product Except Self — 안 보고 재작성 |
| 60~80분 | 424 Char Replacement — 안 보고 재작성 |
| 80~120분 | 주간 패턴 노트 정리 |

**주간 패턴 노트**

```
Two Pointers 핵심:
  양끝 수렴: while (left < right)
  3Sum: 정렬 + i 고정 + 중복 스킵

Sliding Window 핵심:
  고정 윈도우: right - left + 1 === k
  가변 윈도우: 조건 만족 시 left 이동
  공식: maxLen = Math.max(maxLen, right - left + 1)
```

---

## 🗓️ WEEK 3 (4/6 ~ 4/10) — BFS / DFS (★ 가장 중요)

> **목표**: 11문제 / BFS 템플릿 + DFS 템플릿 완전 암기

---

### BFS / DFS 템플릿 (매일 시작 전 5분 손으로 작성)

```ts
// BFS 템플릿
function bfs(grid: number[][], sr: number, sc: number): void {
    const queue: [number, number][] = [[sr, sc]];
    const visited = new Set([`${sr},${sc}`]);
    const dirs = [,[0,-1],,[-1,0]];[1]

    while (queue.length > 0) {
        const [r, c] = queue.shift()!;
        for (const [dr, dc] of dirs) {
            const nr = r + dr;
            const nc = c + dc;
            const key = `${nr},${nc}`;
            if (nr >= 0 && nr < grid.length
                && nc >= 0 && nc < grid.length
                && !visited.has(key)) {
                visited.add(key);
                queue.push([nr, nc]);
            }
        }
    }
}

// DFS 템플릿
function dfs(graph: number[][], node: number, visited: Set<number>): void {
    visited.add(node);
    for (const neighbor of graph[node]) {
        if (!visited.has(neighbor)) {
            dfs(graph, neighbor, visited);
        }
    }
}
```

---

### 4/6 (월) — BFS/DFS Grid 기초

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 0~10분 | — | BFS/DFS 템플릿 손으로 작성 | — | — | — |
| 10~65분 | 200 | Number of Islands | BFS/DFS Grid | Medium | https://leetcode.com/problems/number-of-islands/ |
| 65~120분 | 994 | Rotting Oranges | 멀티소스 BFS | Medium | https://leetcode.com/problems/rotting-oranges/ |

**핵심 패턴**

```
Number of Islands → DFS/BFS로 섬 탐색, 방문한 칸 '0' 처리
Rotting Oranges   → 모든 썩은 오렌지를 queue에 동시 추가 → 멀티소스 BFS
                    time++ 조건: queue에서 한 레벨씩 처리
```

**복기 체크**
- [ ] Islands: BFS/DFS 둘 다 구현 가능한가
- [ ] Rotting: 왜 멀티소스 BFS인지 설명

---

### 4/7 (화) — BFS Tree

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 0~10분 | — | BFS 템플릿 재작성 | — | — | — |
| 10~50분 | 104 | Maximum Depth of Binary Tree | DFS Tree | Easy | https://leetcode.com/problems/maximum-depth-of-binary-tree/ |
| 50~120분 | 102 | Binary Tree Level Order Traversal | BFS Tree | Medium | https://leetcode.com/problems/binary-tree-level-order-traversal/ |

**핵심 패턴**

```
Max Depth        → 재귀 DFS: 1 + Math.max(left, right)
Level Order BFS  → BFS + 레벨별 처리
                   const size = queue.length  ← 현재 레벨 크기 고정
                   for (let i = 0; i < size; i++) queue에서 하나씩 처리
```

**복기 체크**
- [ ] Max Depth: 재귀 종료 조건 `if (!node) return 0`
- [ ] Level Order: size 고정 후 for 루프가 핵심

---

### 4/8 (수) — Graph 위상정렬

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~65분 | 207 | Course Schedule | 위상정렬/사이클 감지 | Medium | https://leetcode.com/problems/course-schedule/ |
| 65~120분 | 210 | Course Schedule II | 위상정렬 순서 출력 | Medium | https://leetcode.com/problems/course-schedule-ii/ |

**핵심 패턴**

```
Course Schedule  → DFS + 방문 상태 3가지
                   0=미방문, 1=방문중, 2=완료
                   방문중(1)인 노드 다시 방문 → 사이클 → false

Course Schedule II → 위상정렬 (Kahn's Algorithm)
                     indegree[] 배열 → 0인 것부터 queue
                     처리하면서 indegree 감소 → 다시 0이 되면 queue 추가
```

**복기 체크**
- [ ] Course Schedule: 상태 3가지 DFS 패턴 설명
- [ ] Course Schedule II: indegree 배열 기반 위상정렬

---

### 4/9 (목) — Graph BFS 심화

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~65분 | 417 | Pacific Atlantic Water Flow | 역방향 DFS | Medium | https://leetcode.com/problems/pacific-atlantic-water-flow/ |
| 65~120분 | 542 | 01 Matrix | 멀티소스 BFS | Medium | https://leetcode.com/problems/01-matrix/ |

**핵심 패턴**

```
Pacific Atlantic → 경계에서 역방향 DFS (낮은 곳 → 높은 곳으로)
                   pacific, atlantic 두 visited Set → 교집합이 정답

01 Matrix       → 모든 0을 queue에 동시 추가 → BFS로 거리 계산
                  dist[r][c] = dist[nr][nc] + 1
```

**복기 체크**
- [ ] Pacific Atlantic: 왜 역방향 DFS인지 설명
- [ ] 01 Matrix: 멀티소스 BFS 패턴 Rotting Oranges와 비교

---

### 4/10 (금) — BST + DFS 심화

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~60분 | 98 | Validate Binary Search Tree | DFS + 범위 | Medium | https://leetcode.com/problems/validate-binary-search-tree/ |
| 60~120분 | 133 | Clone Graph | BFS + Map | Medium | https://leetcode.com/problems/clone-graph/ |

**핵심 패턴**

```
Validate BST    → DFS + min/max 범위 전달
                  dfs(node, -Infinity, Infinity)
                  왼쪽: dfs(left, min, node.val)
                  오른쪽: dfs(right, node.val, max)

Clone Graph     → BFS + Map<원본, 복사본>
                  방문한 노드는 Map에 저장 → 중복 생성 방지
```

**복기 체크**
- [ ] Validate BST: 범위 파라미터 DFS 패턴 설명
- [ ] Clone Graph: Map으로 노드 복사 추적하는 패턴

---

### 4/11 (토) — Week 3 복기

| 시간 | 내용 |
|------|------|
| 0~10분 | BFS/DFS 템플릿 2개 손으로 작성 |
| 10~35분 | 200 Number of Islands — 안 보고 재작성 |
| 35~60분 | 207 Course Schedule — 안 보고 재작성 |
| 60~85분 | 102 Level Order Traversal — 안 보고 재작성 |
| 85~120분 | 주간 패턴 노트 정리 |

**주간 패턴 노트**

```
BFS 핵심:
  레벨별 처리: const size = queue.length; for (let i = 0; i < size; i++)
  멀티소스: 시작점 여러 개를 queue에 동시 추가
  방향 배열: const dirs = [,[0,-1],,[-1,0]][1]

DFS 핵심:
  재귀 종료 조건 먼저 작성
  visited Set으로 중복 방문 방지
  트리: if (!node) return base값
```

---

## 🗓️ WEEK 4 (4/13 ~ 4/17) — Stack / Binary Search / Greedy

> **목표**: 10문제 / 스택=최근 것 먼저, 이분탐색=범위 절반 체화

---

### 4/13 (월) — Stack

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~50분 | 155 | Min Stack | Stack | Medium | https://leetcode.com/problems/min-stack/ |
| 50~120분 | 739 | Daily Temperatures | Monotonic Stack | Medium | https://leetcode.com/problems/daily-temperatures/ |

**핵심 패턴**

```
Min Stack        → 보조 스택(minStack)에 현재 최솟값 함께 저장
                   push 시: minStack.push(Math.min(minStack.top, val))

Daily Temperatures → 모노톤 스택 (더 큰 값을 만날 때 pop)
                     stack에 인덱스 저장
                     nums[stack.top] < nums[i] → pop → result[idx] = i - idx
```

**복기 체크**
- [ ] Min Stack: 보조 스택 패턴 설명
- [ ] Daily Temp: 모노톤 스택 "다음 큰 수" 패턴 설명

---

### 4/14 (화) — Stack 심화

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~60분 | 150 | Evaluate Reverse Polish Notation | Stack | Medium | https://leetcode.com/problems/evaluate-reverse-polish-notation/ |
| 60~120분 | 239 | Sliding Window Maximum | Monotonic Deque | Hard | https://leetcode.com/problems/sliding-window-maximum/ |

**핵심 패턴**

```
RPN              → 숫자면 push, 연산자면 pop 2개 계산 후 push
                   주의: b op a 순서 (먼저 pop한 게 오른쪽 피연산자)

Sliding Window Max → 모노톤 덱
                     덱 앞: 현재 윈도우 최댓값 인덱스
                     오래된 인덱스 앞에서 제거
                     작은 값 뒤에서 제거 (단조감소 유지)
```

**복기 체크**
- [ ] RPN: 연산자 처리 순서 주의 (`b op a`)
- [ ] Sliding Window Max: 덱 앞뒤 처리 조건 설명

---

### 4/15 (수) — Binary Search

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~60분 | 33 | Search in Rotated Sorted Array | Binary Search | Medium | https://leetcode.com/problems/search-in-rotated-sorted-array/ |
| 60~120분 | 153 | Find Minimum in Rotated Sorted Array | Binary Search | Medium | https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/ |

**핵심 패턴**

```
Search Rotated  → 어느 쪽이 정렬되어 있는지 판별 후 target 위치 결정
                  nums[lo] <= nums[mid] → 왼쪽 정렬됨
                  target이 [lo, mid) 범위면 hi = mid - 1, 아니면 lo = mid + 1

Find Min Rotated → nums[mid] > nums[hi] → min은 오른쪽 → lo = mid + 1
                   아니면 hi = mid
```

**복기 체크**
- [ ] Search Rotated: 조건 분기 4가지 경우 직접 그려보기
- [ ] Find Min: `nums[mid] > nums[hi]` 조건이 핵심

---

### 4/16 (목) — Greedy

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~60분 | 53 | Maximum Subarray | Greedy (카데인) | Medium | https://leetcode.com/problems/maximum-subarray/ |
| 60~120분 | 55 | Jump Game | Greedy | Medium | https://leetcode.com/problems/jump-game/ |

**핵심 패턴**

```
Maximum Subarray → 카데인 알고리즘
                   curr = Math.max(num, curr + num)
                   maxSum = Math.max(maxSum, curr)

Jump Game        → 최대 도달 범위 추적
                   maxReach = Math.max(maxReach, i + nums[i])
                   i > maxReach → return false
```

**복기 체크**
- [ ] Max Subarray: 왜 `Math.max(num, curr + num)`인지 설명
- [ ] Jump Game: maxReach 추적 방식 설명

---

### 4/17 (금) — Greedy 심화

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~65분 | 45 | Jump Game II | Greedy | Medium | https://leetcode.com/problems/jump-game-ii/ |
| 65~120분 | 134 | Gas Station | Greedy | Medium | https://leetcode.com/problems/gas-station/ |

**핵심 패턴**

```
Jump Game II    → 구간별 최대 도달 범위
                  현재 구간 끝(end)에 도달 시 점프 수+1, end = farthest 갱신

Gas Station     → 누적합이 0 미만이면 시작점을 다음으로 리셋
                  총합 >= 0이면 반드시 해가 존재
```

**복기 체크**
- [ ] Jump Game II: end와 farthest 두 변수 역할 구분
- [ ] Gas Station: 왜 시작점 리셋이 O(n)인지 설명

---

### 4/18 (토) — Week 4 복기

| 시간 | 내용 |
|------|------|
| 0~20분 | 739 Daily Temperatures — 안 보고 재작성 |
| 20~40분 | 33 Search Rotated Array — 안 보고 재작성 |
| 40~60분 | 53 Maximum Subarray — 안 보고 재작성 |
| 60~80분 | 155 Min Stack — 안 보고 재작성 |
| 80~120분 | 주간 패턴 노트 정리 |

**주간 패턴 노트**

```
Monotonic Stack 핵심:
  인덱스를 스택에 저장
  더 큰 값(또는 작은 값) 만날 때 pop
  결과: result[popped] = i - popped (거리 계산)

Binary Search 핵심:
  lo = 0, hi = n-1, mid = (lo+hi)>>1
  while (lo <= hi) → 정확한 값 탐색
  while (lo < hi)  → 범위 좁히기 (최솟값 등)

Greedy 핵심:
  현재 가능한 최선을 선택 → 미래를 보장
  카데인: Math.max(num, curr + num)
  도달 범위: Math.max(maxReach, i + nums[i])
```

---

## 🗓️ WEEK 5 (4/20 ~ 4/24) — Dynamic Programming

> **목표**: 10문제 / DP는 "점화식 세우기"에 집중

---

### DP 접근법 (매 문제 적용)

```
Step 1. dp[i]가 무엇을 의미하는지 한 줄로 정의
Step 2. 점화식: dp[i] = f(dp[i-1], dp[i-2], ...)
Step 3. 초기값: dp, dp 설정[1]
Step 4. 채우는 방향 결정
Step 5. 최종 답: dp[n] 또는 Math.max(...dp)
```

---

### 4/20 (월) — DP 1D 기초

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~40분 | 70 | Climbing Stairs | DP 1D | Easy | https://leetcode.com/problems/climbing-stairs/ |
| 40~120분 | 198 | House Robber | DP 1D | Medium | https://leetcode.com/problems/house-robber/ |

**핵심 패턴**

```
Climbing Stairs → dp[i] = dp[i-1] + dp[i-2] (피보나치)
House Robber    → dp[i] = Math.max(dp[i-1], dp[i-2] + nums[i])
                  훔치거나 vs 이전 집까지 최대값
```

**복기 체크**
- [ ] Climbing: dp[1]=1, dp[2]=2 초기값 설정
- [ ] House Robber: 점화식 유도 과정 설명

---

### 4/21 (화) — DP 1D 심화

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~65분 | 213 | House Robber II | DP 원형 | Medium | https://leetcode.com/problems/house-robber-ii/ |
| 65~120분 | 300 | Longest Increasing Subsequence | DP + 이분탐색 | Medium | https://leetcode.com/problems/longest-increasing-subsequence/ |

**핵심 패턴**

```
House Robber II → 원형 배열 → 두 번 풀기
                  Math.max(rob(0~n-2), rob(1~n-1))

LIS             → dp[i] = max(dp[j]+1) where nums[j] < nums[i]
                  O(n log n): patience sorting (tails 배열 + 이분탐색)
```

**복기 체크**
- [ ] HRobber II: 왜 두 번 풀어야 하는지 설명
- [ ] LIS: O(n²) 풀이 먼저 → O(n log n) 최적화 순서

---

### 4/22 (수) — DP 2D

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~65분 | 62 | Unique Paths | DP 2D | Medium | https://leetcode.com/problems/unique-paths/ |
| 65~120분 | 322 | Coin Change | DP 배낭 | Medium | https://leetcode.com/problems/coin-change/ |

**핵심 패턴**

```
Unique Paths    → dp[r][c] = dp[r-1][c] + dp[r][c-1]
                  위 + 왼쪽 경우의 수 합산

Coin Change     → dp[i] = Math.min(dp[i], dp[i - coin] + 1)
                  dp=0, 나머지 Infinity로 초기화
```

**복기 체크**
- [ ] Unique Paths: 1행/1열 초기화(모두 1) 이유 설명
- [ ] Coin Change: 배낭 문제 점화식 유도

---

### 4/23 (목) — DP 문자열

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~65분 | 5 | Longest Palindromic Substring | DP/확장 | Medium | https://leetcode.com/problems/longest-palindromic-substring/ |
| 65~120분 | 1143 | Longest Common Subsequence | DP 2D | Medium | https://leetcode.com/problems/longest-common-subsequence/ |

**핵심 패턴**

```
Longest Palindrome → 중심 확장 패턴
                     홀수: expand(i, i)
                     짝수: expand(i, i+1)

LCS              → dp[i][j] = s1[i-1]===s2[j-1] ? dp[i-1][j-1]+1
                                                  : Math.max(dp[i-1][j], dp[i][j-1])
```

**복기 체크**
- [ ] Palindrome: 홀수/짝수 두 경우 expand 모두 처리
- [ ] LCS: dp 표 직접 그려보기

---

### 4/24 (금) — DP 심화

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~65분 | 91 | Decode Ways | DP 1D | Medium | https://leetcode.com/problems/decode-ways/ |
| 65~120분 | 139 | Word Break | DP + Hash Set | Medium | https://leetcode.com/problems/word-break/ |

**핵심 패턴**

```
Decode Ways     → dp[i]: s[0..i-1]의 디코딩 방법 수
                  1자리 유효: dp[i] += dp[i-1]
                  2자리 유효: dp[i] += dp[i-2]

Word Break      → dp[i]: s[0..i-1]이 단어 분리 가능한가
                  dp[j]===true && wordSet.has(s[j..i]) → dp[i]=true
```

**복기 체크**
- [ ] Decode Ways: "01", "00" 등 invalid 케이스 처리
- [ ] Word Break: dp[0]=true 초기화 이유 설명

---

### 4/25 (토) — Week 5 복기

| 시간 | 내용 |
|------|------|
| 0~20분 | 198 House Robber — 안 보고 재작성 |
| 20~40분 | 322 Coin Change — 안 보고 재작성 |
| 40~60분 | 300 LIS — 안 보고 재작성 |
| 60~80분 | 62 Unique Paths — 안 보고 재작성 |
| 80~120분 | DP 점화식 정리 + 다음 주 준비 |

**주간 패턴 노트**

```
DP 핵심 공식:
  1D: dp[i] = f(dp[i-1], dp[i-2])
  2D: dp[i][j] = f(dp[i-1][j], dp[i][j-1], dp[i-1][j-1])
  배낭: dp[i] = Math.min/max(dp[i], dp[i - val] + 1)

DP 초기화 패턴:
  경우의 수: dp = 1
  최솟값: dp.fill(Infinity), dp = 0
  최댓값: dp.fill(0) 또는 dp.fill(-Infinity)
```

---

## 🗓️ WEEK 6 (4/27 ~ 4/30) — 구현/시뮬레이션 + 실전 모의고사

> **목표**: 4문제 + 모의고사 2회 / 시간 내 풀기 연습

---

### 4/27 (월) — 구현/시뮬레이션

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~65분 | 48 | Rotate Image | 구현 | Medium | https://leetcode.com/problems/rotate-image/ |
| 65~120분 | 54 | Spiral Matrix | 구현 | Medium | https://leetcode.com/problems/spiral-matrix/ |

**핵심 패턴**

```
Rotate Image    → 전치(Transpose) + 좌우 반전
                  transpose: matrix[i][j] ↔ matrix[j][i]
                  reverse: 각 행 reverse()

Spiral Matrix   → 방향 전환 시뮬레이션
                  top, bottom, left, right 경계 좁혀가며 순회
```

**복기 체크**
- [ ] Rotate: 전치 후 반전 순서 정확히 기억
- [ ] Spiral: 경계 변수 4개 관리 패턴

---

### 4/28 (화) — 구현/시뮬레이션 심화

| 시간 | # | 문제 | 유형 | 난이도 | 링크 |
|------|---|------|------|--------|------|
| 10~65분 | 73 | Set Matrix Zeroes | 구현 | Medium | https://leetcode.com/problems/set-matrix-zeroes/ |
| 65~120분 | 289 | Game of Life | 구현 | Medium | https://leetcode.com/problems/game-of-life/ |

**핵심 패턴**

```
Set Matrix Zeroes → 1행/1열을 마커로 활용 → 2회 패스
                    O(1) 공간: 첫 행/열에 0 여부 기록

Game of Life    → in-place 상태 인코딩
                  2: 1→0 (죽음), 3: 0→1 (탄생)
                  두 번째 패스에서 실제 값 복원
```

**복기 체크**
- [ ] Set Matrix: O(1) 공간 풀이에서 첫 행/열 처리 순서
- [ ] Game of Life: 인코딩 값 2, 3 의미 설명

---

### 4/29 (수) — 실전 모의고사 1회 ⏱️ 90분 타이머 ON

| 시간 | 문제 | 유형 | 난이도 | 링크 |
|------|------|------|--------|------|
| 0~20분 | 1. Two Sum | Hash Map | Easy | https://leetcode.com/problems/two-sum/ |
| 20~55분 | 200. Number of Islands | BFS/DFS | Medium | https://leetcode.com/problems/number-of-islands/ |
| 55~90분 | 322. Coin Change | DP | Medium | https://leetcode.com/problems/coin-change/ |

> **규칙**: 타이머 ON → 실제 코테처럼 진행 → 못 풀어도 90분에 종료  
> **이후 30분**: 못 푼 문제 풀이 확인 + 시간 배분 회고

---

### 4/30 (목) — 실전 모의고사 2회 ⏱️ 90분 타이머 ON

| 시간 | 문제 | 유형 | 난이도 | 링크 |
|------|------|------|--------|------|
| 0~20분 | 20. Valid Parentheses | Stack | Easy | https://leetcode.com/problems/valid-parentheses/ |
| 20~60분 | 56. Merge Intervals | Array | Medium | https://leetcode.com/problems/merge-intervals/ |
| 60~90분 | 207. Course Schedule | Graph | Medium | https://leetcode.com/problems/course-schedule/ |

> **규칙**: 동일하게 타이머 ON → 90분에 종료  
> **이후 30분**: 전체 6주 패턴 노트 최종 정리

---

## 📊 전체 문제 목록 요약

| 주차 | 기간 | 문제 수 | 유형 |
|------|------|---------|------|
| Week 1 | 3/26~3/28 | 4 | Hash Map, Hash Set |
| Week 2 | 3/30~4/3 | 10 | Array, Two Pointers, Sliding Window |
| Week 3 | 4/6~4/10 | 11 | BFS, DFS, Graph |
| Week 4 | 4/13~4/17 | 10 | Stack, Binary Search, Greedy |
| Week 5 | 4/20~4/24 | 10 | Dynamic Programming |
| Week 6 | 4/27~4/30 | 4 + 모의 2회 | 구현/시뮬레이션 |
| **합계** | | **49 + 모의 2회** | |

---

## 🏢 회사별 포커스 유형

| 회사 | 집중 유형 | 비고 |
|------|----------|------|
| **토스** | 구현/시뮬레이션, Hash, Stack | 쉬운 문제 빠르게 + Medium 2개 |
| **당근** | BFS/DFS, DP, 구현 | 실무 시나리오형 |
| **카카오** | 구현/시뮬레이션, BFS/DFS | 창의적 문제 해석 중요 |
| **네이버** | Graph, DP | 알고리즘 깊이 요구 |
| **쿠팡** | Array/Hash, Greedy | 실용적 시나리오 |
| **배민** | 구현, 시뮬레이션 | Medium 난이도 집중 |

---

## 🔧 JS 치트시트

```ts
// Map 빈도수 카운팅
const freq = new Map<string, number>();
for (const x of arr) freq.set(x, (freq.get(x) || 0) + 1);

// Set 중복 제거 & 존재 확인
const set = new Set(arr);
if (set.has(target)) { ... }

// 2차원 배열 BFS 방향
const dirs = [,[0,-1],,[-1,0]];[1]

// 이분탐색
let lo = 0, hi = arr.length - 1;
while (lo <= hi) {
    const mid = (lo + hi) >> 1;
    if (arr[mid] === target) return mid;
    else if (arr[mid] < target) lo = mid + 1;
    else hi = mid - 1;
}

// 모노톤 스택 (다음 큰 수)
const stack: number[] = [];
const result = new Array(arr.length).fill(-1);
for (let i = 0; i < arr.length; i++) {
    while (stack.length && arr[stack[stack.length-1]] < arr[i]) {
        result[stack.pop()!] = arr[i];
    }
    stack.push(i);
}

// DP 1차원 템플릿
const dp = new Array(n + 1).fill(0);
dp = 1; // 초기값
for (let i = 1; i <= n; i++) {
    dp[i] = Math.max(dp[i-1], dp[i-2] + val);
}
```
