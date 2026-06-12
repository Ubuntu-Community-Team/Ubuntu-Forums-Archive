---
title: "Please give me some guidance on C/C++ programming with Linux"
date: 2009-05-15
forum: Programming Talk
---

### Post by Pidgin on 2009-05-15
I have read the FAQs.
I am some sort of familiar with the Windows-style of C/C++ programming, in which Microsoft Visual Studio handles much for me. Now I have almost migrated to Ubuntu, and I wanted to learn how to do C/C++ programming with Linux.
I do not have much knowledge on that topic. I think it quite differentiates from programming with Microsoft Visual Studio. I have heard some words, like configure, automake, make, etc. But I do not know what those words actually mean. I just have no idea where should I start.
I will appreciate it if you give me an overview or make some explanations or point me to some useful materials.
Thank you!

---

### Post by bloeper on 2009-05-15
Programming C/C++ isn't that different from windows.. although as far as i know there aren't any IDE's who make GUI's for you, although there are enough tutorials on how to make a window for it.

With make etc. you can compile you're program although that's possible trough numerous IDE's that are available on Ubuntu/Linux (personally i prefer Geany).

I think you should just test it out a bit.. Don't be scared to make mistakes ;)

---

### Post by MadCow108 on 2009-05-15
a list of linux IDE's
[http://linuxmafia.com/faq/Devtools/ides.html](http://linuxmafia.com/faq/Devtools/ides.html)

I use anjuta for my personal small tasks. It's quite decent but not as feature rich as studio.

You can easily create gui's for gtk with the visual editor Glade, some IDE's also have Glade plugins.
very short introduction for glade + gtkmm (the gtk c++ wrapper):
[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-libglademm.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-libglademm.html)

---

### Post by TheStatsMan on 2009-05-15
Of the IDE's I have tried codeblocks is the closest to visual studio and the Windows experience. Possibly a good place to start.

I think it is worth learning to compile from the terminal and to learn to write makefiles, which may seem like a step backwards at first but you will seem the advantages after a while. Just google and you will find a million guides on how to do these things. Once you get used to these things learn how to use a good text editor. Vim (plus as few plugins) is my favorite. There is a small learning curve but it is worth it. 

A couple of useful tools:
   gprof for profiling
   valgrind to see if your code has memory leaks
   gdb debugger (DDD) is a visual from end, which some people prefer. There are      tutorials which can be found using google for these.

---

### Post by samjh on 2009-05-15
> **Pidgin said:**
> I have heard some words, like configure, automake, make, etc. But I do not know what those words actually mean. I just have no idea where should I start.

configure, automake:

Those two are tools that form part of the GNU Autotools.  Many (most) Linux software packages are designed to be built using GNU Autotools.  When you download packages in source form (usually in .tar.gz or .tar.bz2 format) and extract the contents, you'll find the source code for the software packages, and also some scripts.  The scripts include "configure" and "Makefile".  The ./configure command checks for dependencies and prepares the Makefile.  After you run ./configure, you can then run ./make, which causes the software to be compiled in accordance with instructions in the Makefile script.

This is a very comprehensive tutorial on using Autotools:
[http://sourceware.org/autobook/autobook/autobook_toc.html](http://sourceware.org/autobook/autobook/autobook_toc.html)

Beware, Autotools is an extremely complex system.  It is designed first and foremost, as a portable means for *end-users* to build software from source.  It is *not* designed to make life easier for *developers*!  There are alternative build systems which are gaining in popularity, with the most popular being [SCons](http://www.scons.org/), and [CMake](http://www.cmake.org/) following closely behind.

**Make** is a command I mentioned before.  However, it is separate from Autotools.  Autotools helps to prepare the Makefile script, which is used by the "make" command to build software from source.  However, you can (and people usually do) use Makefiles and make independently of Autotools.  Creating a Makefile is relatively easy.  Tutorials are abundant, but I found this to be easiest to understand (PDF download): [http://oreilly.com/catalog/make3/book/ch01.pdf](http://oreilly.com/catalog/make3/book/ch01.pdf)

You will obviously need to know how to use the gcc and g++ compilers from source.  That is very easy.  The parameters are exactly the same for both compilers.  For example, to compile helloworld.cpp into an executable named, helloworld, you'd call g++ as follows (assuming the current directory is the same as the location of the helloworld.cpp file):
```
g++ -o helloworld helloworld.cpp
```
**g++**: the compiler.
**-o helloworld**: the "output" option.  You use this to specify the name of the resulting file (helloworld, in this case).
**helloworld.cpp**: the source file.

Find out more here: [http://www.network-theory.co.uk/docs/gccintro/](http://www.network-theory.co.uk/docs/gccintro/) (the link also includes a chapter on Makefiles)

---

### Post by Pidgin on 2009-05-15
Thank you! You are all so kind to help me!
After reading TheStatsMan and samjh's replies, now I understand that what I want to learn is how to write Makefiles. I already know how to invoke gcc or g++ to compile sources. However, a Makefile will automate the process and help organize a project, right?
I will read the materials you give and have some experiments.
Thank you again! But still modestly looking forward to more guidance.

---

### Post by samjh on 2009-05-15
Makefiles can definitely make compilation easier.  Saves a lot of typing when you have many source files, compiler flags, and libraries to link!

---

### Post by C-- on 2009-05-15
Here's a makefile tutorial.

[http://www.opussoftware.com/tutorial/TutMakefile.htm](http://www.opussoftware.com/tutorial/TutMakefile.htm)

---

### Post by Pidgin on 2009-05-15
> **C-- said:**
> Here's a makefile tutorial.
[http://www.opussoftware.com/tutorial/TutMakefile.htm](http://www.opussoftware.com/tutorial/TutMakefile.htm)
Thank you! I'll check it.

---

