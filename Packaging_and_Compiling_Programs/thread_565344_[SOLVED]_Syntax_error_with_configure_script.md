---
title: "[SOLVED] Syntax error with configure script"
date: 2007-10-02
forum: Packaging and Compiling Programs
---

### Post by WebDrake on 2007-10-02
Hello all,

I'm trying to build a library (my own creation) using the GNU Autotools.  Since upgrading to Gutsy beta, I've run into a problem.  I've issued the commands,
```

autoreconf -i
./configure
```
... and some way through the running of the configure file, get an error:
```

checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
./configure: line 10170: syntax error near unexpected token `DEPS,gsl'
./configure: line 10170: `PKG_CHECK_MODULES(DEPS,gsl >= 1.8)'

```

The configure.ac file is as follows:
```

AC_INIT([minga],[0.0.1])
AC_CONFIG_SRCDIR([minga_version.c])
AC_CONFIG_AUX_DIR([build-aux])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])

AC_CONFIG_HEADERS([config.h])

MINGA_LT_VERSION="0:0:0"
AC_SUBST(MINGA_LT_VERSION)

AC_LANG(C)
AC_PROG_CC
AC_PROG_CPP
AC_PROG_LN_S

dnl Disable unnecessary libtool tests for C++, FORTRAN and Java
define([AC_LIBTOOL_LANG_CXX_CONFIG],[:])dnl
define([AC_LIBTOOL_LANG_F77_CONFIG],[:])dnl
define([AC_LIBTOOL_LANG_GCJ_CONFIG],[:])dnl
AC_PROG_LIBTOOL

PKG_CHECK_MODULES(DEPS,[gsl >= 1.8])
AC_SUBST(DEPS_CFLAGS)
AC_SUBST(DEPS_LIBS)

MINGA_CFLAGS="-I$includedir $DEPS_CFLAGS"
MINGA_LDFLAGS="$DEPS_LIBS"
MINGA_LIBS="-L$libdir -lminga $MINGA_LDFLAGS"

AC_SUBST([MINGA_CFLAGS])
AC_SUBST([MINGA_LDFLAGS])
AC_SUBST([MINGA_LIBS])

AC_CONFIG_FILES([minga.pc minga/Makefile agents/Makefile anal/Makefile error/Makefile games/Makefile rng/Makefile Makefile demos/Makefile])
AC_OUTPUT

```

Can anyone suggest what the problem is?  As a (very) amateurish user of the Autotools I really have no idea.

---

### Post by WebDrake on 2007-10-02
D'oh.  Of course, pkg-config was not installed.

```

sudo apt-get install pkg-config

```

*smacks self over head*

---

