---
title: "programming windows code on linux..."
date: 2010-02-17
forum: Programming Talk
---

### Post by phen on 2010-02-17
Dear all,

I am planning to develop a c++ library for some computer vision tasks. Its basically a wrapper around some OpenCV functions.

This library needs to run under windows xp and needs to compile with visual studio 8.

But I would like to start coding it using linux and gcc (because this is my OS..). Using the plain standard c++, this shouldnt be a problem until the hardware interfaces are needed, right? later, I want to switch to a VM.

Is there something I have to consider? Would it possible to make the whole library OS-independent?

I remember that VS uses _t** and _w** commands over and over... Its about unicode/UTF-8, do I have to care?

thanks

---

