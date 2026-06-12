---
title: "GNU Automake and Autoconf"
date: 2006-06-14
forum: Programming Talk
---

### Post by bieber on 2006-06-14
I'm currently starting work on a small GTK+ application (my first foray into GUI programming on GNU systems), and the gtkmm tutorial I'm using mentioned that it was best to use autoconf and automake, rather than the command they had shown for compiling.  So, I went and looked into them, and found exactly what they do, and now I've decided that I must learn to use them before continuing, since that seems to be the standard GNU way to do things.  I've got it basically working to create a makefile for the project, but I can't seem to get it to add in the neccesary command line options to link in the gtkmm library, which, of course, presents something of a problem.  Currently, the directory structure is like this:
```

/quickbrowse
   configure.ac
   Makefile.am
   [other standard files]
   /src
	  quickbrowse.cc
	  Makefile.am

```

quickbrowse.cc is currently a **very** minimal GTK+ app, just launches a window and waits for it to close.  It has to be linked with the gtkmm (C++ bindings for GTK+) library to compile.  The configure.ac file is this:
```

AC_INIT(src/quickbrowse.cc)
AM_INIT_AUTOMAKE(quickbrowse,0.1)
AM_CONFIG_HEADER(config.h)
PKG_CHECK_MODULES(DEPS, gtkmm-2.4 >= 1.0.0)
AC_SUBST(DEPS_CFLAGS)
AC_SUBST(DEPS_LIBS)
AC_PROG_CC
AC_PROG_CXX
AC_PROG_INSTALL
AC_OUTPUT(Makefile src/Makefile)

```

The Makefile.am in the root directory looks like this:
```

SUBDIRS = src

```

and finally, Makefile.am in the src directory is this:
```

bin_PROGRAMS = quickbrowse
quickbrowse_SOURCES = quickbrowse.cc
quickbrowse_INCLUDES = $(DEPS_CFLAGS)
quickbrowse_LIBS = $(DEPS_LIBS)

```
The complete source is at [http://bieber.homeip.net/~bieber/quickbrowse.tar.gz](http://bieber.homeip.net/~bieber/quickbrowse.tar.gz)

Despite all this, it's still creating a makefile that just tries to build quickbrowse.cc with g++, without linking in gtkmm.  All this is the product of my trying to follow these two tutorials:
[http://www.openismus.com/documents/linux/a.../automake.shtml](http://www.openismus.com/documents/linux/automake/automake.shtml)
[http://www.openismus.com/documents/linux/u...libraries.shtml](http://www.openismus.com/documents/linux/using_libraries/using_libraries.shtml)
although it would appear as though I haven't done it quite right.  I plan to thoroughly learn to work autoconf, automake, and autoheader in the near future, but for the moment, I'm just trying to get a basic setup as quickly as possible so I can move on with the project.  Any help or advice would be greatly appreciated.

Thank you, 
Robert Bieber

---

### Post by nagilum on 2006-06-15
To use the libraries from $(DEPS_LIBS) for linking you need to specify them with *quickbrowse_LDADD*, not *quickbrowse_LIBS*.

---

### Post by bieber on 2006-06-15
Edit - Got it to work, I wasn't supposed to add LIBS and FLAGS with quickbrowse_ in front of them, but rather by themselves.  Now Makefile.am looks like this, and it actually builds.
```

bin_PROGRAMS = quickbrowse
quickbrowse_SOURCES = quickbrowse.cc
LIBS = $(DEPS_LIBS)
INCLUDES = $(DEPS_CFLAGS)

```

---

### Post by Fundamental Unity on 2009-04-13
I had the same problem following the tutorials.  However, I needed a different solution because my project may need multiple executables with different build requirements.  The following Makefile.am both works and meets my requirements.

```

bin_PROGRAMS = main

main_SOURCES = main.cc

main_CXXFLAGS = $(DEPS_CFLAGS)
main_LDADD = $(DEPS_LIBS)

AUTOMAKE_OPTIONS = foreign

```

(Note that I am calling my executable "main" rather than onewindow)

---

