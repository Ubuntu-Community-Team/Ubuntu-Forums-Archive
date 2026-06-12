---
title: "port c++/g++ program to windows"
date: 2008-12-19
forum: Programming Talk
---

### Post by monkeyking on 2008-12-19
I have a program, that i've developed on a ubuntu machine.
With standard Makefile.

I've been compiling with -ansi -Wall -pedantic
So the code in it self, shouldn't be a big problem.

I've installed ms visual c++ with the ms compiler, and I've also downloaded the bloodshed devc++ with the mingw compiler.

But these winprogs, revolves around the concept of a project,
not really a Makefile.

Does anyhow have an idea on how to compile the program, 
without doing a platform fork.

thanks in advance

---

### Post by stevescripts on 2008-12-19
As an alternative to VC++/bloodshed - look at mingw [http://www.mingw.org/](http://www.mingw.org/) ...

Many folks that I interact with on a daily basis, are quite comfortable with mingw. (I use it often myself)

This is not to say that you cannot configure both of the above to build your project, you certainly can (provided you dont have OS specific code in your source files...), learning to do so just takes a bit of time and effort.

Hope this is helpful.

Steve

---

### Post by curvedinfinity on 2008-12-19
I'll second MinGW...

VC++ will be a major pain because you also have to recompile all of your dependencies for windows, and VC++ isn't compatible with the gnu toolchain. MinGW with MSYS is kind of "unix on top of windows" so it is compatible with shell script, make, and so on.

I used to use VC++ for my windows ports, but it was simply a pain to setup, since you have to use the complex GUI for everything that is normally just a short little bit of text in a command line or makefile.

---

### Post by monkeyking on 2008-12-20
As I wrote in my original post,
I wanted to avoid having to fork the code.

This package [http://www.murdoch-sutherland.com/Rtools/](http://www.murdoch-sutherland.com/Rtools/)

Contains basic mingw and unix commands, plus other stuff.
Which makes it possible to use makefiles.

I can recommend it.

---

