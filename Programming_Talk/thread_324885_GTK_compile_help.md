---
title: "GTK compile help"
date: 2006-12-24
forum: Programming Talk
---

### Post by spookyct on 2006-12-24
Hey, I am having tons of trouble compiling a simple program using the GTK libraries.  I think the reason is that g++ can't find them....  neither can I.  A friend told me that Ubuntu comes with GTK.  Can anyone help me out?  Ive been stuck on this for days....  I've read tons of FAQ's but can't find anything that works.  ](*,)   Thanks!

---

### Post by lnostdal on 2006-12-24
> **spookyct said:**
> Hey, I am having tons of trouble compiling a simple program using the GTK libraries.  I think the reason is that g++ can't find them....  neither can I.  A friend told me that Ubuntu comes with GTK.  Can anyone help me out?  Ive been stuck on this for days....  I've read tons of FAQ's but can't find anything that works.  ](*,)   Thanks!

```
aptitude search libgtk
``` ..gives some hints, and:

```
aptitude install libgtk2.0-dev
``` ..is what you want .. consider getting libgtk2.0-doc also

then compile using pkg-config to generate arguments for gcc:
```
gcc -Wall -g -c helloworld.c `pkg-config --cflags gtk+-2.0`
```
..and link:
```
gcc -Wall -g helloworld.o -o helloworld `pkg-config --libs gtk+-2.0`
```

---

### Post by spookyct on 2006-12-27
I am getting the same error....  does it matter where hello.cpp is?

also im using c++ not c.  does that make a difference?

the install worked though


"gcc: pkg-config -cflags gtk+-2.0: No such file or directory
hello.c:1:21: error: gtk/gtk.h: No such file or directory
"

i get those errors compiling with gcc and g++

---

### Post by duff on 2006-12-27
> **spookyct said:**
> 
"gcc: pkg-config -cflags gtk+-2.0: No such file or directory
hello.c:1:21: error: gtk/gtk.h: No such file or directory
"


Are you sure you're using backticks? (That's the tick mark on the tilde ~ key).  And it's two dashes in front of cflags "--cflags".  And, yes, you have to use g++ if your compiling c++ code.

---

### Post by spookyct on 2006-12-27
got it to work...  thanks a lot...  you guys rock!

I wasn't using backticks

---

### Post by OlJanx on 2007-01-05
I've had the same problem, it compiles fine but I can't link:

g++ -Wall -g test.o -o test `pkg-config --libs gtk+-2.0`

/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgdk-x11-2.0.so: undefined reference to `cairo_xlib_surface_create_for_bitmap'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgdk-x11-2.0.so: undefined reference to `cairo_xlib_surface_create'
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libgdk-x11-2.0.so: undefined reference to `cairo_xlib_surface_set_size'
collect2: ld returned 1 exit status

As far as I can tell cairo is current, but being fairly new I'm not sure...
I'm trying to build the hello world code from [http://www.gtk.org/tutorial/c39.html#SEC-HELLOWORLD](http://www.gtk.org/tutorial/c39.html#SEC-HELLOWORLD)

---

