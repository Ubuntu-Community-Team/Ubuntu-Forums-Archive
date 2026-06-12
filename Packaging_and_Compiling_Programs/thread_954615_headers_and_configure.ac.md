---
title: "headers and configure.ac"
date: 2008-10-21
forum: Packaging and Compiling Programs
---

### Post by Alason on 2008-10-21
Hello,

at first sorry for my bad english.

My problem, I wrote a program in c/c++ and I would like to published them. 

The program use gnuplot and needs gsl, lapack, arpack, arpack++, arpack++-dev (with the files ardsmat.h, ardssym.h).

I wrote a "Makefile.am" and a "configure.ac". when I type in the console:

> 
autoreconf --install && ./configure


I get the following (error) messages

> 
[...]
checking for gnuplot... no
configure: WARNING: Graphical Output of Isomap is not available
checking for main in -llapack... yes
checking for main in -larpack... yes
checking for main in -larpack++... yes
./configure: line 20036: ac_cv_lib_arpack++=ac_cv_lib_arpack++_main: command not found
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking gsl/gsl_diff.h usability... yes
checking gsl/gsl_diff.h presence... yes
checking for gsl/gsl_diff.h... yes
checking cstdio usability... no
checking cstdio presence... no
checking for cstdio... no
checking arpack++/ardsmat.h usability... no
checking arpack++/ardsmat.h presence... no
checking for arpack++/ardsmat.h... no
checking ardssym.h usability... no
checking ardssym.h presence... no
checking for ardssym.h... no
[...]
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: executing depfiles commands


What I have to change in "configure.ac" therewith "./configure" find the headers and gnuplot?

**Thank you very much!**





Gnuplot was compiled in $HOME/install/src and installed in $HOME/bin

The headers can be found in
> 
locate cstdio
/usr/include/c++/4.2/cstdio
/usr/include/c++/4.2/tr1/cstdio


> 
locate arpack++/ardsmat.h
/usr/include/arpack++/ardsmat.h


> 
locate gsl/gsl_diff.h
/usr/include/gsl/gsl_diff.h



The **configure.ac**
> 
AC_PREREQ(2.59)
AC_INIT([XY], [0.1], [my@email.eu])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
AC_CONFIG_HEADERS([config.h])

# Checks for programs.
AC_PROG_CXX
AC_PROG_CC
AC_PROG_MAKE_SET
AC_PROG_LIBTOOL
AC_CHECK_PROGS([GP], [gnuplot], [:])
if test "$GP" = :; then
 AC_MSG_WARN([Graphical Output of XY is not available])
fi

# Checks for libraries.
#AC_HAVE_LIBRARY([gsl])
#AC_HAVE_LIBRARY([gslcblas])
AC_HAVE_LIBRARY([lapack])
AC_HAVE_LIBRARY([arpack])
AC_HAVE_LIBRARY([arpack++])

# Checks for header files.
AC_HEADER_STDC
AC_CHECK_HEADERS([stdlib.h string.h gsl/gsl_diff.h],,[exit])
AC_CHECK_HEADERS([cstdio arpack++/ardsmat.h ardssym.h])


# Checks for typedefs, structures, and compiler characteristics.
AC_HEADER_STDBOOL
AC_C_CONST
AC_C_INLINE
AC_TYPE_SIZE_T

# Checks for library functions.
AC_FUNC_MALLOC

AC_CONFIG_FILES([Makefile])
AC_OUTPUT


---

