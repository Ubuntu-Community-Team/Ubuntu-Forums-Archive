---
title: "Simple MIPS multiplication gives &quot;address out of range&quot;"
date: 2009-11-15
forum: Programming Talk
---

### Post by blazemore on 2009-11-15
Hi, for an assignment I have to multiply two integers, check for overflow, and then print the result if no overflow occurs.

The overflow checking works, but if it has to output, say 10 * 20 = 200, it just says runtime exception, address out of range.
It's weird because I go through step by step and see that register $a0 contains the value 200, but when it gets to the syscall it just gives an error!
Or is 200 too big an integer to display? Would I have to move it to coprocessor 1 or something?

---

