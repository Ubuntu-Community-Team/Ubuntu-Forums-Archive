---
title: "Linking problem with g++ and autotools"
date: 2011-10-12
forum: Programming Talk
---

### Post by WebDrake on 2011-10-12
I'm having an unexpected problem with a C++ project which is falling over at the linking stage:
```

/bin/bash ../libtool --tag=CXX   --mode=link g++ -I.. -g -O2 -lgsl -lgslcblas -lm    -o minga minga.o libminga.la 
libtool: link: g++ -I.. -g -O2 -o .libs/minga minga.o  -lgsl -lgslcblas -lm ./.libs/libminga.so
./.libs/libminga.so: undefined reference to `gsl_rng_uniform_int'
./.libs/libminga.so: undefined reference to `gsl_rng_uniform'
collect2: ld returned 1 exit status
```

A quick check reveals that the problem is in the order of arguments being presented to g++.  If I call g++ as above, the undefined reference errors occur; if instead I type,
```
g++ -I.. -g -O2 -o .libs/minga minga.o  ./.libs/libminga.so -lgsl -lgslcblas -lm
```

... then the executable links without complaint.

So, I have two questions:

[LIST]
[*]Why is g++ (v4.6.1 on Oneiric) being so fussy about the order of library arguments?  On earlier systems the program built without complaint, and I have changed nothing in the autotools setup files.
[*]How do I get the autotools to present the correct order of arguments to g++?
[/LIST]
Thanks in advance for any advice!

---

### Post by WebDrake on 2011-10-12
For reference, here are the configure.ac and Makefile.am files for this part of the project:

**configure.ac:**
```

AC_INIT([Minga],[development version])
AC_CONFIG_SRCDIR([minga/minga.cpp])
AC_CONFIG_AUX_DIR([build-aux])
AC_CONFIG_MACRO_DIR([m4])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])

AC_CONFIG_HEADERS([config.h])

AC_DISABLE_STATIC
AM_PROG_LIBTOOL
AC_LIBTOOL_CXX


MINGA_LT_VERSION="0:0:0"
AC_SUBST(MINGA_LT_VERSION)

AC_LANG(C)
AC_LANG(C++)
AC_PROG_CC
AC_PROG_CXX
AC_PROG_CPP
AC_PROG_LN_S

dnl Swig specific options

AM_PATH_PYTHON([2.5])
AC_PROG_SWIG([1.3.21])
SWIG_ENABLE_CXX
SWIG_PYTHON


dnl Disable unnecessary libtool tests for FORTRAN and Java
define([AC_LIBTOOL_LANG_F77_CONFIG],[:])dnl
define([AC_LIBTOOL_LANG_GCJ_CONFIG],[:])dnl
AC_PROG_LIBTOOL

dnl Check for Python

AX_PYTHON

dnl Check for Boost libraries

AX_BOOST_BASE([1.36.0])
AX_BOOST_PYTHON

PKG_CHECK_MODULES(DEPS,[gsl >= 1.8])
AC_SUBST(DEPS_CFLAGS)
AC_SUBST(DEPS_CXXFLAGS)
AC_SUBST(DEPS_LIBS)

MINGA_CFLAGS="-I$includedir $DEPS_CFLAGS"
MINGA_CXXFLAGS="-I$includedir $DEPS_CXXFLAGS"
MINGA_LDFLAGS="$DEPS_LIBS"
MINGA_LIBS="-L$libdir -lminga $MINGA_LDFLAGS"

AC_SUBST([MINGA_CFLAGS])
AC_SUBST([MINGA_CXXFLAGS])
AC_SUBST([MINGA_LDFLAGS])
AC_SUBST([MINGA_LIBS])

dnl CFLAGS="$CFLAGS -std=c99 -pedantic -Wall -Werror"
dnl CXXFLAGS="$CXXFLAGS -ansi -pedantic -Wall"

AC_CONFIG_FILES([minga/minga.pc minga/minority/agent/Makefile minga/minority/game/Makefile minga/minority/interactive/Makefile minga/minority/reward/Makefile minga/minority/Makefile minga/Makefile pyminga/Makefile Makefile pyminga/api_spec/Makefile])
AC_OUTPUT

```


