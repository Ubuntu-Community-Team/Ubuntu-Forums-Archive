---
title: "porting win programming to linux"
date: 2007-06-08
forum: Programming Talk
---

### Post by nonoykevin on 2007-06-08
i have my project in programming...i need to port my win32 source code to linux plarform in C/C++.
can somebody help me...
thanks!

---

### Post by avik on 2007-06-08
Well, can you give us more information?  What kind of project is it?  Is the code tied to the Windows API?  How big is the project?

---

### Post by nonoykevin on 2007-06-08
yes (API)...it is a big project...a program for robotic arm...

---

### Post by avik on 2007-06-09
If it's tied to the Windows API, I don't know of any way to port it to GNU/Linux without simply rewriting the code.

Maybe some other forum member can help you further?

---

### Post by Toxe on 2007-06-09
Or you could try running it under "wine". But probably you will have to rewrite the code.

---

### Post by kostkon on 2007-06-09
Another option is to compile it with [winelib]("http://www.winehq.org/site/docs/winelib-guide/winelib-introduction") but I don't know if this is going to work or if this is actually a good solution in general.

You said your software controls a robotic arm; thus, do you access specific hardware?

You said is a project, thus the only "clean" way of doing this is actually to rewrite the whole code from the start, but it depends how much is tied to Windows APIs or just most of it is clean C/C++.

---

