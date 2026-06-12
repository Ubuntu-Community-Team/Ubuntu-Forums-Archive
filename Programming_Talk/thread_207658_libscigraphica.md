---
title: "libscigraphica"
date: 2006-07-02
forum: Programming Talk
---

### Post by frogotronic on 2006-07-02
I'm trying to compile/install libscigraphica to be able to install scigraphica.

Can't seem to get libscigraphica to install.   I get

```
 *******[Error 1]  all recursive
```


when I use the command ```
sudo make
```


I think its a general (non-scigraphica) make related error

any suggestions?

---

### Post by frogotronic on 2006-07-02
Update to make error when running ```
sudo make
``` with libscigraphica2.1.0 after running ```
sudo sh ./configure
``` with no errors (on configure).

Error with make is 

```
gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../pixmaps -I../../scigraphica -I../../scigraphica/dialogs -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/local/include/gtkextra-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/python2.4 -g -O -W -Wall -DWITH_WARNINGS -MT sg_dialog.lo -MD -MP -MF .deps/sg_dialog.Tpo -c sg_dialog.c  -fPIC -DPIC -o .libs/sg_dialog.lo
In file included from /usr/include/python2.4/Python.h:8,
                 from ../../scigraphica/sg_python.h:26,
                 from ../../scigraphica/sg.h:44,
                 from sg_dialog.c:21:
/usr/include/python2.4/pyconfig.h:835:1: warning: "_POSIX_C_SOURCE" redefined
In file included from /usr/include/limits.h:26,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:122,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.0.3/include/limits.h:11,
                 from /usr/lib/glib-2.0/include/glibconfig.h:11,
                 from /usr/include/glib-2.0/glib/gtypes.h:30,
                 from /usr/include/glib-2.0/glib/galloca.h:30,
                 from /usr/include/glib-2.0/glib.h:30,
                 from /usr/include/gtk-2.0/gdk/gdktypes.h:32,
                 from /usr/include/gtk-2.0/gdk/gdkcolor.h:31,
                 from /usr/include/gtk-2.0/gdk/gdkcairo.h:23,
                 from /usr/include/gtk-2.0/gdk/gdk.h:30,
                 from /usr/include/gtk-2.0/gtk/gtk.h:31,
                 from sg_dialog.c:19:
/usr/include/features.h:190:1: warning: this is the location of the previous definition
In file included from ../../scigraphica/sg.h:44,
                 from sg_dialog.c:21:
../../scigraphica/sg_python.h:35:25: error: arrayobject.h: No such file or directory
sg_dialog.c:48: warning: unused parameter 'dialog'
sg_dialog.c:56: warning: unused parameter 'dialog'
sg_dialog.c:57: warning: unused parameter 'event'
sg_dialog.c:68: warning: unused parameter 'dialog'
sg_dialog.c:248: warning: unused parameter 'button'
sg_dialog.c:256: warning: unused parameter 'button'
sg_dialog.c:264: warning: unused parameter 'button'
sg_dialog.c:272: warning: unused parameter 'button'
sg_dialog.c:280: warning: unused parameter 'button'
make[3]: *** [sg_dialog.lo] Error 1
make[3]: Leaving directory `/home/andor/Downloads/libscigraphica-2.1.0/scigraphica/widgets'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/andor/Downloads/libscigraphica-2.1.0/scigraphica'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/andor/Downloads/libscigraphica-2.1.0'
make: *** [all] Error 2
```

---

### Post by nicker2005 on 2006-12-08
Try

./configure --with-python-numeric-path=/usr/include/python2.4/numarray/


Good luck!

---

### Post by frogotronic on 2006-12-08
> **nicker2005 said:**
> Try

./configure --with-python-numeric-path=/usr/include/python2.4/numarray/


Good luck!

cool...I'll try this and let you know.

- CH

---

