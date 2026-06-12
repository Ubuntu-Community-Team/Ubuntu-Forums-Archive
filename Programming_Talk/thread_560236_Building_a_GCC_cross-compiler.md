---
title: "Building a GCC cross-compiler"
date: 2007-09-26
forum: Programming Talk
---

### Post by dwhitney67 on 2007-09-26
Does anyone have experience dealing with GCC cross-compilers on Ubuntu (or any other Linux distro)?

All of my systems are of the i686 architecture, however I need to build code using the i586 instruction set.  My target architecture is the Pentium 2 MMX.

I came across [Dan Kegel's cross-tool]("http://www.kegel.com/crosstool/") that provides the necessary tools to build a cross-compiler, however I am at a loss on how to use the compiler for building complex projects like the Linux kernel, X11, etc.  Sure, for "hello world" programs it is easy, but for the others it is not that trivial.

Does anyone have experience with something like this?  What issues can I expect if I am compiling/linking applications for the i586 architecture that are referencing libraries on my i686 host system?

---

### Post by Compyx on 2007-09-26
You do realize that a Pentium II MMX is an i686 processor? i586 applies to the original Pentium.

---

### Post by dwhitney67 on 2007-09-26
heh heh, your right.  I meant to say that my target is a Pentium MMX.

---

### Post by Compyx on 2007-09-26
Aha!

Well, although I have very little experience with cross-compiling (I've only used CC65 and cross-assemblers for the C64), I think you might want to take a look at the Gentoo documentation about cross-compiling. Although much of it may be Gentoo-specific, I think you should be able to gain some insight. Can't remember the URL, but [http://www.gentoo.org/]("http://www.gentoo.org/") should get you started.
Another option could be looking into the Linux From Scratch project, where they use a chroot-ed environment to build a new environment.

As for compiling a kernel for i586, since you're running a related architecture, you can just run 'make menuconfig' and pick the right CPU-family.

As for linking, I think if you use dynamic linking, not static linking, you should be okay.
But then again, I have very little experience with cross-compiling for 'modern' systems, so I could be way off here..

---

### Post by gnusci on 2007-09-26
What you need to learn is how to build a cross Tool Chain, here some links:

[http://en.wikipedia.org/wiki/GNU_toolchain](http://en.wikipedia.org/wiki/GNU_toolchain)
[http://www.parisc-linux.org/toolchain/index.html](http://www.parisc-linux.org/toolchain/index.html)
[http://ecos.sourceware.org/build-toolchain.html](http://ecos.sourceware.org/build-toolchain.html)
[http://www.kegel.com/crosstool/](http://www.kegel.com/crosstool/)

I did not check the links very deeply but they can give you some ideas.

---

### Post by dwhitney67 on 2007-09-26
Thanks.  I went through the Cross-Compiled Linux From Scratch (CLFS) exercise recently, however I found it is a pain to build from within an incomplete "system" once I chroot-ed to the new environment.

Many of the packages I need to build have numerous dependencies that are needed during compilation, but which are not needed during runtime.  Then there was X11R6.9.0 which always brought the system to its knees when compiling a particular file (I forgot the name).  But essentially all of the free memory was gobbled up, including about 85+% of the swap space.

So for now I am building my software on a Pentium MMX system running Fedora Core 5, however it would be nice to use a newer, faster architecture with a newer Linux distro.  It takes 12 hours to compile X11R6.9.0!!!

I remember in the past cross-compiling from a Sun Sparc to a PPC target.  However I haven't a clue as to what "magic" was employed to build that cross-compiler.  And the s/w being built was all proprietary; nothing off-the-shelf.  Life was easy back then.

---

### Post by fordp on 2007-12-05
Do you really need a cross compiler to build x86 apps on x86. I would guess not but it depends how the stock Ubuntu one has been set up.

I would be very confident that the stock GCC can build for at least 8086 and 80686.

Just my thoughts ;)

---