**Makefile.am:**
```

SUBDIRS = minority
SUBLIBS = minority/libminga-minority.la

ACLOCAL_AMFLAGS = -I ../m4

AM_CFLAGS = -I$(top_builddir)
AM_CXXFLAGS = -I$(top_builddir)
AM_LDFLAGS = $(MINGA_LDFLAGS)

pkgconfigdir = $(libdir)/pkgconfig
pkgconfig_DATA = minga.pc

lib_LTLIBRARIES = libminga.la
libminga_la_SOURCES = info.cpp
libminga_la_LIBADD = $(SUBLIBS)
libminga_la_LDFLAGS = -version-info $(MINGA_LT_VERSION)
libminga_la_includedir = $(includedir)/minga
libminga_la_include_HEADERS = minga.hpp agent.hpp game.hpp info.hpp interactive.hpp outsider.hpp reward.hpp var.hpp minority.hpp

bin_PROGRAMS = minga minga-mgbasic minga-imgbasic
minga_SOURCES = minga.cpp
minga_LDADD = libminga.la
minga_mgbasic_SOURCES = demo/mg_basic.cpp
minga_mgbasic_LDADD = libminga.la
minga_imgbasic_SOURCES = demo/img_basic.cpp
minga_imgbasic_LDADD = libminga.la

```

---

