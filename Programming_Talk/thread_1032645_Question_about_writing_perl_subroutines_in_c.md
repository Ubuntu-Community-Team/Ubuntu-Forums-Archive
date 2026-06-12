---
title: "Question about writing perl subroutines in c"
date: 2009-01-06
forum: Programming Talk
---

### Post by 2weird on 2009-01-06
I have read about writing perl subroutines in c and plan to try it out.
One question i need to ask is, by writing the subroutines in c does that mean my sub routines will run with c like efficiency?

---

### Post by jimi_hendrix on 2009-01-06
try it out...make a routine that does:

get current time

do large amount of math

get current time

print difference in time

then run it in C and run it in Perl

---

### Post by snova on 2009-01-06
> **2weird said:**
> I have read about writing perl subroutines in c and plan to try it out.
One question i need to ask is, by writing the subroutines in c does that mean my sub routines will run with c like efficiency?

If you write it in C, you get the speed of C...

Tempered by any Perl code you call, of course. But that may be negligible.

---

### Post by 2weird on 2009-01-07
For those who would like to know: I have done some tests and it turns out that on first time run c code takes longer than perl. On the Second time it runs faster.

---

