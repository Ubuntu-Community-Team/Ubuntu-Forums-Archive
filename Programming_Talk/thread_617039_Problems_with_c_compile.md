---
title: "Problems with c compile"
date: 2007-11-18
forum: Programming Talk
---

### Post by saphil on 2007-11-18
I get this response when I attempt to install C-SNOBOL4 on feisty
```

wolf@prospero:~/snobol-0.99.4$ sudo make
./configure
autoconf: no input file
autoconf failed
make: *** [config.m4] Error 1
wolf@prospero:~/snobol-0.99.4$ 

```

On the "autoconf: no input file", what file do you suppose it is looking for?

It makes sense that the make command fails without a configuration set, I guess.

---

### Post by jfinkels on 2007-11-18
Have you done ```
./configure
```first? Also, you shouldn't need to run make as root. Just do ```
make
```

---

### Post by samjh on 2007-11-19
You have to first do:
```
./configure
```

Then:
```
make
```

Make doesn't need to be invoked with admin privileges: ie. you don't need su or sudo.

If you have downloaded the program from svn, you may need to do this before running ./configure:
```
./autogen.sh
```

Most source-code packages will come included with a COMPILE, README, or INSTALL files which include instructions on how to compile the software.  Make sure you look for and read those.

---

### Post by saphil on 2007-11-19
thanks!

ok, I checked the permisions and changed the whole collection to chown me, and unlocked all the read-only files for the moment.
```
wolf@prospero:~/snobol-0.99.4$ ./configure
autoconf: **no input file**
autoconf failed

```

running ./autoconf on its own gets me
```
wolf@prospero:~/snobol-0.99.4$ ./autoconf
# config generated Mon Nov 19 09:09:24 EST 2007 on prospero (i686-pc-linux-gnu)
looking for gcc
found gcc in /usr/bin
using gcc
include(config/gcc.m4)
CC=gcc
# Using built-in specs.
# Target: i486-linux-gnu
# Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
# Thread model: posix
# gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
using posix config file
include(config/posix.m4)
using POSIX unistd.h
HAVE_UNISTD_H=-DHAVE_UNISTD_H
using ranlib
using uname(2) for system name information
using BSD string functions
using sockets for TCP
using termios.h for tty modes
using system provided getopt() function
using dlopen() for LOAD() support
LOAD_C=$(SRCDIR)lib/unix98/load.c
SNOLIB_FILE=snolib.so
using -ldl
ADD_LDFLAGS(-ldl)
# if the file local-config exists it will be included here

```


The iNSTALL file just says run make.  The makefile includes the command ./configure in this case.

---

### Post by jespdj on 2007-11-21
Try running [FONT="Courier New"]./autogen.sh[/FONT] first as is suggested by the other posters above.

---

### Post by saphil on 2007-11-21
Sorry, I don't have that file, [FONT=Courier New]autogen.sh,[/FONT] in the directory.  Where would it be found?

OK, I found an example in /usr/share/doc/autotools-dev/examples

wolf@prospero:~/snobol-0.99.4$ ./autogen.sh
Cleaning autotools files...
Running autoreconf...
autoreconf: `configure.ac' or `configure.in' is required

Does this mean my source is corrupt or missing pieces?

It also erased the configure file that was there, but I had a copy in the .gz file

---

### Post by jfinkels on 2007-11-21
When in doubt, go back to the website from which you got this package and contact the maintainer as a last resort.

---

### Post by saphil on 2007-11-22
[quote=jfinkels]When in doubt, go back to the website from which you got this package and contact the maintainer as a last resort.[/quote]  

I think this may be that resort.  Thanks Y'all

Happy Thanksgiving (or happy thursday) :KS

---

