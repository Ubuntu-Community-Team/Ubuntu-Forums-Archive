---
title: "C++ Compiling and Editing Questions"
date: 2007-10-24
forum: Programming Talk
---

### Post by Unicycle on 2007-10-24
I'm fairly new to programming, although I did take a class on C++ over the summer.  I've solidly learned the basics, and I'd like to start programming in Linux.  So, I need to know how I do this....

First of all, I see that I can edit and save my .cpp files in gedit, but then how do I compile them?  Also, is there anything different about coding C++ in Linux that is different than Windows that I should look out for?

Thanks!  \\:D/

---

### Post by Can+~ on 2007-10-24
> gcc -o [output] [input.cpp]

Example:
> gcc -o calc calculator.cpp

But I think you need those libraries for development, I don't remember which ones right now... *edit*: build-essential it's on synaptic.

---

### Post by Unicycle on 2007-10-24
OK, now how about an IDE?

I downloaded Anjuta, but I can't even find how to compile!! :confused:

---

### Post by Can+~ on 2007-10-24
I don't use anjuta, but I guess you can find something useful here:
[http://anjuta.sourceforge.net/documentations/subpage/documents/C/anjuta-manual/anjuta-manual.html](http://anjuta.sourceforge.net/documentations/subpage/documents/C/anjuta-manual/anjuta-manual.html)

---

### Post by dwhitney67 on 2007-10-24
> **Unicycle said:**
> OK, now how about an IDE?

I downloaded Anjuta, but I can't even find how to compile!! :confused:

If you are indeed serious about programming and building applications under Linux, then learn the basics... use the command line, and learn how to develop Makefiles.  If you are looking for a simple, canned solution, then you are learning nothing, and whatever procedure you use may not be portable to other systems/environments.

Here's a helpful web-site to [GCC]("http://gcc.gnu.org/onlinedocs/gcc-4.1.2/gcc/").

Here's one for [Makefiles]("http://www.gnu.org/software/make/manual/make.html").

Btw, you don't not have to memorize everything on those webpages.  Just reference them when you have a question.

---

### Post by dumbsnake on 2007-10-24
you should go to the command prompt and type "man g++" to get some more information, but essentially to compile your files into an executable, something simple like "g++ -o myexec *.cpp" will compile all the .cpp files in the directory as C++ link them with the C++ standard library and then output it to an executable called "myexec" because of the "-o myexec" option. If you need to link with libraries, you will need to add those also as arguements to g++ usually by specifying -lsomelib where libsomelib.so.* is in your library include path.  See the g++ man pages though for this info and more.

I hope this helps.

---

