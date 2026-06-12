---
title: "C++ framework choice"
date: 2007-11-27
forum: Programming Talk
---

### Post by dewm_solo on 2007-11-27
Hi all, I am aware that this has most likely been discussed before, but my searches on the forum hasn't lead to an answer to my question.

I am a C++ developer that comes from a Windows development world as most of you do. I started with Win32 api and since 2004 have been working with .Net 1.1 and 2.0. To skip over the personal history, I'll jump ahead. I have been growing tired and doubtful of .Net ....the more I use it the more design flaws and problems I get with deployment and sharing libraries, etc etc...and quite frankly I would like to get back to native C++. I do still need to develop for windows as the company I work for develops utilities for a piece of software that exists only on windows. 

So...here's the question. Amongst all of the different frameworks and apis.....I'm talking Qt, wxWidgets, QTK+, etc etc....Is there one that I could learn on linux, in my spare time, that allows for cross platform compilation, that would allow me to develop relatively fast and be good enough for corporate software.

I have been looking quite a bit at wxWidgets....I have the source...and its all compiled. I browsed the classes descriptions and read some tutorials online. I am just concerned with the future of it, how it will move on to newer Os's : ie Vista. I am also worried about how productive will I get to be with it. With all the problems I've been encountering at deployment time with .Net....if I could get to be 80~85% as productive with another framework and cut a little on my deployment problems....I would end up being better off with something else than .Net.

---

### Post by LaRoza on 2007-11-27
I would go with wxWidgets. Not only does it work on all platforms, it is available for Python and other languages.

---

### Post by DavidBell on 2007-11-28
If you want to try it in windows/MSVS, there is a thing called wxPack (google it) that basically sets you up with wx on a windows machine - it installs precompiled libraries, sources, docs, GUI editors plus wizards and helpfiles for MSVS all in one step. It's about 200MB, but I found it an easy way to get into wxwidgets.

I have found programs done with wx in MSVS pretty easy to make cross platform. Basically you just get it working in MSVS and compiling without errors/warnings; then switch to linux and recompile with gcc; fix any new errors/warnings; when that's done it should be good to go.

DB

---

### Post by dewm_solo on 2007-11-28
Ok...so wxWidgets is recommendable, even for commercial applications?

Here is stuff that I didn't mention yet that the apps I build need:
-Connect to an ODBC database
-Connect to an Access database through a security database
-Connect to MS SQL Databases
-Print/Display Crystal Reports

The rest is mostly data handling, csv files reading, gui, file manipulation....the usual...LoL

Does wxWidgets provide classes to do all those things? I know there is an ODBC class, so that should be covered....the one that worries me is the crystal reports.


BTW, thanks for your answers.

---

### Post by slavik on 2007-11-29
> **LaRoza said:**
> I would go with wxWidgets. Not only does it work on all platforms, it is available for Python and other languages.

Same but replace wxWidgets with GTK. :)

---

