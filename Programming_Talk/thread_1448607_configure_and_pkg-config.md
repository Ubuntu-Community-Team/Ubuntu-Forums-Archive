---
title: "configure and pkg-config"
date: 2010-04-06
forum: Programming Talk
---

### Post by y50a7XpWRH66IV on 2010-04-06
Hi everyone,

I am currently building a GTK app in ubuntu 9.10.

I was using kdevelop as my IDE, however, due to some bugs, I have decided to move to eclipse.

I have configured eclipse with CDT and the linux tools (auto tools) plugin. I have also created an autotools helloworld project and moved all of my source files into the project.

I am now having trouble compiling my program because the builder is unable to find certain include files. Namely, the GTK.h and the libtar.h files.

In Kdevelop, the following C Compiler Flags (CFLAGS) was entered into the options: -O0 -g3 $(pkg-config --cflags --libs gtk+-2.0 gmodule-2.0) -ltar

I have tried a lot of different changes to my configure.ac file, but they never worked.

How do I convert this so that it can be inserted into my configure.ac file?

Thank you :)

---

### Post by y50a7XpWRH66IV on 2010-04-06
Problem solved for those interested:

configuration.ac:
```

dnl Process this file with autoconf to produce a configure script.

AC_PREREQ(2.59)
AC_INIT(app, 1.0)

PKG_CHECK_MODULES(GTK, gtk+-2.0 gmodule-2.0)

PACKAGE_CFLAGS="-g -Wall $GTK_CFLAGS"
PACKAGE_LIBS="-g $GTK_LIBS -ltar"
PACKAGE_LDFLAGS="$GTK_LDFLAGS"

AC_SUBST(PACKAGE_CFLAGS)
AC_SUBST(PACKAGE_LIBS)
AC_SUBST(PACKAGE_LDFLAGS)

AC_CANONICAL_SYSTEM
AM_INIT_AUTOMAKE()

AC_PROG_CC

AC_CONFIG_FILES(Makefile src/Makefile)
AC_OUTPUT
```

Makefile.am
```
bin_PROGRAMS=app
app_SOURCES=app.c one.c two.c

noinst_HEADERS = one.h two.h three.h

app_LDADD = @PACKAGE_LIBS@
app_LDFLAGS = @PACKAGE_LDFLAGS@
INCLUDES = @PACKAGE_CFLAGS@
```

---

