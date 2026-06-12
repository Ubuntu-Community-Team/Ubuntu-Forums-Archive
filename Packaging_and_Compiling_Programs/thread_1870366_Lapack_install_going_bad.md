---
title: "Lapack install going bad"
date: 2011-10-27
forum: Packaging and Compiling Programs
---

### Post by Dirich on 2011-10-27
Hello,

I recently upgraded to 11.10. I installed lapack and blas multiple times because of a linking problem: I did it in 11.04 via Symantec, then removed and re-isntalled in 11.10 once via the Software Center, once via apt-get.

When I compile my code with gcc I get this output:

/tmp/ccwbpwJg.o: In function `symm_tridiag_problem':
GNRcompute.c:(.text+0xff): undefined reference to `cos'
GNRcompute.c:(.text+0x15a): undefined reference to `dstev_'
collect2: ld returned 1 exit status

The problem with cos persists even if I add the -lm option in the compiler, which I usually don't because by adding -lblas and -llapack I implicitly link the math libraries too.

Also, the code compiles perfectly under 9.10 (at the moment I have no more any 10.# to try it on, but if memory serves me correctly, I had no problem before the upgrade).
So, the problem is not in the code or how I invoke the compiler.

By googling the issue, I found only cases where the problem was simply not using the -lblas and -llapack options, so I've run out of ideas.

From what I get, it's like the compiler doesn't see the lapacks I installed. So the problem is more ubuntu-related than programming-related, thus I'm here. Any idea what could have gone wrong?


Thanks!


P.S.
All installations were made after logging in on an Administrator account.

---

### Post by MadCow108 on 2011-10-27
> **Dirich said:**
> Hello,


/tmp/ccwbpwJg.o: In function `symm_tridiag_problem':
GNRcompute.c:(.text+0xff): undefined reference to `cos'
GNRcompute.c:(.text+0x15a): undefined reference to `dstev_'
collect2: ld returned 1 exit status

The problem with cos persists even if I add the -lm option in the compiler, which I usually don't because by adding -lblas and -llapack I implicitly link the math libraries too.


This is wrong. You must always explicitly link against all libraries you are directly using.
Beginning with ubuntu 11.10 and debian wheezy the flag --no-copy-dt-needed is used in ld by default.
This does not allow such implicit links.

Note you **must** place  -lm **behind** all objects needing it on the command line due to another flag new in ubuntu 11.10, ld --as-needed). See the billion other threads in this forum about this issue.

---

