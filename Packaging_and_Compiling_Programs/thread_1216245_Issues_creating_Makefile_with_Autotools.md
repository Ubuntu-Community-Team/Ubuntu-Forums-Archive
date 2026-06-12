---
title: "Issues creating Makefile with Autotools"
date: 2009-07-18
forum: Packaging and Compiling Programs
---

### Post by abeisgreat on 2009-07-18
Alright, let me start off by saying I have no idea what I'm doing, I mean Im quite experienced in linux, and programming, but as for creating Makefile and using Autotools, Its my first time.

Basically, I have a small SDL app which I wanted to create a makefile/configure script for, I started off following many tutorials and I have a directory structure like this:

.
-gfx
--gfx.bmp
-src
--clockwork.c
--Makefile.am

I have been trying to use autotools to generate a working makefile for awhile now, the closest I have gotten is one that outputs this

```

make  all-recursive
make[1]: Entering directory `/home/abeisgreat/Desktop/Code/C++[SDL]/clockwork'
Making all in src
make[2]: Entering directory `/home/abeisgreat/Desktop/Code/C++[SDL]/clockwork/src'
make[2]: *** No rule to make target `all'.  Stop.
make[2]: Leaving directory `/home/abeisgreat/Desktop/Code/C++[SDL]/clockwork/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/abeisgreat/Desktop/Code/C++[SDL]/clockwork'
make: *** [all] Error 2
```

Basically I run 

```
aclocal
autoconf
autoheader
automake

```

all of which run without errors, but something is wrong.

Here is the output of ls in .

```

-rw-r--r-- 1 abe abe  32612 2009-07-18 01:36 aclocal.m4
-rw-r--r-- 1 abe abe      0 2009-07-18 00:31 AUTHORS
-rwxr-xr-x 1 abe abe     62 2009-07-18 00:34 autogen.sh
drwxr-xr-x 2 abe abe   4096 2009-07-18 01:36 autom4te.cache
-rw-r--r-- 1 abe abe      0 2009-07-18 00:13 autoscan.log
-rw-r--r-- 1 abe abe      0 2009-07-18 00:31 ChangeLog
-rwxr-xr-x 1 abe abe  27953 2009-07-12 21:55 clockwork
-rw-r--r-- 1 abe abe   1731 2009-07-18 01:37 config.h
-rw-r--r-- 1 abe abe   1525 2009-07-18 01:36 config.h.in
-rw-r--r-- 1 abe abe  16209 2009-07-18 01:37 config.log
-rwxr-xr-x 1 abe abe  33502 2009-07-18 01:37 config.status
-rwxr-xr-x 1 abe abe 162221 2009-07-18 01:36 configure
-rw-r--r-- 1 abe abe    548 2009-07-18 01:36 configure.ac
lrwxrwxrwx 1 abe abe     32 2009-07-18 00:30 COPYING -> /usr/share/automake-1.10/COPYING
drwxr-xr-x 2 abe abe   4096 2009-07-02 18:14 gfx
lrwxrwxrwx 1 abe abe     32 2009-07-18 00:30 INSTALL -> /usr/share/automake-1.10/INSTALL
lrwxrwxrwx 1 abe abe     35 2009-07-18 00:24 install-sh -> /usr/share/automake-1.10/install-sh
-rw-r--r-- 1 abe abe  19332 2009-07-18 01:37 Makefile
-rw-r--r-- 1 abe abe  19419 2009-07-18 01:04 Makefile~
-rw-r--r-- 1 abe abe     14 2009-07-18 00:27 Makefile.am
-rw-r--r-- 1 abe abe  18865 2009-07-18 01:36 Makefile.in
lrwxrwxrwx 1 abe abe     32 2009-07-18 00:24 missing -> /usr/share/automake-1.10/missing
-rw-r--r-- 1 abe abe      0 2009-07-18 00:31 NEWS
-rw-r--r-- 1 abe abe   1474 2009-07-16 01:11 README
-rw-r--r-- 1 abe abe    635 2009-07-06 01:44 README~
drwxr-xr-x 2 abe abe   4096 2009-07-18 01:34 src
-rw-r--r-- 1 abe abe     23 2009-07-18 01:37 stamp-h1

```

I've been doing a mix of running tools and editing/creating files as required, and if your wondering, the reason I wanted this at all is for [http://icculus.org/~dolson/sdl/](http://icculus.org/~dolson/sdl/), so I can cross compile for *dows easily


I will be happy to give any information I can that will help you help me, thanks!

FIXED!!!
Followed this:
[http://www.airs.com/ian/configure/configure_2.html#SEC8](http://www.airs.com/ian/configure/configure_2.html#SEC8)

---

