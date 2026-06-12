---
title: "Compiling programs in linux for windows"
date: 2006-07-09
forum: Programming Talk
---

### Post by nazakthul on 2006-07-09
I have a problem 
I want use only native linux programs do make aplication wich can run on windows platform my question is how i can do that only with linux programs except java programing or run the windows compilers under wine or another emulation program

I do not want use MS programs or windows anymore but i need to program for this platform (in c c++ c#)because many peoble in my country use windows as OS and i need to program for it UNDER LINUX

I don t want to write the code under linux and compile it in win

Please help

Thanks in advance!

---

### Post by mostwanted on 2006-07-09
I think it's pretty stubborn of you to refuse to use Windows when you still want to develop for it; there's no shame in dual-booting, might as well do it.

But for cross-compiling the compiler is called mingw32. Then you could use wine for testing (if it's a simple app) or some kind of emulation which would still have to run Windows.

---

### Post by Max Luebbe on 2006-07-09
If you're willing to use Java, thats an easy fix to this problem.

If you want to do it in c/c++ try using the gtk windowing library, because it uses glib which allows for easy porting.

---

### Post by bieber on 2006-07-09
A similar question:  I just installed Mingw32 from Synaptic, how do I go about compiling a program as a Windows executable?

---

