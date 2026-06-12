---
title: "gcc with O2 and O3"
date: 2005-12-08
forum: Packaging and Compiling Programs
---

### Post by GoldBuggie on 2005-12-08
If I would compile with O2 and O3; I would get the O3 one right? They haven't done such a bad thing as checking the flags and choosing the only of of them?

and if i use cpu type flags? will the highest cpu get precedence?
Meaning if I have two flags one saying pentium3 the other saying 386 or something would the pentium3 flags get compiled?

---

### Post by gord on 2005-12-10
i think you would be better off just not confusing the compiler by giving it conflicting arguments.

---

### Post by jdong on 2005-12-10
Well, the later it comes in the gcc argument list, the more it takes precedence. For example:

gcc -O2 -O3 foo.c

would generate -O3 optimized binaries, while

gcc -O3 -O2 foo.c

would generate -O2 optimized binaries.


I do not  recommend O3 anyways, as it's almost always a speed **DROP** from -O2 due to missing L1/L2 cache limitations and generating substantially larger binaries.

---

### Post by GoldBuggie on 2005-12-10
Thank you jdong:D

---

### Post by MighMoS on 2005-12-12
[QUOTE=jdong]I do not  recommend O3 anyways, as it's almost always a speed **DROP** from -O2 due to missing L1/L2 cache limitations and generating substantially larger binaries.[/QUOTE]

If you wanted to do some benchmarks (I don't have anything to benchmark with) you could try "-O3 -fno-inline-functions", as I believe that its the function inlining that dramatically increases size, but there are some other optimizations in there (although depending on your version, it may varry.)

---

