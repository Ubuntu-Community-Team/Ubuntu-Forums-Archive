---
title: "Simple ANSI C IDE"
date: 2018-08-01
forum: Programming Talk
---

### Post by Lewis Balentine on 2018-08-01
I guess old fashion "C" has lost its appeal but I would prefer it for small task targeted applications. Unfortunately I can not seem to locate a simple IDE for C. Everything I have looked at is bloated with C++, Python, Java,...., etc. All I really want is a GUI text editor, compiler and debugger. I would actually be happy with the OS Text editor* (in my case Mate's Pumma Text Editor)*, gcc and a debugger. Problem is I have not found a half decent debugger.  The closest thing I have found is ChIDE but it is hopelessly outdated. **Suggestions?**

---

### Post by howefield on 2018-08-01
Thread moved to the "*Programming Talk*" forum, probably a better fit.

---

### Post by Lewis Balentine on 2018-08-01
Thank Thee

---

### Post by spjackson on 2018-08-01
My "go to" debugger on Linux is ddd. Gvim, make and ddd could be all you need.

 For a full IDE, you could try Code::Blocks. Geany provides debug support via a plugin. Eclipse can be used for C with the right packages, but probably doesn't qualify as "a simple IDE".

---

### Post by Lewis Balentine on 2018-08-03
I tried ddd but it came up with teensy fonts on my system. I tried changing the fonts to no avail. Looking for alternatives I ran across **gdbgui_0.13.0.0** that runs in a browser (*Chrome in my case*).
At least then I can increase or decrease the size of the UI.Not overly pleased with the manner either one shows character arrays. Scrolling down through a long array is a pain in the most southern region but I can live with it.

I looked into geany. It does include a debugger plugin  back in version 1.27 however Ubuntu is currently distributing version 1.32 and does not include it. I downloaded all the sources for the current development version 1.34 and spent most of the night figuring out how to get it to build. The build instructions on their website are "sparse" ... and that is being overly kind. Requires about half a GByte of support dev files as well. After going through all that I found that the debugger module would not build ... I am assuming that the Ubuntu folks had similar problems. Nice package ... I may try to configure it so that it uses **gdbgui** as a debugger.

If anyone should to want to build geany, I have attached a text file with my notes. I ran through them step by step twice on a clean system to insure that they work (*sans the debugger of course*).
Cheers

[ATTACH]280627[/ATTACH]

---

### Post by spjackson on 2018-08-04
Did you try Code::Blocks? It works reasonably well out of the box from what I can see. (See attached.)

I've always found ddd adequate for basic needs. For a more sophisticated IDE I've used Eclipse and would recommend that, but that is more heavyweight than it sounds like you are looking for.

Building Geany from source seems a bit OTT if all you want to do is get a simple IDE for C.

---

