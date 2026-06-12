---
title: "Java |  operator?"
date: 2007-09-29
forum: Programming Talk
---

### Post by keeler1 on 2007-09-29
I am writing a program for a college class of mine and I became quite curious as to what the | operator does in Java.  

What i needed was some int1 == (int2 or int3).

I know the || operator needs a boolean expression on both sides.  But the single | did not have errors.  

Will the syntax int1 == (int2 | int3) check to see if int1 == int2 || int1 == int3?

---

### Post by CptPicard on 2007-09-30
No, it's a binary or. It takes the bits of your ints and applies or to each respective pair of them.

So like... 1001 | 0101 = 1101, for example... of course an int has more bits.

---

