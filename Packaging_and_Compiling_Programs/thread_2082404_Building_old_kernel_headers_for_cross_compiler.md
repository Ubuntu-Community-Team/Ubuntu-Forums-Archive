---
title: "Building old kernel headers for cross compiler"
date: 2012-11-09
forum: Packaging and Compiling Programs
---

### Post by stefangr1 on 2012-11-09
I have been trying to build a cross compiler for my Asus O'Play media player, which has a MIPS processor. I have compiled everything from source, e.g.: gmp, mpc, mpfr, binutils, gcc, linux headers and eglibc.

In principle, this seems to work. However, when I try to run the executable on the O'Play it gives a "kernel too old" error. The kernel headers I used for the cross-compiler were from Linux 2.6.32.37, while the O'Play is running 2.6.12.6.

So now I hope that my problem will be fixed by simply using older kernel headers (or should I also use an older version of eglibc?). 

However, I don't know how to compile the kernel headers of 2.6.12.6, because the Makefile included with that kernel source code doesn't know about headers_install. With newer questions, make headers_install gets everything right without having to do any configuration.

So my question: what is the simplest way to compile (or get) the kernel headers?

---

### Post by stefangr1 on 2012-11-10
I fixed it. The solution was actually very simple, I had to comiple eglibc with the correct --enable-kernel option. It needs to be lower than or equal to the kernel of the system it needs to run on. I had never compiled for an old system, so I thought it needed to be set to the kernel headers used to compile the cross-compiler.

---

