---
title: "mapping a buffer with mmap"
date: 2016-09-15
forum: Programming Talk
---

### Post by fabian9i on 2016-09-15
I use Ubuntu 16.04.1 LTS.
I write a program in C++ and would like to know, if it is possible to map a buffer using mmap?

Or can mmap only map files. If that's the case, why?

I tried to map a buffer ([COLOR=#000080]**float**[/COLOR]* A = ([COLOR=#000080]**float**[/COLOR]*) malloc( M * N * [COLOR=#000080]**sizeof**[/COLOR]([COLOR=#000080]**float**[/COLOR]) ) with mmap but it failed. 

Thanks in advance!

Best regards,
Fabian

---

### Post by spjackson on 2016-09-16
Welcome to the forums.

I'm not sure that I understand what your underlying objective is, but perhaps the MAP_ANONYMOUS section of the mmap man page might help you.

---

