---
title: "gcc march questions"
date: 2012-03-23
forum: Programming Talk
---

### Post by nolag on 2012-03-23
I know that march and mtune both try to optimize for a specific cpu (knowing cache size, instruction speed,  and that march will use instructions for that cpu that may not be compatible with i386 but there is one thing I want to confirm.  

Instruction wise (I don't care if it's slow on other computers I'm wondering if it will run), are all i686 the same?  Same question about all SSE 4.0.

---

### Post by Bachstelze on 2012-03-23
If you compile with -march=i686 it will run on any i686-compatible processor (from the Pentium Pro onwards). I guess the same is true for SSE4, it will run on any CPU that supports SSE4.

---

### Post by nolag on 2012-03-23
> **Bachstelze said:**
> If you compile with -march=i686 it will run on any i686-compatible processor (from the Pentium Pro onwards). I guess the same is true for SSE4, it will run on any CPU that supports SSE4.

Right, but lets say I do -march=corei7.  As far as I know core i7, i5, i7 (and duo?) are all SSE4, and none have instructions the others don't, so is it correct to assume that it would work on all of them, but optimize for the corei7?  I don't understand how you can optimize for i7 and i5 differently, as even within i7 (and i5) there are different cache sizes etc, and from what I understand both run the same instruction in the same number of cycles.  I guess my real question should have been what is the difference between -march=corei7 and -march=corei5 (or i3)?

---

### Post by Bachstelze on 2012-03-24
> **nolag said:**
> Right, but lets say I do -march=corei7.  As far as I know core i7, i5, i7 (and duo?) are all SSE4, and none have instructions the others don't, so is it correct to assume that it would work on all of them, but optimize for the corei7?

It's never correct to "assume" anything, but you can try and find out.

> I guess my real question should have been what is the difference between -march=corei7 and -march=corei5 (or i3)?

There is no -march=corei5 or i3 (or if there is, they are not documented), only corei7.

---

