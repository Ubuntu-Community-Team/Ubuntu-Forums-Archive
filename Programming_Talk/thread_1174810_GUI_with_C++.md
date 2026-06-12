---
title: "GUI with C++"
date: 2009-05-31
forum: Programming Talk
---

### Post by penguin-of-doom on 2009-05-31
Hey,
I have started to build my own programs, and now I want to learn how I can make a GUI. I have heard, that I can make a GUI easy with QT. But the problem is, I want the program for windows and linux. So that I can write the program on Linux and then compile it for linux and windows, so I do not have to change the source. I hope you can help me ;)

regards
penguin-of-doom

---

### Post by NielsBhor on 2009-05-31
When you compile it in windows you need to make sure that the libraries aren't using system calls that are part of linux. Alot of the linux libraries uses the system calls built into the OS. If you want to port code over to Windows from linux, you need to do a little research on OS concepts.

---

### Post by penguin-of-doom on 2009-05-31
thank you for the answer...
>  you need to do a little research on OS concepts.
because of this I asked here and I hope you can answer ^^

---

### Post by NielsBhor on 2009-05-31
The book I recommend (it's not in German) is Operating System Concepts by Abraham Silberchatz, e.t. multiple authors.

---

### Post by Habbit on 2009-05-31
Er... you do not need to know that much about OS concepts to program a GUI in C++. Just use Qt and the standard C++ class library, and stay away from operating-system provided routines.

---

### Post by SledgeHammer_999 on 2009-05-31
> **penguin-of-doom said:**
> Hey,
I have started to build my own programs, and now I want to learn how I can make a GUI. I have heard, that I can make a GUI easy with QT. But the problem is, I want the program for windows and linux. So that I can write the program on Linux and then compile it for linux and windows, so I do not have to change the source. I hope you can help me ;)

regards
penguin-of-doom

As far I know you can use QT in Windows too(never tried it)
Another solution(and C++) is [WxWidgets](www.wxwidgets.org). I've tried it and it works.

---

### Post by NielsBhor on 2009-05-31
> **Habbit said:**
> Er... you do not need to know that much about OS concepts to program a GUI in C++. Just use Qt and the standard C++ class library, and stay away from operating-system provided routines.

If he wants just GUI, it's fine. I was thinking if there are other stuff within his program in the backend of the GUI.

---

