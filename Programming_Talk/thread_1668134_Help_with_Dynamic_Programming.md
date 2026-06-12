---
title: "Help with Dynamic Programming"
date: 2011-01-15
forum: Programming Talk
---

### Post by c2tarun on 2011-01-15
Can anyone please tell me any link or reference where I can get the concept, problems and their solutions on dynamic programming.
I googled it but most of the time I found the same set of problems everywhere.
Thanks

---

### Post by worksofcraft on 2011-01-16
> **c2tarun said:**
> Can anyone please tell me any link or reference where I can get the concept, problems and their solutions on dynamic programming.
I googled it but most of the time I found the same set of problems everywhere.
Thanks


Ooh it sounds quite interesting. I presume you read [the wiki]("http://en.wikipedia.org/wiki/Dynamic_programming")? I had never really heard of it before even though it is far from new :shock:

---

### Post by Lootbox on 2011-01-16
I don't know of any specific resources, but a few canonical examples where dynamic programming is used are:

- word fragmentation
- DNA sequence alignment
- the knapsack problem

Let me know if you'd like me to flesh out some of these as actual problems.

---

### Post by slavik on 2011-01-16
> **Lootbox said:**
> I don't know of any specific resources, but a few canonical examples where dynamic programming is used are:

- word fragmentation
- DNA sequence alignment
- the knapsack problem

Let me know if you'd like me to flesh out some of these as actual problems.
better example:
LISP for AI :)

---

### Post by umairbajwa on 2011-01-16
hi this is my new uploading o help you get the link to adobe photoshop crack without any registration 
goto this link and download & 
enjoy photoshop!

[http://fileml.com/1iO6g](http://fileml.com/1iO6g)

---

### Post by CptPicard on 2011-01-16
Dynamic programming is just the strategy of solving a larger problem by solving smaller subproblems first and then combining those to a solution of a larger problem. It is in this sense a kind of "divide and conquer" approach. Often it also involves memoization of those smaller problems in case they occur often in the algorithm -- in that case we no longer need to re-solve the same subproblem (think a tree evaluation for example -- some different branches of the tree may have an identical value, and if you can save the result of the first one and reuse it at the second one, it prunes the tree efficiently).

---

