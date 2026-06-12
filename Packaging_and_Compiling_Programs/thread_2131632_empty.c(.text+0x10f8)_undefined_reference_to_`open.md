---
title: "empty.c:(.text+0x10f8): undefined reference to `openpty'"
date: 2013-04-02
forum: Packaging and Compiling Programs
---

### Post by jfmxl on 2013-04-02
I'm trying to compile a c language program ... 'empty' ... but ld complains it cannot find 'openpty' or 'login_tty'.  Here's the full return ....

jfl@ws7:~/Downloads/empty-0.6.18b$ make
gcc  -Wall -lutil -o empty empty.c
/tmp/ccG9pZWz.o: In function `main':
empty.c:(.text+0x10f8): undefined reference to `openpty'
empty.c:(.text+0x118e): undefined reference to `login_tty'
collect2: ld returned 1 exit status
make: *** [all] Error 1

Googling the whereabouts of the functions leads me to believe they are in /usr/lib/libutil.so.

My system ... 11.10 ... has no such library, which explains why I cannot compile the program.

I cannot find any libutil package for 11.10.

Where are 'openpty' and 'login_tty' to be found on ubuntu 11.10?

Thanks.

---

### Post by steeldriver on 2013-04-02
Try moving '-lutil' after 'empty.c' on the gcc command line

> It makes a difference where in the command you write this option; the linker searches and processes libraries and object files in the order they are specified. Thus, ‘foo.o -lz bar.o’ searches library ‘z’ after file foo.o but before bar.o. If bar.o refers to functions in ‘z’, those functions may not be loaded.

[http://gcc.gnu.org/onlinedocs/gcc/Link-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Link-Options.html)

In 12.04 libutil is part of the libc6-dev package - don't know about 11.10, sorry

---

### Post by jfmxl on 2013-04-02
Here're the relevant lines in the makefile ...

CC =	gcc
LIBS =	-lutil

PREFIX = /usr/local

all:
	${CC} ${CFLAGS} -Wall ${LIBS} -o empty empty.c

---

### Post by jfmxl on 2013-04-02
CC =	gcc
LIBS =	-lutil

PREFIX = /usr/local

all:
	${CC} ${CFLAGS} -Wall -o empty empty.c ${LIBS}

seems to have done the trick! Who'd a thunk it? Thanks.

---

