---
title: "XPLAB ocr pattern recogniton"
date: 2010-10-03
forum: Packaging and Compiling Programs
---

### Post by phenest on 2010-10-03
I came across this: [XPLAB]("http://www.pattern-lab.de/"). I've not been successful at compiling it, but it looks very good judging by the screenshots. It looks way more advanced than any other ocr app I've seen and used, and Linux in general could do with some thing like this.

If some one could compile this, or help me, I'd appreciate it.

My own attempt at compiling:
```
13:29: ~/downloads/xplab-0.4.5/src $ make
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
xplab_init_types.c ... xplab_init_types.c:39:21: error: gtk/gtk.h: No such file or directory
In file included from xplab_init_types.c:40:
xplab_init_defs.h:1454: error: ‘guchar’ undeclared here (not in a function)
xplab_init_defs.h:1454: error: expected ‘)’ before numeric constant
xplab_init_defs.h:1455: error: expected ‘)’ before numeric constant
xplab_init_defs.h:1456: error: expected ‘)’ before numeric constant
xplab_init_defs.h:1457: error: expected ‘)’ before numeric constant
xplab_init_defs.h:1458: error: expected ‘)’ before numeric constant
xplab_init_defs.h:1459: error: expected ‘)’ before numeric constant
xplab_init_defs.h:1460: error: expected ‘)’ before numeric constant
xplab_init_defs.h:1461: error: expected ‘)’ before numeric constant
xplab_init_defs.h:1462: error: expected ‘)’ before numeric constant
In file included from xplab_init_types.c:40:
xplab_init_defs.h:1977: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘nr_sqrarg’
In file included from xplab_init_types.c:41:
xplab_init_types.h:29: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘pack_def’
xplab_init_types.h:32: error: expected specifier-qualifier-list before ‘gdouble’
cc1: warnings being treated as errors
xplab_init_types.h:33: error: struct has no members
xplab_init_types.h:227: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘kern_def’
xplab_init_types.h:230: error: expected specifier-qualifier-list before ‘gint’
xplab_init_types.h:233: error: struct has no members
xplab_init_types.h:236: error: expected specifier-qualifier-list before ‘gint’
xplab_init_types.h:239: error: struct has no members
xplab_init_types.h:242: error: expected specifier-qualifier-list before ‘gint’
xplab_init_types.h:245: error: struct has no members
xplab_init_types.h:248: error: expected specifier-qualifier-list before ‘gdouble’
xplab_init_types.h:251: error: struct has no members
xplab_init_types.h:254: error: expected specifier-qualifier-list before ‘gdouble’
xplab_init_types.h:257: error: struct has no members
xplab_init_types.h:260: error: expected specifier-qualifier-list before ‘gint’
xplab_init_types.h:264: error: struct has no members
xplab_init_types.h:267: error: expected specifier-qualifier-list before ‘gint’
xplab_init_types.h:270: error: struct has no members
xplab_init_types.h:278: error: expected specifier-qualifier-list before ‘gdouble’
xplab_init_types.h:279: error: struct has no members
xplab_init_types.h:282: error: expected specifier-qualifier-list before ‘guchar’
xplab_init_types.h:283: error: struct has no members

```
...it goes on like this with 1000's of errors.

Where do I go from here? I'm running Lucid (fresh install), but that package is not showing.

---

### Post by SevenMachines on 2010-10-03
do you have libgtk2.0-dev installed?

---

### Post by phenest on 2010-10-03
> **SevenMachines said:**
> do you have libgtk2.0-dev installed?

That would help. :lol:

Still getting compile errors though.

---

### Post by SevenMachines on 2010-10-03
hmm, looking at it on maverick, the source would need work before it'll compile with newer gtk versions. i'm not sure how it is on lucid

---

### Post by phenest on 2010-10-03
Under Lucid (fresh install):
```
steve@virtual:~/Downloads/xplab-0.4.3/src$ make
xplab_init_types.c ... cc1: warnings being treated as errors
In file included from /usr/include/glib-2.0/glib/gasyncqueue.h:34,
                 from /usr/include/glib-2.0/glib.h:34,
                 from /usr/include/glib-2.0/gobject/gtype.h:26,
                 from /usr/include/glib-2.0/gobject/gboxed.h:26,
                 from /usr/include/glib-2.0/glib-object.h:25,
                 from /usr/include/glib-2.0/gio/gioenums.h:30,
                 from /usr/include/glib-2.0/gio/giotypes.h:30,
                 from /usr/include/glib-2.0/gio/gio.h:28,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from xplab_init_types.c:39:
/usr/include/glib-2.0/glib/gthread.h: In function ‘g_once_init_enter’:
/usr/include/glib-2.0/glib/gthread.h:348: error: cast discards qualifiers from pointer target type
make: *** [xplab_init_types.o] Error 1

```
There is a note in the 'read me' about GTK but maybe xplab is pre-lucid. Try in Karmic, perhaps?

---

### Post by SevenMachines on 2010-10-03
Although obviously not ideal, you might want to remove -Werror
from the Makefile. Fixing warnings is better but... :)

---

### Post by phenest on 2010-10-03
Had success under Debian Lenny. Need version 0.4.4 minimum as I'm compiling under 64 bit.

Now I've had a play with it, it's very long winded.

---

