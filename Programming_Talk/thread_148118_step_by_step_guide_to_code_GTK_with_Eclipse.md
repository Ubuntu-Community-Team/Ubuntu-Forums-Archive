---
title: "step by step guide to code GTK with Eclipse"
date: 2006-03-21
forum: Programming Talk
---

### Post by rupert on 2006-03-21
Hi,
i would like to switch to eclipse and code my GTK+ Stuff there, but I cant find any Guides how I have to configure all the include path and compiler flags to get my sources compiled under Eclipse.

thx for help

---

### Post by benguin on 2006-03-21
Hey there,
I use Eclipse for C++ stuff, and one of my projects is in GTK+ (multi-threaded gtkmm, actually). I do not use a managed make process however; I write my own makefiles, utilizing pkg-config to find the libs and include paths. If that's what you want, I can post a little howto here for you.

Cheers,
-J-

---

### Post by rupert on 2006-03-21
sure why not, i tried it once but maybe i gave it not enough time...

---

### Post by benguin on 2006-03-21
okay cool. Just gimme a day, right now kinda busy with meeting a deadline; I'll post it tomorrow night.

Cheers,
-J-

---

### Post by rupert on 2006-03-26
im trying right now to get a makefile working,
it looks like this:
```

#CFLAGS=`-l/user/include/gtk-2.0 -l/user/lib/gtk-2.0 -l/usr/include/atk-1.0 -l/user/include/cairo -l/user/include/pango-1.0 -l/user/include/glib-2.0 -l/user/lib/glib-2.0/include -L/user/lib/mysql -lmysqlclient`
CFLAGS='-I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/user/lib/mysql -Imysqlclient'

#PACKAGE_LIBS = -lgtk-x11-2.0 -latk-1.0 -lgdk-x11-2.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lXrender -lX11 -ldl  

CC = gcc

$(CC) $(CFLAGS) -o $@ main.c 

```
How can i add a second file?
I have a functions.c that needs to be included!
The compiler says there i a space missing in the last line, why?

thx

---

### Post by benguin on 2006-03-26
[QUOTE=rupert]im trying right now to get a makefile working,
it looks like this:
```

#CFLAGS=`-l/user/include/gtk-2.0 -l/user/lib/gtk-2.0 -l/usr/include/atk-1.0 -l/user/include/cairo -l/user/include/pango-1.0 -l/user/include/glib-2.0 -l/user/lib/glib-2.0/include -L/user/lib/mysql -lmysqlclient`
CFLAGS='-I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/user/lib/mysql -Imysqlclient'

#PACKAGE_LIBS = -lgtk-x11-2.0 -latk-1.0 -lgdk-x11-2.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lXrender -lX11 -ldl  

CC = gcc

$(CC) $(CFLAGS) -o $@ main.c 

```
How can i add a second file?
I have a functions.c that needs to be included!
The compiler says there i a space missing in the last line, why?

thx[/QUOTE]

Hey there,
Lets say you have two files handlers.c and mail.c, and want to build them using a makefile. Try this:

```

CC=gcc
LDFLAGS=`pkg-config --libs gtk+-2.0`
CFLAGS=`pkg-config --cflags gtk+-2.0` -g3

main_progr: main.o handlers.o
[TAB]$(CC) main.o handlers.o -o main_progr $(LDFLAGS)

main.o:main.c
[TAB]$(CC) -c main.c -o main.o $(CFLAGS)

handlers.o:handlers.c
[TAB]$(CC) -c handlers.c -o handlers.o $(CFLAGS)

```

The place where I write [TAB] is important, because you have to press tab and insert a tabspace in that area; make is picky about that.

Hope that helps. Ofcourse add your mysql libs and headers; this example is for pure gtk only applications.

-J-

---

### Post by rupert on 2006-03-27
mmh, the linker or compiler give me a message that it cant find the .h files,
also adding the wont work, i tried youre cflags and mine:
```

CC=gcc
#LDFLAGS=`pkg-config --libs gtk+-2.0`
CFLAGS=`pkg-config --cflags gtk+-2.0 -I/user/lib/mysql -Imysqlclient` -g3
#CFLAGS=`-I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/user/lib/mysql -Imysqlclient` -g3
LDFLAGS=`-lgtk-x11-2.0 -latk-1.0 -lgdk-x11-2.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXinerama -lXi -lXrandr -lXext -lXcursor -lXfixes -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -lXrender -lX11 -ldl`


main_progr: main.o functions.o
	$(CC) main.o functions.o -o main_progr $(LDFLAGS)

main.o:main.c
	$(CC) -c main.c -o main.o $(CFLAGS)

functions.o:functions.c
	$(CC) -c functions.c -o functions.o $(CFLAGS)

```

---

