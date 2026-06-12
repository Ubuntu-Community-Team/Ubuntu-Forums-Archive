---
title: "Build your software into tarballs."
date: 2015-04-17
forum: Programming Talk
---

### Post by flaymond on 2015-04-17
Hello! I'm curious of how developers and programmers build their software into tarballs that can be installed with ./configure, make and make install commands. Since .deb packaging is 100x times hard for me, I want to try something easier, and very easy to do and standard for Linux installation. Well, I'm gonna use a hello word program implemented in C and package it into tarballs that can be easy to install from device target. How can I package this hello world program, can you show me the steps and what program, commands do I need in the process?

1. What softwares/programs do I need other than *build-essential* and *make*?

2. How can I make the executable installing itself in /usr/local/bin or /usr/bin ?

3. What commands do I need?

4. What scripts would I use?


This might be the last question I ask about packaging and distributing into tarballs and .deb in this forums, since I gonna stick with what I can do and understand.

Would you provide me some useful links about this stuff that I can learn from?

Thanks for helping me out guys!

---

### Post by TheFu on 2015-04-17
autoconf is the tool - [https://www.gnu.org/software/autoconf/](https://www.gnu.org/software/autoconf/)
However, this isn't 1995 anymore and I will only install software from either a repo or a well-known PPA. I won't touch source installs anymore. It just isn't worth my time as an admin to maintain them over the life of a server - even downloading a ".deb" file isn't something I want.  I want a PPA.

BTW, I used to write installation programs for commercial UNIX systems. Our clients demanded packages, so we switched for everything we could - only the software that was too complex for a local admin to install - where we'd send an engineer to do the install still used my scripts when I left that job in 2000.  My scripts were all written in Bourne Shell, but on Linux you could safely choose to use Bash these days.

Also - whatever you do, do not require root access for installation if someone wants to install elsewhere on their system. Requiring root is "bad form" these days for commercial software.  Of course, to install binaries into /usr/bin or /usr/local will need root, but you don't want to require root to do any "build" or "test" parts of your installation process.

Clearly, you can do whatever you like. Just saying my thoughts on this subject.

---

### Post by ofnuts on 2015-04-18
Don't expect '"tarball" packaging to be any easier than creating a .deb. It's even worse, and if everyone using Ubuntu can be told how to install a .deb (double click it in the file explorer), installing from tarball will require some skills and likely some support from you.

---

### Post by flaymond on 2015-04-20
Thanks for the advice!

---

