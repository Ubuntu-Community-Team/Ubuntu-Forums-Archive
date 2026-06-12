---
title: "TkTable"
date: 2011-02-24
forum: Packaging and Compiling Programs
---

### Post by li-unix on 2011-02-24
I'm trying to import tktable in my python program, but my interpretor can't find tktable. I have the package libtktable2.9 which I thought had the correct library, but my python interpretor can't find tktable

---

### Post by sjnovick on 2012-02-29
Similar question from me, but from R with Ubuntu 11.10.

When I issue the command:

> tclRequire("Tktable")

the tcltk package cannot find it and issues the command:

[1] FALSE
Warning message:
In tclRequire("Tktable") : Tcl package 'Tktable' not found


What am I missing?

---

### Post by sjnovick on 2012-03-01
I answered my own question.

I downloaded and installed a Debian tk-table.deb package.  

Then, inside R, you have to issue the command  addTclPath("/usr/lib/tcltk").  R can then find the tk-table libraries.

---

