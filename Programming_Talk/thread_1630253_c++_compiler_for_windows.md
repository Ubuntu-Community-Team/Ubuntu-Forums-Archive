---
title: "c++ compiler for windows"
date: 2010-11-24
forum: Programming Talk
---

### Post by zealibib slaughter on 2010-11-24
Hi everyone.  I recently purchased a used book on c++ and started reading it, but I've ran into a problem.  The book was written for use with windows and some of the lessons have header files which is MS platform only :cry: and won't compile with g++.  Can someone suggest a good compiler for windows.  Must be free and I would prefer it be open source.  Thanks ya'll :).

---

### Post by zealibib slaughter on 2010-11-25
bump

---

### Post by worseisworser on 2010-11-25
GCC is ported to both Linux, Windows, Mac and several other platforms:
  [http://en.wikipedia.org/wiki/GNU_Compiler_Collection](http://en.wikipedia.org/wiki/GNU_Compiler_Collection)

A popular development package/environment on Windows which includes GCC is Code::Blocks:
  [http://www.codeblocks.org/](http://www.codeblocks.org/)

edit:
..and you can use Windows headers with GCC (g++) via these packages.

---

### Post by Zugzwang on 2010-11-25
Note that there exist some header files which GCC for windows won't have either, namely those that are found exclusively in either Borland C++ Builder or Visual Studio. You might want to reply here which header files you actually mean.

---

### Post by spjackson on 2010-11-25
> **zealibib slaughter said:**
> Hi everyone.  I recently purchased a used book on c++ and started reading it, but I've ran into a problem.  The book was written for use with windows and some of the lessons have header files which is MS platform only :cry: and won't compile with g++.  Can someone suggest a good compiler for windows.  Must be free and I would prefer it be open source.  Thanks ya'll :).
If your book uses proprietary headers in order to teach you non-standard, non-portable C++, then it ought to tell you which compiler to use.

Microsoft Visual C++ Express is a free (as in beer) download, but is not free (as in speech) nor is it open source.

---

### Post by ziekfiguur on 2010-11-25
For gcc in windows take a look at [http://www.mingw.org/](http://www.mingw.org/) and [http://www.cygwin.com/](http://www.cygwin.com/)

Code::Blocks makes use of mingw, but you can also use mingw without the IDE.
Cygwin provides a complete *nix environment within windows, including bash and lots of development packages like gcc, make and binutils

---

### Post by trent.josephsen on 2010-11-25
> **zealibib slaughter said:**
> I recently purchased a used book on c++ and started reading it, but I've ran into a problem.  The book was written for use with windows and some of the lessons have header files which is MS platform only :cry: and won't compile with g++.  Can someone suggest a good compiler for windows.

Does nobody else see the *non sequitur* here?

1. "I have an up-to-date toolchain that supplies standard headers and libraries."

2. "I have a used book that teaches non-standard headers and libraries."

3. "Therefore, I need to replace my toolchain so that it conforms to the non-standard and probably outdated language that my book teaches."

---

### Post by zealibib slaughter on 2010-11-25
The header file in question is dos.h and won't compile on a *nix system.  Thanks for the suggestions everyone.  Mingw is exactly what I needed and it worked perfect, I just wish I could do all the lessons in Ubuntu instead of having to do a few of them in windows, but I guess that it is good to learn on both platforms.:)

---

### Post by v1ad on 2010-11-25
i use Geany with MinGW compiler. 

Geany:
[http://downloads.sourceforge.net/gtk-win/gtk2-runtime-2.16.1-2009-04-21-ash.exe](http://downloads.sourceforge.net/gtk-win/gtk2-runtime-2.16.1-2009-04-21-ash.exe) 

and i used this tutorial to set up the compiling. works perfectly.
[http://grandfiles.com/tutorials/mingw/index.html](http://grandfiles.com/tutorials/mingw/index.html)

---

### Post by trent.josephsen on 2010-11-25
> **zealibib slaughter said:**
> The header file in question is dos.h and won't compile on a *nix system.  Thanks for the suggestions everyone.  Mingw is exactly what I needed and it worked perfect, I just wish I could do all the lessons in Ubuntu instead of having to do a few of them in windows, but I guess that it is good to learn on both platforms.:)

It's better to learn to code according to standards.  Get a book worth reading.  I've got a copy of Stroustrup; it seems to do fine, but maybe other people can suggest other, more suitable C++ books.

<dos.h> should have tipped you off that this book is probably teaching you non-standard code from at least fifteen years ago.

---

### Post by bcz on 2010-11-27
[www.cplusplus](www.cplusplus) has a excellent tutorial which is uptodate.  IMO excellent.

I recently bought a C++ teach yourself book which was out of date;  really a pity it is distributed worldwide

---

### Post by trent.josephsen on 2010-11-27
[.com](http://www.cplusplus.com/)

---

