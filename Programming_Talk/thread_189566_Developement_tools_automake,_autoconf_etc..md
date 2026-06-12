---
title: "Developement tools: automake, autoconf etc."
date: 2006-06-05
forum: Programming Talk
---

### Post by Laterix on 2006-06-05
Hi,

I'm quite new to developeing software in Linux and I have found difficult to understand all this tools and scripts there are. I'm using C/C++ and coding is the easy part, but compiling, installing etc. is harder.

How do I develop C++ program in linux the right way? Using these automake, autoconf, etc. tools? Is there some Linux software developement guides available on net, because I couldn't find one with Google?

What other developement tools there are? What are they used for? How I can use them?

---

### Post by Arndt on 2006-06-05
[QUOTE=Laterix]Hi,

I'm quite new to developeing software in Linux and I have found difficult to understand all this tools and scripts there are. I'm using C/C++ and coding is the easy part, but compiling, installing etc. is harder.

How do I develop C++ program in linux the right way? Using these automake, autoconf, etc. tools? Is there some Linux software developement guides available on net, because I couldn't find one with Google?

What other developement tools there are? What are they used for? How I can use them?[/QUOTE]

The minimalistic way (unless you don't use any tool at all) would be to just use 'make'. It is well documented by "info make".

The installation part if usually also performed by rules in a Makefile, but maybe there are tools out there helping with that too.

As I understand autoconf, it is used to generate a configure script, which the person compiling the code on some other platform can run to have all platform-dependent parameters of the code be set correctly. It is probably not the first thing you need to write when you are developing, unless you know from the start that you will develop on several platforms.

One tool which does not add structure to the source code, but helps navigating in it, is 'etags'. It produces a file containing the location of all C definitions in the source code (functions and macros), which you can then easily look up with the command M-. in Emacs. Maybe it works for other languages than C, but I haven't used it for anything else.

---

### Post by -Rick- on 2006-06-05
As build system I prefer [SCons]("http://www.scons.org/"). It's much easier and less bloated than autotools IMO. It depends on python though and only the recent dev versions have './configure support'.
The guide is pretty clear in making a good config file.

Some other tools which I use: subversion(code version managment), ctags(for finding functions and such, kdevelop has a nice frontend), gdb(debugging, again kdevelop has a nice frontend for this) and ... kdevelop.

[http://www.koders.com]("http://www.koders.com") is a nice site to easily search for (example) code in other Open Source projects.

And for *cough* installing check my sig ;)

---

### Post by hod139 on 2006-06-05
For automake documentation, [http://www.gnu.org/software/automake/manual/](http://www.gnu.org/software/automake/manual/)

---

### Post by Laterix on 2006-06-05
[QUOTE=hod139]For automake documentation, [http://www.gnu.org/software/automake/manual/](http://www.gnu.org/software/automake/manual/)[/QUOTE]
Thanks for the link. And thank to others too. I'll take look at different options and see which is right to me. But thread is still open for more comments and proposes. :)

---

### Post by toojays on 2006-06-06
A decent introduction to the autotools is a book called [GNU Autoconf, Automake and Libtool](http://sourceware.org/autobook/). The autotools are a bit convoluted, but they are the most widely used tools, and very capable. I use them on a wxWidgets project which I build for GNU/Linux and Windows.

Before you learn the autotools, I suggest you aquaint yourself with GNU Make. You should be able to write a simple makefile which can build the project with "make", and install it with "make install". It is much easier to debug your autotools stuff if you can read makefiles.

I develop my C++ projects in GNU Emacs and GNU Make. Both these programs are very flexible, so I can use them for all kinds of other projects, from C to DocBook to LaTeX. The steep learning curve really pays off when you can easily adapt what you've learnt to other situations.

---

### Post by mellibra on 2006-06-20
Confused with Autotools, automake, autoconf, r they the same with VC studio?

---

### Post by toojays on 2006-06-20
mellibra: The autotools are completely different to VC Studio. The autotools are a set of programs for making programs portable. A properly autotooled program will compile on GNU/Linux, Solaris, Windows (with mingw), etc. MSVC only really exists for one platform, so it doesn't provide any portability tools.

---

