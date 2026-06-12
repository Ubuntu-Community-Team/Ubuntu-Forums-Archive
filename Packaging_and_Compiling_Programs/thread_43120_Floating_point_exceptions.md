---
title: "Floating point exceptions?"
date: 2005-06-20
forum: Packaging and Compiling Programs
---

### Post by Quest-Master on 2005-06-20
One pre-compiled and compiled-by-self program return these: Floating point exception.

The compiled-by-self returns it before launching, and the pre-compiled one just does it whenever it wants.

Now, absolutely NOBODY on any other distro's running these two programs get this same problem. Gentoo, Fedora, whatever.

I really need to figure out how to fix this.. I didn't come to Ubuntu to lose two of my most precious programs.

---

### Post by Quest-Master on 2005-06-22
Bump.. because otherwise I'm going to have to resort to trying out another Linux distribution in the meantime.

---

### Post by LordHunter317 on 2005-06-24
No way to tell without source code.  FPEs could be caused by literally thousands of different bugs.

---

### Post by jdong on 2005-06-24
hmm, what programs are these?

Tried a self-compiled kernel?

---

### Post by Quest-Master on 2005-06-24
[http://spheredev.net/files/sphere-linux.tar](http://spheredev.net/files/sphere-linux.tar)

Dependencies: SpiderMonkey, Corona, Audiere, SDL, SCons, and probably some more I don't remember atm. :\

Also, waste can be found at [http://waste.sf.net](http://waste.sf.net)
.
I'll try a self-compiled kernel though I don't know how it'd help.

---

### Post by RJARRRPCGP on 2005-07-15
[QUOTE=LordHunter317]No way to tell without source code.  FPEs could be caused by literally thousands of different bugs.[/QUOTE]

That also includes unstable processor overclocking! I always ran Prime95 to make sure that my processor is working properly. If there's a processor malfunction, Prime95 will fail!!! Usually, Prime95 is able to detect a problem with giving a "graceful exception" by scrolling an error message, which means that Prime95 detected a calculation problem. 

When the above is the cause, floating point exceptions usually occur when the processor is under stress. Crashes also would be random.

---

### Post by RJARRRPCGP on 2005-07-16
[QUOTE=Quest-Master]One pre-compiled and compiled-by-self program return these: Floating point exception.

The compiled-by-self returns it before launching, and the pre-compiled one just does it whenever it wants.

Now, absolutely NOBODY on any other distro's running these two programs get this same problem. Gentoo, Fedora, whatever.

I really need to figure out how to fix this.. I didn't come to Ubuntu to lose two of my most precious programs.[/QUOTE]

Have you ever ran Prime95 to test for stability problems? I do and recommend it to be ran for 24 hours! 

Also, do you have an Athlon 64 processor? If you do, there's possibly some batches of processor chips that are faulty!!! At least on a couple of message boards, some people are complaning about the Prime95 torture test failing on them, even when the processor isn't overclocked at all!!! The problem was reported the most with "Winchester" cores. 

[http://www.ocforums.com/showthread.php?t=390844](http://www.ocforums.com/showthread.php?t=390844)

---

