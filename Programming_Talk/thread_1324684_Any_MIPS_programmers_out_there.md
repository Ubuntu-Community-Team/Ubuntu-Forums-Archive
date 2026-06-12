---
title: "Any MIPS programmers out there?"
date: 2009-11-12
forum: Programming Talk
---

### Post by blazemore on 2009-11-12
I'd really appreciate some help with this one
No. 1, yes this is an assignment.
No.2 I've been ill with horrible flu for the last 2 weeks and haven't been able to do this, and this is the only question I can't do.

Basically, how do you read in two integers, multiply them, and then check for overflow, printing either the answer or "overflow".
TBH I can't even do the first part, let alone the check for overflow. (My lecturer has a very strong accent!)

Oh and btw the result should be representable with a signed 32 bit number (or an overflow exception, the program should throw)

Help is much appreciated!

---

### Post by Can+~ on 2009-11-12
To ask user input:

[PHP]li $v0, 5
syscall
move <where do you want it>, $v0 [/PHP]

And probably there's an instruction to check for the Overflow bit.

---

