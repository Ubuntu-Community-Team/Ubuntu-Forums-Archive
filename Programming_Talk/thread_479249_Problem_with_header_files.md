---
title: "Problem with header files"
date: 2007-06-20
forum: Programming Talk
---

### Post by 3saul on 2007-06-20
I've just re-installed my system (Ubuntu 7.04) and the Anjuta 2.1.3 debs. Now I can't compile my apps (yes I've installed all the dev libraries and headers). Here's the first error

/usr/include/gtk-2.0/gdk/gdkcolor.h:30:19: error: cairo.h: No such file or directory

The file is absolutely there... any ideas?

---

### Post by visik7 on 2007-06-20
1st are you sure that libcairo2-dev is installed ?
2nd maybe you need to pass to gcc the output of pkg-config --cflags cairo

---

