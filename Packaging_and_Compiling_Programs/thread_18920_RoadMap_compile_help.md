---
title: "RoadMap compile help"
date: 2005-03-09
forum: Packaging and Compiling Programs
---

### Post by YoungNastyMan on 2005-03-09
Hi everyone, thank you for taking the time to look at this problem.

I am trying to compile and install [RoadMap](http://roadmap.digitalomaha.net), a vector based GPS mapping program.  I haven't been able to find a debian package for it, so I'm trying to compile it from source.  I've tried with warty, and upgrading to backports warty universe (which is what I'm running now).

The "easy" way to get this thing installed, is to download the Linux/i686 binaries, extract them, go to the gtk2 directory and type make install.  When I do this, this is what I get: (starting with the first error)

```

brian@carl:~/roadmap-1.0.9/src/gtk2 $ make install 
/bin/sh: line 1: gtk-config: command not found
roadmap_main.c:28:21: gtk/gtk.h: No such file or directory
roadmap_main.c:29:28: gdk/gdkkeysyms.h: No such file or directory
In file included from roadmap_main.c:35:
roadmap_gtkcanvas.h:33:21: gtk/gtk.h: No such file or directory
In file included from roadmap_main.c:35:
roadmap_gtkcanvas.h:38: error: parse error before '*' token
.
.  (a bunch more errors and warnings)
.
roadmap_main.c: At top level:
roadmap_main.c:49: error: storage size of `RoadMapMainPeriodicTimer' isn't knownmake[2]: *** [roadmap_main.o] Error 1
make[1]: *** [modules] Error 1
make: *** [install] Error 2

```

I get a similar error when I try to compile the source with 'make DESKTOP=GTK2'

I have libgtk2.0-0, libgtk2.0-bin, libgtk2.0-common, libgtk2.0-dev all at version 2.4.10-1ubuntu1.

I have libglib2.0-0, libglib2.0-data, libglib2.0-dev at version 2.4.7-0ubuntu2

flex version 2.5.31-26ubuntu1
bison version 1:1.875a-1.1

Does anyone know why it can't find gtk-config, even though I have all the gtk2 libraries?  Thanks for the help!

---

