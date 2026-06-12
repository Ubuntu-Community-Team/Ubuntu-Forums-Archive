---
title: "Extended Euclidean Algorithm Explanation Help and Modular Multiplicative Inverse"
date: 2009-03-31
forum: Programming Talk
---

### Post by Peter_APIIT on 2009-03-31
Hello to all, i have a hard time understand this these two topics.

I hope someone can clear my myth.

I do check the EEA page and did quite amount of research regarding this topic.

This is what i understand.

51x + 36y = gcd(a, b)
Rewrite them in quotient remainder theorem

Euclid Algorithm
51 = 1 x 36 + 15 52 / 36 = 3 r 6
36 = 2 x 15 + 6 36 / 15 = 2 r 6
15 = 2 x 6 + 3 15 / 6 = 2 r 3
6 = 2 x 3 + 0 6 / 2 = 3 r 0

Extended Euclidean Algorithm
=Take the last second solution

15 = 2 x 6 + 3
Rewrite the remainder at LHS

3 = 15 - 2 x 6
= 15 - 2 x (36 - 2 * 15)
= 5 * 15 - 2 * 36 (simplifying)(*)
= 5 * (51 - 36) - 2 * 36
= 5 * 51 - 7 * 36 (simplifying)(*)

Question
1. How modular multiplicative inverse related to EEA ?
Please show example.
2. How to simplify the equation(*) ?
3. How human hand calculation differ to code implementation ?

Thanks for your help.

---

### Post by Tony Flury on 2009-04-02
Sounds like homework.

We don't do your homework for you here.

If you have a specific question about a particular programm that you have written - please let us know.

---

