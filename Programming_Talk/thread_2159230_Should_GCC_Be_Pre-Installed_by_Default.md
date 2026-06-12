---
title: "Should GCC Be Pre-Installed by Default?"
date: 2013-07-02
forum: Programming Talk
---

### Post by King Dude on 2013-07-02
I've been trying to install GCC for the past two days, and it has been a real pain in my neck. So I thought to myself, "Why isn't GCC included by default?"

I'm aware GCC lacks an IDE, which makes it difficult for beginning programmers, so I also was wondering if an IDE could be included by default as well.

---

### Post by TheFu on 2013-07-02
No. It shouldn't be installed.  Most Ubuntu users will never need to compile anything.  Heck, I'd like to have Evolution removed from the default install and strip down the defaults in the OS so it fits under 512MB of disk.

The easiest way to get a C/C++ development environment is to install the metapackage ... **build-essential**
As to an IDE .... well, beginners shouldn't be using ANY IDE, IMHO.  Learn to do things manually, so when the IDE settings get screwed up, then you can fix them.  Of course, I say this when I learned using the TurboC and TurboC++ IDEs.  The closest that I've found to those are Geany, but you'll need to setup all the external programs ... **gdb**, **gcc**, **g++**, and **make** manually.  I like the **ddd** tool for a GUI debugger too.  Anything except the hugely (understatement) bloated Eclipse IDE.

Understanding a UNIX development environment will pay off the next 50 yrs of your life.  Most Windows-only devs don't really understand everything and are tripped up by stupid issues in their environments.  BTW, I worked as a cross-platform dev for a decade ... about 12 different platforms.  On Windows, we used CLI tools for everything we could because the huge IDEs were too slow.

---

### Post by Dirich on 2013-07-02
King Dude: I recently (one week ago) installed 13.04 and gcc was already installed. I had to manually install g++ though (and by "manually" I mean I used the Software Center, I did not even bother using apt-get). I did not do anything special, so it should already be installed on yours OS too...
Also, I am under the impression that most options are common for different compilers (-o <executable name> i.e.) so you can use that knowledge if you have it on other compilers (i.e. gfortran).

TheFu: what you say is true, but sometime I want to start fast because I am always short on time. An IDE is not so bad to begin with, you can just start learning stuff a bit more easyly and then you "grow out of it". Learning by doing is often times faster than learning and then start doing stuff, like you have to without an IDE, where you are drown by so many options that at the very beginning you do not even know how to do the default gcc -o exectuable file.cpp.

---

### Post by nvteighen on 2013-07-02
I'm not a Ubuntu user for a long time, having sticked to Debian since years... but I think the point is valid for both distros.

IIRC, the GCC toolchain is installed by default for some reason, but installing build-essential 1) ensures that you really have gcc + g++, 2) gets the glibc development headers, 3) gets you GNU make.

---

