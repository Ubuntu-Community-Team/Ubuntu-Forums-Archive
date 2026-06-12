---
title: "Autotools and Vala"
date: 2011-09-08
forum: Programming Talk
---

### Post by skinney on 2011-09-08
Hi! I’m trying to create my first vala and first autotools supported project. Everything actually works after following a tutorial online, but when gcc compiler kicks in to compile my program i get the error "glib.h not found".

first off, can’t just autotools use valac as a compiler instead of creating the .c files and then run gcc? (cause running valac directly works perfectly)

If I can’t configure autotools to just run valac instead of valac -c and then gcc, how would I go about solving this problem?

configure.ac:
```
#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.68])
AC_INIT([Scraps], [0.1], [Scraps])
AM_INIT_AUTOMAKE
AM_CONFIG_HEADER([config.h])
AC_PROG_CC
AM_PROG_VALAC
AC_CONFIG_FILES([Makefile
                 src/Makefile])
AC_OUTPUT
```

Makefile.am in ./src/:
```
scrapsdir=../
scraps_PROGRAMS=scraps
scraps_SOURCES=main.vala
```

Thanks!

---

### Post by anatolik on 2011-11-03
You might find this blogpost useful. It compiles for gtk2 but it should not be a problem to migrate it to gtk3.

[http://pomozok.wordpress.com/2011/01/02/vala-autotools-example/](http://pomozok.wordpress.com/2011/01/02/vala-autotools-example/)

---