### Post by WebDrake on 2011-10-12
One solution is found in a response to an earlier query of mine -- [http://ubuntuforums.org/showthread.php?t=1686429](http://ubuntuforums.org/showthread.php?t=1686429)

I'm curious if there is a recommended way to fix this via autotools ... ?  I did so by adding the line,
```
CXXFLAGS="$CXXFLAGS -Wl,--no-as-needed"
```
to my configure.ac file, but I don't know if this is the recommended option.

---

### Post by JupiterV2 on 2011-10-14
I am not an expert but from my own experience I see the following issues:
```
PKG_CHECK_MODULES(DEPS,[gsl >= 1.8])
AC_SUBST(DEPS_CFLAGS)
AC_SUBST(DEPS_CXXFLAGS)
AC_SUBST(DEPS_LIBS)

MINGA_CFLAGS="-I$includedir $DEPS_CFLAGS"
MINGA_CXXFLAGS="-I$includedir $DEPS_CXXFLAGS"
MINGA_LDFLAGS="$DEPS_LIBS"
MINGA_LIBS="-L$libdir -lminga $MINGA_LDFLAGS"

AC_SUBST([MINGA_CFLAGS])
AC_SUBST([MINGA_CXXFLAGS])
AC_SUBST([MINGA_LDFLAGS])
AC_SUBST([MINGA_LIBS])
```

Libtool tends to have issues when things aren't assigned to the variables it expects. LDFLAGS are just for linker flags and LDADD is for additional libraries needing to be linked. Link ordering does sometimes matter for some reason too, so DEPS_LIBS might need to come before -lminga.  These should be more like:

MINGA_LDFLAGS="-L$libdir"
MINGA_LIBS="$DEPS_LIBS -lminga"

then in your Makefile.am
```
bin_PROGRAMS = minga minga-mgbasic minga-imgbasic
minga_SOURCES = minga.cpp
minga_LDADD = libminga.la
minga_mgbasic_SOURCES = demo/mg_basic.cpp
minga_mgbasic_LDADD = libminga.la
minga_imgbasic_SOURCES = demo/img_basic.cpp
minga_imgbasic_LDADD = libminga.la
```

change minga_LDADD to:
```
minga_LDADD=$MINGA_LIBS libminga.la
minga_LDFLAGS=$MINGA_LDFLAGS
```

This should correctly order your libraries. Maybe not. It's also possible you should link the libraries into your libminga.la library because libtool tries to build a shared object (libminga.so) which may also be a reason why you're getting unresolved symbols. I'm not sure. Just a few things to play around with.

Incidentally, there a reason you're linking -lminga and libminga.la?

---

### Post by WebDrake on 2011-10-14
Thanks for the feedback.  I think I may have confused things by setting ```
AM_LDFLAGS = $(MINGA_LDFLAGS)
``` in *Makefile.am*, because really the MINGA_* variables are not intended to be used in the build process -- rather, they're used to generate the pkg-config info for the built library:

**minga.pc.in:**
```
prefix=@prefix@
exec_prefix=@exec_prefix@
libdir=@libdir@
includedir=@includedir@

Name: minga
Description: Minority and market entry game simulation library
Version: @VERSION@
Libs: @MINGA_LIBS@ @LIBS@
Cflags: @MINGA_CFLAGS@
Cxxflags: @MINGA_CXXFLAGS@
```

The MINGA_LDFLAGS are used to set the value of AM_LDFLAGS in *Makefile.am* simply because they are by definition the linker flags required to build anything against libminga.la.

By contrast MINGA_LIBS is not called on anywhere in the build process.  Nothing builds calling -lminga -- that's the linker flag you'd use to build against this library once installed on the system.

Following your advice I tried taking out the AM_LDFLAGS statement from *Makefile.am* and instead putting in separate LDFLAGS statements with respect to the individual executables:```
bin_PROGRAMS = minga minga-mgbasic minga-imgbasic
minga_SOURCES = minga.cpp
minga_LDADD = libminga.la
minga_LDFLAGS = $(MINGA_LDFLAGS)
minga_mgbasic_SOURCES = demo/mg_basic.cpp
minga_mgbasic_LDADD = libminga.la
minga_mgbasic_LDFLAGS = $(MINGA_LDFLAGS)
minga_imgbasic_SOURCES = demo/img_basic.cpp
minga_imgbasic_LDADD = libminga.la
minga_imgbasic_LDFLAGS = $(MINGA_LDFLAGS)
```
... but this generates the same faulty g++ call when building the *minga* executable, and hence the same linking error at the same point in the build process.

---

### Post by WebDrake on 2011-10-14
Well, here's something interesting ...

... so, as you can see from the error message, the linking falls over on the command,
```
g++ -I.. -g -O2 -o .libs/minga minga.o  -lgsl -lgslcblas -lm ./.libs/libminga.so
```
... with undefined references to GSL random number functions.

The random number functions are called at various places inside the code that goes into libminga.so.  However, _none of that code is called from within minga.o_.  So presumably the default --as-necessary option of g++ doesn't see the need for the GSL linking, even though libminga.la _does_ need it.

The other binary executables described in *Makefile.am* _do_ call that code, and don't fall over at the linking stage -- so presumably g++ recognizes their need to link to GSL through the fact that they call on the GSL-related functions.

So, it turns out there are two solutions to the problem.

One is to add a line to *Makefile.am*,
```
minga_CXXFLAGS = -Wl,--no-as-needed
```
... which ensures that the minga executable does indeed link against GSL.

The other is to make sure that the minga executable does not link against the whole libminga.la library but only against the (tiny) subset of its code that it actually needs:
```
minga_SOURCES = minga.cpp
minga_LDADD = info.o
```

Very interesting and informative learning experience about how g++ and autotools fit together ...

---

### Post by MadCow108 on 2011-10-14
assnumg gsl is correctly linked,no need to disable as-needed with autotools, just use it correctly.
libraries to link with go into LDADD or LIBS **not** LDFLAGS
with libtool the variable for the libtool files is LIBADD

if gsl is incorrectly linked you do have to disable as-needed or do some double adding of libraries to the command line :/

ldd -r the gsl libs should show no undefined references.
see [http://wiki.mandriva.com/en/Underlinking](http://wiki.mandriva.com/en/Underlinking)

---

### Post by WebDrake on 2011-10-17
> **MadCow108 said:**
> assnumg gsl is correctly linked,no need to disable as-needed with autotools, just use it correctly.
libraries to link with go into LDADD or LIBS **not** LDFLAGS
with libtool the variable for the libtool files is LIBADD
Ahhh, now I understand what you're getting at.

Can't speak for the linking of GSL, but replacing the line in Makefile.am ```
libminga_la_LIBADD = $(SUBLIBS)
``` with ```
libminga_la_LIBADD = $(SUBLIBS) $(AM_LDFLAGS)
``` did the trick -- the library itself is now linking against GSL when it builds.

Previously libminga.la was being built with the command, ```
g++ -I.. -g -O2 -version-info 0:0:0  -o libminga.la -rpath /usr/local/lib info.lo minority/libminga-minority.la
```

Now, with $(AM_LDFLAGS) added to the libminga_la_LIBADD variable, it builds with,
```
g++ -I.. -g -O2 -version-info 0:0:0  -o libminga.la -rpath /usr/local/lib info.lo minority/libminga-minority.la -lgsl -lgslcblas -lm
```

... and the executables thus build correctly against libminga.la without disabling the --as-needed flag.

Many, many thanks for the useful advice!

---

