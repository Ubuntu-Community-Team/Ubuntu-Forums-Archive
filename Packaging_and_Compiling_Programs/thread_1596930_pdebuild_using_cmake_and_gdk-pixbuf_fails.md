---
title: "pdebuild using cmake and gdk-pixbuf fails"
date: 2010-10-14
forum: Packaging and Compiling Programs
---

### Post by gusnan on 2010-10-14
Using pdebuild to build my package, which uses cmake, gtk and gdk-pixbuf I run into problems:

```
make[3]: Entering directory `/tmp/buildd/sciteproj-0.3.9/obj-x86_64-linux-gnu'
/usr/bin/cmake -E cmake_progress_report /tmp/buildd/sciteproj-0.3.9/obj-x86_64-linux-gnu/CMakeFiles 1
[  6%] Building C object CMakeFiles/sciteproj.dir/src/main.o
/usr/bin/cc   -g -O2 -g -Wall -O2 -I/tmp/buildd/sciteproj-0.3.9/include -I/usr/include/glib-2.0 -I/usr/lib64/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib64/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/atk-1.0   -fomit-frame-pointer -mms-bitfields -o CMakeFiles/sciteproj.dir/src/main.o   -c /tmp/buildd/sciteproj-0.3.9/src/main.c
In file included from /usr/include/gtk-2.0/gdk/gdkcairo.h:28,
                 from /usr/include/gtk-2.0/gdk/gdk.h:33,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from /tmp/buildd/sciteproj-0.3.9/src/gui.h:24,
                 from /tmp/buildd/sciteproj-0.3.9/src/main.c:22:
/usr/include/gtk-2.0/gdk/gdkpixbuf.h:37: fatal error: gdk-pixbuf/gdk-pixbuf.h: No such file or directory
compilation terminated.
make[3]: *** [CMakeFiles/sciteproj.dir/src/main.o] Error 1
make[3]: Leaving directory `/tmp/buildd/sciteproj-0.3.9/obj-x86_64-linux-gnu'
make[2]: *** [CMakeFiles/sciteproj.dir/all] Error 2

```How can I solve this? I have tried to make my project depend on libgdk-pixbuf2.0-dev, but to no avail.

Also, I have searched for cmake-modules for the gdk-pixbuf stuff, but no luck - 

So, how can this be solved? Is it just some small simple mistake? I have set build-depends to 
```
debhelper (>= 7), cmake, cdbs, libgtk2.0-dev, libglib2.0-dev
```Is that not enough?


[edit]
This should obviously be in the Packaging and Compiling Programs category - Could someone please move it?
[/edit]

---

### Post by gusnan on 2010-10-16
Solved it myself, Seems GTK packaging has changed on later Ubuntu versions. (I needed to add dependencies and change the build to include more GTK stuff.)

---

### Post by tobixen on 2010-10-19
How did you solve this problem?

I'm getting the same error when compiling the trunk version of gpsdrive.  Worked before upgrading to Maverick.

---

### Post by gusnan on 2010-10-21
I actually updated my CMakeLists.txt build system and added gthread-2.0 gobject-2.0 and glib-2.0 gdk_pixbuf-2.0 to my link flags, as well as 
 "/usr/include/gdk-pixbuf-2.0"

to the header search path - in addition to using the variables that the cmake GTK module should add. It isn't optimal at all, but it does work for me...

---

### Post by SevenMachines on 2010-10-21
You might want to think about using pkg-config, gtk dependencies especially are quite involved.
> $ pkg-config --cflags --libs gtk+-2.0
-pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12  -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpng12 -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0  

I believe cmake has a module that uses pkg-config which you might want to look into, should make life easier

---

### Post by gusnan on 2010-10-21
ah, thanks SevenMachines - pkg-config has slipped my mind - that seems very helpful!

Thanks!

---

