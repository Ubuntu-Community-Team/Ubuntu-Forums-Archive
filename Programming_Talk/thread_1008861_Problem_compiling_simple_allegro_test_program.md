---
title: "Problem compiling simple allegro test program"
date: 2008-12-12
forum: Programming Talk
---

### Post by jlmeza on 2008-12-12
Hi, I am new to Linux so please bare with me. I am trying to compile a simple program to test that I have installed all the allegro libs correctly. I am trying to compile with the following:

make testgcc -O -Wall  -o test2 test2.c -L/usr/local/lib -L/usr/X11R6/bin -lalleg -lpthread -lXxf86dga -lXxf86vm -ldl -lX11

But I get the following errors which make me think I am not including some library it is looking for:

/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/liballeg.a(xwin.o): In function `_xwin_private_set_window_defaults':
(.text+0x9410): undefined reference to `XpmCreatePixmapFromData'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/liballeg.a(xwin.o): In function `_xwin_hide_x_mouse':
(.text+0x9482): undefined reference to `XcursorImageDestroy'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/liballeg.a(xwin.o): In function `_xwin_private_create_window':
(.text+0x97a7): undefined reference to `XcursorSupportsARGB'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/liballeg.a(xwin.o): In function `_xwin_show_mouse':
(.text+0xb366): undefined reference to `XcursorImageLoadCursor'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/liballeg.a(xwin.o): In function `_xwin_set_mouse_sprite':
(.text+0xb427): undefined reference to `XcursorImageDestroy'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/liballeg.a(xwin.o): In function `_xwin_set_mouse_sprite':
(.text+0xb46e): undefined reference to `XcursorImageCreate'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/liballeg.a(xwin.o): In function `_xwin_destroy_window':
(.text+0xe3a0): undefined reference to `XcursorImageDestroy'
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/liballeg.a(digmid.o): In function `digmid_init':
(.text+0x198b): undefined reference to `pow'
collect2: ld returned 1 exit status
make: *** [test] Error 1

Can someone help with this problem please?

My program is as follows:

 22 #ifdef HAVE_CONFIG_H
 23 #include <config.h>
 24 #endif
 25 
 26 #include <stdio.h>
 27 #include <stdlib.h>
 28 #include <allegro.h>
 29 
 30 int main(int argc, char *argv[])
 31 {
 32     char version[80];
 33     allegro_init();
 34     sprintf(version, "Allegro library version = %s", allegro_id);
 35     allegro_message(version);
 36     return 0;
 37   //printf("Hello, world!\n");
 38 
 39   //return EXIT_SUCCESS;
 40 }
 41 END_OF_MAIN();

Thanx

---

### Post by dwhitney67 on 2008-12-12
> **jlmeza said:**
> ...

make testgcc -O -Wall  -o test2 test2.c -L/usr/local/lib -L/usr/X11R6/bin -lalleg -lpthread -lXxf86dga -lXxf86vm -ldl -lX11


Try:
```

gcc -O -Wall test2.c -o test2 `allegro-config --libs`

```
From looking at your code, I cannot determine why you attempted to link in the pthread library.

As for the final error, concerning pow, that was generated because you are missing the math library.  If you still have an undefined reference for "pow", then add to the statement above a -lm (that's a dash-ell-m).

---

### Post by jlmeza on 2008-12-12
Thanks your suggestion worked no problem. Can you explain though why I have to use `allegro-config --libs`. I am using a book to learn game programming and thats why I included all those libs.

---

### Post by dwhitney67 on 2008-12-12
You do not have to use the `allegro-config --libs`, but it makes life easier.

To see what is generated from the statement, just run it in a terminal (without the back-ticks).  It should present to you the output of libraries and library paths that are needed for developing applications using the allegro library suite.

---

