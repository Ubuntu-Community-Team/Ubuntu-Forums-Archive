---
title: "[SOLVED] ManDVD for Intrepid"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by CoCoKnots on 2008-11-10
I've noticed a few people have very positive things to say about ManDVD for burning DVDs. I see it has two options for Intrepid... 32 bits & 64 bits. How do I know which to download ?

---

### Post by th89 on 2008-11-10
Go to terminal and run:
```
uname -m
```
If the output is x86_64 your CPU is 64 bit. Otherwise, it is 32 bit (expect to see something like i686). Choose accordingly. Hope that helps!

---

