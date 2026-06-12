---
title: "install library"
date: 2010-08-26
forum: Packaging and Compiling Programs
---

### Post by tbastian on 2010-08-26
I'm setting up autotools for my project, and everything in working, except that my library (libplot.so) gets installed to /usr/local/lib and my program looks for it in /usr/lib. How do I get it to install where linking will work automatically without manually creating a symbolic link?

Heres my Makefile.am
```

lib_LTLIBRARIES = libplot.la

plotincludedir = $(includedir)/plot
plotinclude_HEADERS = 		\
	canvas.h		\
	plot.h

libplot_la_SOURCES =		\
	$(plotinclude_HEADERS)	\
	canvas.c		\
	graph.c			\
	LinkedList.c		\
	plot.c			\
	skewt.c			\
	LinkedList.h		\
	Common.h		\
	graph.h

AM_CFLAGS = -Wall 		\
	`pkg-config gtk+-2.0 --cflags`

libplot_la_LDFLAGS = `pkg-config gtk+-2.0 --libs`

```

---

### Post by SevenMachines on 2010-08-26
Its more to do with the configure script
$ ./configure --prefix=/usr
then the right install locations in the Makefiles will be generated

---

### Post by tbastian on 2010-08-27
thanks. That seems to do the trick!

---

