---
title: "KDevelop help"
date: 2006-10-12
forum: Programming Talk
---

### Post by iand675@gmail.com on 2006-10-12
I'm trying to set up KDevelop, but whenever I try to run it (compile/link), I get this:

```

cd '/home/***/programming/helloworld' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -f Makefile.cvs && mkdir '/home/* **/programming/helloworld/debug' && cd '/home/***/programming/helloworld/debug' && CFLAGS="-O0 -g3 " "/home/***/programming/helloworld/configure" --enable-debug=full && cd '/home/***/programming/helloworld/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
aclocal
aclocal: configure.in: 8: macro `AM_PROG_LIBTOOL' not found in library
make: *** [all] Error 1
*** Exited with status: 2 ***

```

How can I fix that?

---

### Post by Guido Loupias on 2006-10-12
I'm only guessing here. But try to install the package *libtool* from the repos and try again. Also install autoconf, automake and autotools if you haven't done so already.

---

