---
title: "automake error compiling Osmo"
date: 2014-04-05
forum: Packaging and Compiling Programs
---

### Post by crcarson on 2014-04-05
First time trying to compiling a source package.  Running autogen.sh which calls automake get the following warnings (errors)

automake: warnings are treated as errors
po/Makefile.am:2: warning: wildcard ../src/*.c ../src/*.h: non-POSIX variable name
po/Makefile.am:2: (probably a GNU make extension)
po/Makefile.am:21: warning: '%'-style pattern rules are a GNU make extension
po/Makefile.am:24: warning: '%'-style pattern rules are a GNU make extension
src/Makefile.am:1: warning: ':='-style assignments are not portable
src/Makefile.am:1: warning: shell if test -e .svn; then echo -DREV=\"`LC_ALL=C svn info | sed -n '/^Rev/p'| sed -e 's/^Revision:\ //'`\"; fi;: non-POSIX variable name
src/Makefile.am:1: (probably a GNU make extension)
src/Makefile.am:2: warning: ':='-style assignments are not portable
src/Makefile.am:2: warning: shell echo $(VERSION: non-POSIX variable name
src/Makefile.am:2: (probably a GNU make extension)
src/Makefile.am:3: warning: ':='-style assignments are not portable
src/Makefile.am:3: warning: shell echo $(VERSION: non-POSIX variable name
src/Makefile.am:3: (probably a GNU make extension)
src/Makefile.am:4: warning: ':='-style assignments are not portable
src/Makefile.am:4: warning: shell echo $(VERSION: non-POSIX variable name
src/Makefile.am:4: (probably a GNU make extension)
src/Makefile.am: installing './depcomp'
src/Makefile.am:62: warning: 'CFLAGS' is a user variable, you should not override it;
src/Makefile.am:62: use 'AM_CFLAGS' instead
done


What is automake trying to tell me and what should I do to correct this?

---

### Post by crcarson on 2014-04-05
Had to change autogen.sh to call aclocal-1.10 and automake-1.10 rather than aclocal (aclocal-1.14) and automake (automake-1.14).

---

