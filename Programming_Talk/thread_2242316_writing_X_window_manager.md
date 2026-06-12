---
title: "writing X window manager"
date: 2014-09-01
forum: Programming Talk
---

### Post by rsmith9265 on 2014-09-01
Hi
I don't know this is the right place to ask but I want to develop my own X window manager and i really don't know where to start.
In fact,I read the source of this project **[http://incise.org/tinywm.html](http://incise.org/tinywm.html)** But I'm really confused and even when i start it,it just only show me black screen not window manager!!:sad: so i just want to start with simple X project to show basic text(for example "hello world!") in window-styled box and by the time turn it into simple window manager,so i need to answer this questions:
[LIST=1]
[*]**What is the best programming language for this project?** 
[*]**Can i write my window manager and then turn it into Desktop Environment?** 
[*]**Does my X window project support UTF-8 and it does not turn** **my strings into question mark or something like that?(I mean using another language other than English.)** 
[/LIST]
Thanks in advance.
Roger Smith

---

### Post by TheFu on 2014-09-01
Use C. There really isn't any other choice for X/Windows programming at that level.

Do you know what a Window Manager does?  Perhaps reading the wikipedia article will help.  A black screen is what they look like until you tell them to hold a GUI program inside a window - then they provide the borders, and placement of the apps window on the desktop and any popup menus that the borders support.  THAT's it.  They may support a menu on a clear part of the desktop - or not.

There are 50 existing WM already written.  Grab the source code and start reading. twm, mwm, fvwm are old and should be pure X11.
You probably want to learn how to program in C, then X/Windows before attempting to tackle a Window Manager project.

If you want to support UTF8/16/32 - fine. You'll need to write the code to handle it.  After all, if it were easy, it would have been done by everyone else already.

Good luck. I think you'll discover this is more work than it appears.

---

### Post by rsmith9265 on 2014-09-01
Thank you very much for you answer.however as you say I will use C and I find this page [http://rosettacode.org/wiki/Window_creation/X11](http://rosettacode.org/wiki/Window_creation/X11),well I know how to compile *.c files but the problem is I don't know how to debug my X window project from Xserver.anyway thank you for your quick response.

---

### Post by TheFu on 2014-09-01
I have a complete set of X11 programming books from the early 1990s that I'm willing to part with if you pick them up. They came with 6 weeks of intensive training on programming X/Windows that my employer covered. I was already an experienced C/C++ programmer with 3 yrs of work experience BEFORE being sent to those classes. I had many, many, many questions that really needed the 1-on-1 help from the instructor and other students. This forum really isn't a viable alternative - at least not from my side.

[https://en.wikibooks.org/wiki/Category:X_Window_Programming](https://en.wikibooks.org/wiki/Category:X_Window_Programming) might be useful.

I wish you well.

---

