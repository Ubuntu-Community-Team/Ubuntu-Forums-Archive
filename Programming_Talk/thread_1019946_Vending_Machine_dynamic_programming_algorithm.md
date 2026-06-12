---
title: "Vending Machine dynamic programming algorithm"
date: 2008-12-23
forum: Programming Talk
---

### Post by Barbas06 on 2008-12-23
Hey guys I'm trying to solve a problem similar to the one mentioned [here]("http://ubuntuforums.org/showthread.php?t=1005608").
In this variation we have a vending machine that only takes 10, 20, and 50 cent coins and we want to find how many ways there are to feed the machine with n cents where n is a multiple of 10.
The solution given in the thread mentioned is using recursion to solve the problem and I'm trying to find an algorithm (so just pseudocode will be just fine) that uses Dynamic Programming.
I guess the idea will be to use memoization so we don't need to recompute the permutations(?). For example if we already know that we can split a 50 cent coin into 2 20s and a 10,  or 5 10s or whatever, we can store this in an array for later use when they come up again in the computation tree.
Thanks!

---

