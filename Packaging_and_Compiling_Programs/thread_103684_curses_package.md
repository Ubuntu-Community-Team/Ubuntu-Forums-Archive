---
title: "curses package?"
date: 2005-12-14
forum: Packaging and Compiling Programs
---

### Post by PowerCore on 2005-12-14
I'm trying to make an app called Edinburgh Speech Tools. During the make there is a call to g++ 3.3 with a number of options including "-lcurses". This fails with the message "/usr/bin/ld: cannot find "-lcurses".

Running the command "locate / curses" finds several files like /lib/ncursesxxx, but not /lib/cursesxxx. Am I missing a curses package? Where do I get this?

Might this be related to the message I get during ./configure that says something like "checking to see if compiler (gcc) works... no"?

Thanks!

---

### Post by PowerCore on 2005-12-14
OK, I've solved the "Checking whether C-compiler (gcc) works... no" problem by reinstalling build-essentials and the rest of the gcc 4.0 packages.

Still have the same "-lcurses not found" error.

---

### Post by gord on 2005-12-14
have you tryed just installing the development files for ncurses? 
sudo apt-get install libncurses5-dev

---

### Post by PowerCore on 2005-12-15
Thanks! That's it! :D

I got several of the other ncurses libs, but missed that one.

---

