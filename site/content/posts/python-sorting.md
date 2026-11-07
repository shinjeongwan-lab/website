+++
title = "Python 정렬 알고리즘 학습 기록"
date = "2026-11-07T00:00:00+09:00"
draft = false
description = "선택 정렬과 병합 정렬의 동작 원리 정리"
tags = ["Python", "알고리즘"]
categories = ["프로그래밍"]
+++

# Python 정렬 알고리즘 학습



이번 학습에서는 선택 정렬과 병합 정렬의 동작 원리를 살펴보았습니다.



## 1\. 선택 정렬



선택 정렬은 정렬되지 않은 구간에서 가장 작은 값을 찾아 앞쪽 원소와 교환하는 방식입니다.



**특징**

* 구현이 비교적 간단합니다.
* 시간 복잡도는 O(n²)입니다.
* 데이터가 많아질수록 비교 횟수가 증가합니다.
* \### 선택 정렬 Python 구현
* 
* ```python
* def selection\_sort(arr):
* &#x20;   n = len(arr)
* 
* &#x20;   for i in range(n):
* &#x20;       min\_idx = i
* 
* &#x20;       for j in range(i + 1, n):
* &#x20;           if arr\[j] < arr\[min\_idx]:
* &#x20;               min\_idx = j
* 
* &#x20;       arr\[i], arr\[min\_idx] = arr\[min\_idx], arr\[i]
* 
* &#x20;   return arr
* 
* numbers = \[5, 3, 8, 1, 2]
* print(selection\_sort(numbers))
* ```
* 
* 실행 결과: `\[1, 2, 3, 5, 8]`



## 2\. 병합 정렬



병합 정렬은 데이터를 작은 부분으로 나눈 다음 정렬하면서 다시 합치는 방식입니다.



**특징**

* 분할 정복 알고리즘을 사용합니다.
* 시간 복잡도는 O(n log n)입니다.
* 추가 메모리가 필요할 수 있습니다.
### 병합 정렬 Python 구현

```python
def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2

    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    result = []
    i = 0
    j = 0

    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1

    result.extend(left[i:])
    result.extend(right[j:])

    return result


numbers = [5, 3, 8, 1, 2]
print(merge_sort(numbers))
```

실행 결과: `[1, 2, 3, 5, 8]`



## 3\. 학습한 내용



두 알고리즘을 비교하면서 정렬 방법에 따라 실행 과정과 시간 복잡도가 달라진다는 점을 학습했습니다.

