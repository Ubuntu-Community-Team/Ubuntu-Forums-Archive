---
title: "Building and linking against local non-installed GTK"
date: 2006-02-26
forum: Programming Talk
---

### Post by stoffe on 2006-02-26
Hello. I'm hacking a little in the GTK+ libs, I pulled down the sources from the repos with apt-get source, but now when I want to test my modifications it would be great to not have to install it all the time, not to mention to not risk the system. I wonder if anyone has any experience in building/linking against local resources?

I've built GTK with my modifications but not installed it. No errors. I've hardcoded include paths and library linkage (direct to .so) for GTK and GDK, then copied the rest of the declarations for pango etc from pkg-config. Test applications build, no errors. But it still behaves as if built against the main GTK.

Here's my makefile for a test application, I know that some lines are uneccesary but they do no harm either. I'm not very good at Makefiles and/or linking and compiling, but it works well enough to make the simplistic app without errors. Except actually doing as expected. :)

```
CC = gcc

CFLAGS = -Wall			 	\
	-DG_DISABLE_DEPRECATED 	 	\
	-DGDK_DISABLE_DEPRECATED 	\
	-DGDK_PIXBUF_DISABLE_DEPRECATED \
	-DGTK_DISABLE_DEPRECATED
INC = -I/home/stoffe/Projects/gtk+2.0-2.8.13/upstream/tarballs/gtk+-2.8.13 \
      -I/home/stoffe/Projects/gtk+2.0-2.8.13/upstream/tarballs/gtk+-2.8.13/gdk \
      -I/usr/include/atk-1.0 -I/usr/include/cairo \
      -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include

LIB = -L/home/stoffe/Projects/gtk+2.0-2.8.13/upstream/tarballs/gtk+-2.8.13/gtk \
      -L/home/stoffe/Projects/gtk+2.0-2.8.13/upstream/tarballs/gtk+-2.8.13/gtk/.libs \
      /home/stoffe/Projects/gtk+2.0-2.8.13/upstream/tarballs/gtk+-2.8.13/gtk/.libs/libgtk-x11-2.0.so \
      /home/stoffe/Projects/gtk+2.0-2.8.13/upstream/tarballs/gtk+-2.8.13/gdk/.libs/libgdk-x11-2.0.so \
      -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext \
      -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0
nb_test: nb_test.c 
	$(CC) nb_test.c -o nb_test $(CFLAGS) $(INC) $(LIB)

clean: 
	rm -f *.o nb_test

```
What am I doing wrong? Any tips would be appreciated.

---

