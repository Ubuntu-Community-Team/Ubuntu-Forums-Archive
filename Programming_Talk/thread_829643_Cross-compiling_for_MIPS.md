---
title: "Cross-compiling for MIPS"
date: 2008-06-15
forum: Programming Talk
---

### Post by Phenax on 2008-06-15
Not directly programming-related, but I thought you guys might know.

I have a router (RTP300) that uses the TI-AR7V (mips32) chip-set and I'd like to compile some software for it. It uses some old 2.4.x kernel and uClibc 0.9.19. I've searched the internet for resources on cross-compiling - what's the easiest way? Just compiling binutils/uclibc/gcc with a MIPS target and compile it with that? There are a few scripts like crosstools but none seem to easily support uClibc.

---

### Post by pdwerryhouse on 2008-06-15
Have a look at [Scratchbox]("http://scratchbox.org/"). While most of it seems to be targeted at the arm architecture, they do have experimental MIPS builds...

---

### Post by John164918a on 2008-09-21
Hello, I am trying to do almost exactly the same thing with exactly the same processor, not really sure what linux my router runs though. Its a Netgear DG834G and I've just figured out how to upload and download files to it using its http server with my firefox and its wget with my GPROFTPD.

I thought I'd start by trying to cross-compile 'hello world' for it but I'm not really sure how to do it. The gcc man page says you can specify the target machine with -b but my gcc (4.2.3) doesnt recognise that option.

There must be some debian package in someones repository that gives gcc the capability to cross compile.

Everything I've found about cross compilation seems to be about how to build toolchains so you can compile your own kernel. I only want to compile Hello World, it must already have its own libraries for doing stdio.h! How hard can it be?

Do I really have to compile my own compiler to compile a kernel and a compiler to compile another kernel and a compiler to compile a compiler to compile hello world? ARRRRRGGGGGGGHHHHHHHH!!!!!

Please help me!

:confused:

John

---

