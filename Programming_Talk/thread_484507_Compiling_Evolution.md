---
title: "Compiling Evolution"
date: 2007-06-25
forum: Programming Talk
---

### Post by Mark Erbaugh on 2007-06-25
I am trying to compile Evolution 2.10.2 under Ubuntu 7.04.

I ran the ./configure program with no options. It complained about various libraries missing. In each case, I went into Synaptic and downloaded the missing library. I got ./configure to run without error. It did issue a warning about iconv.

I then issue the make command.  The make command fails on a compile statement saying it can't find nspr.h.  I do a locate on nspr.h and find it at /usr/include/firefox/include.nspr.  When I look at the output from ./configure, it also found nspr.

What am I doing wrong?

---

### Post by geraldm on 2007-06-27
Omitting a flag in the Makefile?
 -I/usr/include/firefox/include.nspr. (whatever directory it is in)

---

### Post by PoJD on 2007-06-28
Mark, I got in exactly the same troubles as you. First I tried manually editing Makefiles as geraldm suggests, but this got worse and worse. I think the main problem is a bug in the instalation since it does not correctly inform the user that a library is missing. Installing libnss-dev via Synaptic and running the configuration again solves the problem for me. No neccessary paths for either nss or nspr given to configure. Configure succeed as well as the make itself and further instalation..

Hope this helps you and some others as well.. ;)

---

