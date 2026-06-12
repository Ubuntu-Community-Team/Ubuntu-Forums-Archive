---
title: "[SOLVED] [Python] weird error message"
date: 2008-10-27
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-27
I got this error message:
> 
Fatal Python error: (pygame parachute) Segmentation Fault

What?? What parachute? I don't get it. :confused:

That error has absolutely no point.

Not even a line number O.o

---

### Post by snova on 2008-10-27
I have no idea what a parachute is in this context. Nor do I want to use one in any other context.

The only thing that would cause Python to segfault would be a C module somewhere with bugs. Probably PyGame.

Try to figure out where it's happening, by adding some extra print statements. If you can't fix it, ask the PyGame developers about it (it may be a bug).

---

### Post by days_of_ruin on 2008-10-27
Yeah it means some bad error in the module happened.If you post your code
I might be able to tell you whats doing it.

---

### Post by crazyfuturamanoob on 2008-10-27
> **days_of_ruin said:**
> Yeah it means some bad error in the module happened.If you post your code
I might be able to tell you whats doing it.

The problem is - It doesn't give me line numbers and I got 400 lines of code. Plus 2 other libraries I have written myself, that might make the error. Will I post everything?

---

### Post by pmasiar on 2008-10-27
> **crazyfuturamanoob said:**
> The problem is - It doesn't give me line numbers and I got 400 lines of code. Plus 2 other libraries I have written myself, that might make the error. Will I post everything?

To make life easier for us, you may want to eliminate all the code which is NOT causing the error (comment out a piece and see if still error) - and by the time you are done you maybe solved it by yourself 8-)

---

### Post by crazyfuturamanoob on 2008-10-28
Ok I accidentally solved it. :)

---

