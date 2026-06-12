---
title: "[SOLVED] How Do I Interpret This?"
date: 2008-05-21
forum: Programming Talk
---

### Post by Lster on 2008-05-21
Hi!

I'm attempting Project Euler Problem 66 but find the wording particularly difficult to understand. It uses the term "minimal solution" which is confusing me the most. I can find loads of solutions but none work!

Thank you,
Lster

---

### Post by Npl on 2008-05-21
for a given D, find all (x,y) that satisfy x^2 + D*y^2. Then pick the smallest (positive) x from those tuples. Thats the "minimal Solution in x", call it x(D)

You then need to do the same for each D <= 1000 and then pick the largest value of a x(D)

---

### Post by Lster on 2008-05-21
Thanks; that's cleared everything up!

---

