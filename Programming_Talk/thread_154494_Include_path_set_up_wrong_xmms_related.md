---
title: "Include path set up wrong?? xmms related"
date: 2006-04-03
forum: Programming Talk
---

### Post by skinny on 2006-04-03
Hi i'm quite new to Ubuntu and linux in general but have been happily using it for a few months. I've compiled and built several programs, but now there is some that just won't compile. It doesn't appear to be a library issue. It seems more like a path isn't setup right.

skinny@uberskinny:~/downloads/xmmspipe-js$ make
gcc -O2 -Wall -fomit-frame-pointer -funroll-all-loops -finline-functions -ffast-math `xmms-config --cflags` -D_REENTRANT -c xmmspipe.c -fPIC
/bin/sh: xmms-config: command not found
xmmspipe.c:26:18: error: glib.h: No such file or directory
xmmspipe.c:27:21: error: gtk/gtk.h: No such file or directory
xmmspipe.c:31:25: error: xmms/plugin.h: No such file or directory
xmmspipe.c:32:27: error: xmms/xmmsctrl.h: No such file or directory
xmmspipe.c:33:29: error: xmms/configfile.h: No such file or directory
In file included from xmmspipe.c:56:
xmmspipe.h:28: error: syntax error before ‘gint’
xmmspipe.h:28: warning: no semicolon at end of struct or union
...
etc

i have libglib2.0-data and -dev installed, and i can see in the include directories for glib-2.0 and gtk-2.0 so why are they not being found?

all suggestions welcome, thanks

skinny

---

### Post by hod139 on 2006-04-03
Try installing xmms-dev and see what happens.  It should fix all the xmms errors, and hopefully the glib and gtk ones as well.

---

### Post by skinny on 2006-04-03
cheers hod139. when xmms-dev was being installed it added some different glib and gtk things as well, and now it compiles :)

skinny

---

