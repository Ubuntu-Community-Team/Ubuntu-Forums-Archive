---
title: "Packaging my python imgur uploader"
date: 2010-03-28
forum: Packaging and Compiling Programs
---

### Post by nullmind on 2010-03-28
I've written a simple image uploader for imgur.com in Python. It consists of the following files:

gimgur.py
gimgur.desktop
gimgur.png
Makefile

Right now the Makefile just uses `cp` to copy files into their areas in `/usr/share/applications` and `/usr/bin` and I generate the binary package with `checkinstall`, which is a packaging sin.

I want to make a source file so I can move this to the Launchpad PPA. I know how to make a `debian/control`, but I don't see how to make a `debian/rules` that does what I need.

Thanks for the help

---

### Post by luctor on 2010-03-28
Maybe you can use dh_install in the rules file
(notice the missing slash before usr)

dh_install gimgur.py usr/bin
dh_install gimgur.desktp usr/share/applications
dh_install gimgur.png usr/??? (dunno where you want that one :-) )

---

### Post by abdusamed on 2010-12-19
i need this kind of app..how do i use this?

---

