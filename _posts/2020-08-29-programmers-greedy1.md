---
title: "[프로그래머스] 탐욕법lv1-체육복"
date: 2020-08-29 08:26:28 -0400
categories: 프로그래머스
tags : 
- 프로그래머스
- 문제풀이
---

탐욕법(Greedy)-lv1.체육복

탐욕 알고리즘은 

탐욕 알고리즘에 대한 더 자세한 설명은 다음 글을 참고하자. \
[탐욕 알고리즘]()



## ▷ 문제설명
[문제 링크]( https://programmers.co.kr/learn/courses/30/lessons/42862)



## ▷ 아이디어
> 1. 여분의 체육복을 도난받은 학생은 빌려줄 수 없으니, 빌려줄 수 있는 학생 목록에서 가장 먼저 지우자
> 2. i번째 학생이 체육복이 없다면, i-1번째 학생에게 먼저 물어봐야 더 많은 학생이 체육복을 빌릴 수 있다




## ▷ 풀이코드
```{Python}

def solution(n, lost, reserve):
    
    same = [x for x in lost if x in reserve]
    lost = list(set(lost)-set(same))
    reserve = list(set(reserve)-set(same))
    
    d = []
    for i in lost :
        
        if i in reserve:
            d.append(i)
            reserve.remove(i)

        elif i-1 in reserve:
            d.append(i)
            reserve.remove(i-1)

        elif i+1 in reserve:
            d.append(i)
            reserve.remove(i+1)

    answer = n - len(lost) + len(d)
    
    return answer
    
```