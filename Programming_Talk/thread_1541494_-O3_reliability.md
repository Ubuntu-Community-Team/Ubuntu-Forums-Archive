---
title: "-O3 reliability"
date: 2010-07-29
forum: Programming Talk
---

### Post by mansourk on 2010-07-29
Hi,
When one uses -O3 to enhance the speed of running of a  c++ code , could he be sure as to get exactly the same answer as when he doesn't use -O3?

---

### Post by trent.josephsen on 2010-07-29
As long as your code has well-defined behavior -- no uninitialized value accesses, null pointer dereferencing, funky pointer arithmetic, or dependence on memory layout, to name a few common pitfalls -- -O3 should not affect how your program runs.  I have heard that there are corner cases where this is not true, but I don't know of any.  What you will want to look out for is loop unrolling, agressive inlining, and similar optimizations that are perfectly legal, but might break one of your implicit assumptions.  Make your assumptions explicit.

Whether -O3 is a good idea is debatable.  When I have fiddled with optimizations in the past, I have found that -O3 is not really preferable in terms of performance to -O2.  Obviously it will depend on the exact nature of the program and where it has bottlenecks.  In some cases I have heard that -O3 can actually make code slower (I haven't noticed this happen myself).  Don't apply a single optimizing flag across the board without measuring performance first.  If it takes 6 hours to compile and means a 0.01 second speed improvement, it's not worth it.

---

### Post by mansourk on 2010-08-02
Many thanks for your precise answer. it was of great help.

---

### Post by MadCow108 on 2010-08-02
when using an optimizing compiler there are some cases you have to watch out for.
the most common ones I remember are strict aliasing, signed integer wrap arounds and floating point arithmetic.
They also apply to lower optimization levels than O3

aliasing can be checked by newer gcc"s quite well (-Wstrict-aliasing=2) or be disabled -fno-strict-aliasing

signed integer wraps can be handled with -fwrapv or checked with -ftrapv but it is buggy on older gccs

concerning of floating point arithmetic you can get large differences depending on optimization (because of different representation size in fpu and memory, your result is highly dependent on how often it changes from fpu to emmory and vice versa).
But there are many flags in gcc to have a little control over it (ffast-math, ffloat-store, ...)

---

