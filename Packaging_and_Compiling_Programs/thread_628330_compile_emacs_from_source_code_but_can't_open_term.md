---
title: "compile emacs from source code but can't open termcap database file"
date: 2007-12-01
forum: Packaging and Compiling Programs
---

### Post by LaoLiulaoliu on 2007-12-01
emacs: Cannot open termcap database file

I just want to install emacs by hand.
tar the xx.tar.gz file and then ./configure && make
src/emacs -q to check whether this program work.
the error comes:
emacs: Cannot open termcap database file
And the etc/PROBLEM don't have this problem.

Here is head of my config.log
  $ ./configure 

## --------- ##
## Platform. ##
## --------- ##

hostname = artist
uname -m = i686
uname -r = 2.6.22-14-generic
uname -s = Linux
uname -v = #1 SMP Sun Oct 14 23:05:12 GMT 2007

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
/usr/bin/hostinfo      = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:2094: checking build system type
configure:2112: result: i686-pc-linux-gnu
configure:2134: checking host system type
configure:2149: result: i686-pc-linux-gnu
configure:3284: checking for gcc
configure:3300: found /usr/bin/gcc
configure:3311: result: gcc
configure:3549: checking for C compiler version
configure:3556: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3559: $? = 0
configure:3566: gcc -v >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.1.3 --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu

---

### Post by dholbach on 2007-12-03
Is this the full config.log?

Why don't you use the one in the archive?

Try installing Build-Depends by running    sudo apt-get build-dep emacs22

---

