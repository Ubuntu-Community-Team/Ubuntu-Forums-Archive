---
title: "[SOLVED] set individual bits"
date: 2008-09-05
forum: Programming Talk
---

### Post by monkeyking on 2008-09-05
I'm having a somewhat funny problem.

Given a byte, how do I change individual bits with fewest bitoperations. 
That is, given bitpattern A, how do I set the bitvalues at B to the same as A. 

```

ex1.
xx01xxxx A
10101011 B
========
10011011
--------------
ex2.
10xxxxxx A
11101011 B
========
10011011
--------------
ex3.
xxxxxx00 A
10101011 B
========
10011000
--------------

```
I hope this makes sense.

I think this can be done in relative few bitoperations,
but I can't seem to track down to right way to do it.

thanks in advance

---

### Post by loganwm on 2008-09-05
You should be able to use a mask to do this, I'm not sure which numbers/operations you'll need to satisfy your situation, but look into bit masking.

If you post a bit more information I might be able to help out further.

---

### Post by monkeyking on 2008-09-06
Well after trying to explain what I wanted to do,
I managed to find a solution.
For anyone who might search the forums, the solution is.
(shifted value to input) OR (complement of (shiftmask) AND value)

but thanks

---

