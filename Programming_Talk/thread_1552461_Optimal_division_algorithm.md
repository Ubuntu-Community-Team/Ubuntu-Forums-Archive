---
title: "Optimal division algorithm"
date: 2010-08-13
forum: Programming Talk
---

### Post by SpinningAround on 2010-08-13
I trying to solve a problem, but can't find a proper algorithm to do so or if it's even possible.

The problem is as follow. I have a length, this length is going to be divided into different values in such a way that a small or no quotient is left.

Example:
Length is 11 and I want it to be divided into items with length 2, 3 and 4. Optimal division for this would be 4 4 3, 2 2 4 3, 2 2 2 2 3.

---

### Post by Bachstelze on 2010-08-13
Sounds very much like the [knapsack problem]("http://en.wikipedia.org/wiki/Knapsack_problem").

---

### Post by SpinningAround on 2010-08-13
> **Bachstelze said:**
> Sounds very much like the [knapsack problem]("http://en.wikipedia.org/wiki/Knapsack_problem").

Thanks, seem to be what I'm looking for. The interesting part will be to solve it, finally I get some use of the mathematics :P

---

### Post by Lootbox on 2010-08-13
Or if efficiency is not a concern and the problem is small enough, you can just brute force it by recursively exhausting all possibilities.

---

