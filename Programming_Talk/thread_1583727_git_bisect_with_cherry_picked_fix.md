---
title: "git bisect with cherry picked fix?"
date: 2010-09-28
forum: Programming Talk
---

### Post by ssam on 2010-09-28
i am trying to use git bisect to find a bug in the linux kernel. i think that 2.6.34 is good, and 2.6.35rc4 is bad, based on ubuntu kernel change logs. if i build 2.6.34 from linus' tree it works, but 2.6.35rc4 and 2.6.35rc5 fail with an unreleated regression. i have found the fix for the unreleated regression, but suspect that a large chunk of the bisect search space will not boot far enough for me to check them.

there are ways to skip some broken versions in git bisect, but they dont seem to help if the thing you want to find is in the middle of the broken.

suppose
v1 is good
v90 bring break a
v110 fixes break a
v140 brings break b
v160 break break c
v170 fixes break b
v200 is bad
you want to find the commit that breaks c.

break a is easy to skip over, and wont interfere with the search. but break b prevents you bisecting the range you need to find the break c.

so is there a way to cherrypick the fix in v170 while i am testing in range that has break b?

---

