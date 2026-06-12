---
title: "Bug/Mem/Visualising tools for C"
date: 2010-10-25
forum: Programming Talk
---

### Post by Pithikos on 2010-10-25
I came across a great little tool called "decl" that helped me a lot in understanding pointers as it can take a declaration and explain it in plain english. For windows there is an other really great tool called bugfighter which notifies you if the array is overalling and more. Unfortunately I couldn't find it for Linux so that is quite sad.

Anyway, are there any other nifty programs that can help in learning C? Would love to know if there is a program with which you can see excactly what you are doing to the memory. Seeing that a pointer is in fact just a piece in the memory that for a value has an address would just be so damn helpful for newcomers.

---

### Post by spjackson on 2010-10-25
> **Pithikos said:**
> I came across a great little tool called "decl" that helped me a lot in understanding pointers as it can take a declaration and explain it in plain english. For windows there is an other really great tool called bugfighter which notifies you if the array is overalling and more. Unfortunately I couldn't find it for Linux so that is quite sad.

I've never heard of bugfighter. The webpage says "Plattform and compiler indipendent tool for Buffer Overflow detection during run-time". Despite being platform independent, the download is a Windows .exe.

The tools I'd use on Linux for this sort of thing are Valgrind, Nedmalloc, ElectricFence.
> 
Anyway, are there any other nifty programs that can help in learning C? Would love to know if there is a program with which you can see excactly what you are doing to the memory. Seeing that a pointer is in fact just a piece in the memory that for a value has an address would just be so damn helpful for newcomers.That sounds like what a debugger does, so gdb, with optionally a front-end to gdb such as ddd, or even Eclipse/CDT, if you are into that sort of thing.

---

