---
title: "[SOLVED] Linux Kernel"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by beanstalker on 2008-07-28
I have recently read several posts about kernel compilation. Could somebody please explain exactly what this process actually does and what the advantages to doing it are? Or direct me to some reading material on the subject. A clearer description of exactly what the kernel is would also be very much appreciated. I have a rough idea but something a little more accurate would be nice.

Cheers,
Jack :)

---

### Post by Nepherte on 2008-07-28
[http://en.wikipedia.org/wiki/Kernel_(computer_science](http://en.wikipedia.org/wiki/Kernel_(computer_science))

In general, you wouldn't need to compile your own kernel (unless you're *very* curious). The one that comes with Ubuntu should be sufficient. Most of the time you want to compile your own kernel if you need a very specific component or hardware support.

---

### Post by PmDematagoda on 2008-07-28
The kernel is pretty much the core of the entire OS, it handles input/output, processes, system calls, the lot.

Compiling a kernel is when you obtain the kernel source from somewhere and then compile it pretty much like a normal application(but the steps are slightly different). The advantages of compiling a kernel are:-
1) There maybe performance increases, especially if you configure the kernel to fit your PC/architecture.

2) You can patch the kernel source with other things such as GRsecurity, etc. which can extend the abilities of the kernel.

---

### Post by sdennie on 2008-07-28
One of the advantages is that you can tweak the kernel for specific needs.  In reality, I don't recommend compiling your own kernel unless you have some specific need that you are certain a different kernel will fix.  It's far more convenient to use the default Ubuntu kernel and get bug fixes and security updates from there.

For information and links about the kernel, the wikipedia page looks quite good: [http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

---

