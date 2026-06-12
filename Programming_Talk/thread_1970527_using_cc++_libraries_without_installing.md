---
title: "using c/c++ libraries without installing?"
date: 2012-05-01
forum: Programming Talk
---

### Post by korgoth28 on 2012-05-01
I need to demonstrate a large C++ program that uses the ncurses library to my prof, who requires that we compile our code in front of him. He has a linux machine, but I assume it doesn't have ncurses installed, and I wouldn't be surprised if he doesn't have a way to install new libraries.

So I downloaded a copy of curses and I'm confronted by a large number of files. Is it possible to just copy some or all of them on to a cd or flash drive with my project and just change #include <ncurses> to something like #include "curses/ncurses.h"?

---

### Post by codemaniac on 2012-05-01
> **korgoth28 said:**
> I need to demonstrate a large C++ program that uses the ncurses library to my prof, who requires that we compile our code in front of him. He has a linux machine, but I assume it doesn't have ncurses installed, and I wouldn't be surprised if he doesn't have a way to install new libraries.

So I downloaded a copy of curses and I'm confronted by a large number of files. Is it possible to just copy some or all of them on to a cd or flash drive with my project and just change #include <ncurses> to something like #include "curses/ncurses.h"?

You can download ncurses source from [http://ftp.gnu.org/pub/gnu/ncurses/](http://ftp.gnu.org/pub/gnu/ncurses/) and do a source install .
The installation instruction can be found on the file called "INSTALL" when you untar the tarball .

---

### Post by korgoth28 on 2012-05-01
Thanks much! I set up an ssh server instead, but I'll still try this for the experience.

---

