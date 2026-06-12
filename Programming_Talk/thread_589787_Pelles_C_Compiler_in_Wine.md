---
title: "Pelles C Compiler in Wine"
date: 2007-10-24
forum: Programming Talk
---

### Post by xboxbman on 2007-10-24
Is it possible to run the Pelles C compiler through wine?  I like to use gcc in the command line, but my programming prof says any code we submit must be able to compile in Pelles.  I foolishly assumed that C libraries were universal regardless of the OS, then ended up getting 20% on a simple program when it wouldn't compile on Pelles because I used M_PI.  Apparently, Pelles doesn't recognize M_PI as being pre-defined in the math.h library.  So, now I need to test all my progs in Pelles before I submit them.

---

### Post by hecato on 2007-10-24
There more easy way is to try it ;) (like I know there are times when a new wine version don't let run a program that run in a prior version).

But I remember that I installed via wine, pelles, also DevCpp IIRC (also for other programs, try it, or search if there exist a "work around"), I also remember installing a program called LT Spice or some like that (not related much with programming, thus try to install, and try to run it that is the more secure way ;)).

---

### Post by xboxbman on 2007-10-25
i got it working pretty easily.  Except that when you hit the execute button in pelles, it doesn't.  But not biggy, cause I can just run the program through wine after it's compiled.

---

