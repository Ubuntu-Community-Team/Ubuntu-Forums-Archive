---
title: "Change build path"
date: 2010-08-22
forum: Packaging and Compiling Programs
---

### Post by vdawg on 2010-08-22
Hey Guys,

So google isn't being much of a help here. Basically I have configure.ac as follows:
```

AC_INIT([getrichquick], [0.1], [victorparmar@gmail.com])

AC_PREREQ([2.59])
AM_INIT_AUTOMAKE([1.10 -Wall no-define foreign])

AM_MAINTAINER_MODE
AM_CONFIG_HEADER(config.h)

AC_ISC_POSIX
AC_PROG_CXX
AM_PROG_CC_STDC
AC_HEADER_STDC

PKG_CHECK_MODULES(GETRICHQUICK, 
    [gtkmm-2.4 >= 2.8 libglademm-2.4 >= 2.6])

AC_SUBST(GETRICHQUICK_CFLAGS)
AC_SUBST(GETRICHQUICK_LIBS)

AC_CONFIG_FILES([Makefile])
AC_OUTPUT

```

This is what my makefile.am looks like:
```
#gladedir = $(datadir)/glade
#glade_DATA = ui.glade
datadir = ./data

INCLUDES = \
        -DPACKAGE_LOCALE_DIR=\""$(prefix)/$(DATADIRNAME)/locale"\" \
        -DPACKAGE_SRC_DIR=\""$(srcdir)"\" \
        -DPACKAGE_DATA_DIR=\""$(datadir)"\" \
        $(GETRICHQUICK_CFLAGS) \
        -I/usr/local/include

AM_CFLAGS =\
         -Wall\
         -g

bin_PROGRAMS = getrichquick

getrichquick_SOURCES = \
        src/getrichquick.cpp src/MainWindow.h src/MainWindow.cpp

getrichquick_LDFLAGS = 

getrichquick_LDADD = $(GETRICHQUICK_LIBS)

EXTRA_DIST = $(datadir)

## Define an independent executable script for inclusion in the distribution
## archive. It will not be installed on an end user's system, however.
dist_noinst_SCRIPTS = autogen.sh

```

Everything is working fine, except for the fact that I would like my object files and executable to be placed under a build folder instead of the project root. Is this even possible? If so, what would I have to change?

Thanks a lot for your help :)

---

### Post by vdawg on 2010-08-22
Ok I figured it out, basically I run the configure script under my build directory! haha.

```

make distclean
cd build
../configure
make

```

cheers!

---

