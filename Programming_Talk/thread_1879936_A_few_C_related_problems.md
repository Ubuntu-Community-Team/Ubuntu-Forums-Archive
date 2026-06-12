---
title: "A few C related problems"
date: 2011-11-12
forum: Programming Talk
---

### Post by Liiiim on 2011-11-12
I've posted about it here before, but now that I actually have some time to work on it I'm coming up with more questions.  My main objective is to create a GUI for a program which will run in Windows.

First - I have the GUI up and running in Linux, using GTK2.  Compiling the program for Windows is a major pain though.  Following [this]("http://ricardo.ecn.wfu.edu/%7Ecottrell/cross-gtk/") guide, I'm running into a problem building the cross-compiler - I get the error

```
../../gcc-4.6.1-1-mingw32-src/gcc-4.6.1/libgcc/../gcc/tsystem.h:87:19: fatal error: stdio.h: No such file or directory
```after a few minutes of compilation.  I have no idea what is causing this error or how to get around it.

So instead of following that guide exactly, I thought I would try installing mingw32 and the necessary glib/Gtk components from the Arch User Repos (I'm doing this all on Arch).  I installed mingw32-glib2, mingw32-gtk2, etc. and tried compiling with 

```
i486-mingw32-gcc -o ./windows/sim -Wall `pkg-config-script --cflags --libs gtk+-2.0` main.c ui.c screen.c parsefile.c machine.c
```where pkg-config-script is this:

```
#! /bin/sh

PKG_CONFIG_LIBDIR=/usr/i486-mingw32/lib/pkgconfig \
PKG_CONFIG_PATH=/usr/i486-mingw32/lib/pkgconfig pkg-config $*
```Running pkg-config-script --cflags --libs gtk+-2.0 gives ```
-mms-bitfields -I/usr/i486-mingw32/include/gtk-2.0 -I/usr/i486-mingw32/lib/gtk-2.0/include -I/usr/i486-mingw32/include/atk-1.0 -I/usr/i486-mingw32/include/cairo -I/usr/i486-mingw32/include/gdk-pixbuf-2.0 -I/usr/i486-mingw32/include/pango-1.0 -I/usr/i486-mingw32/include/glib-2.0 -I/usr/i486-mingw32/lib/glib-2.0/include -I/usr/i486-mingw32/include/pixman-1 -I/usr/i486-mingw32/include -I/usr/i486-mingw32/include/freetype2 -I/usr/i486-mingw32/include/libpng15  -Wl,-luuid -L/usr/i486-mingw32/lib -lgtk-win32-2.0 -lgdk-win32-2.0 -limm32 -lshell32 -lole32 -latk-1.0 -lpangocairo-1.0 -lgio-2.0 -lgdk_pixbuf-2.0 -lpangoft2-1.0 -lpangowin32-1.0 -lgdi32 -lfreetype -lfontconfig -lpango-1.0 -lm -lcairo -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lglib-2.0 -lintl
```Compiling however gives a bunch of undefined references to glib/gtk stuff.  I'm pretty clueless when it comes to compiling programs like this, so does anyone see a problem with my setup?  I imagine it's something to do with the output of pkg-config-script and the linker not being able to find the mingw32-gtk libraries, but I'm not sure.

So if anyone has any advice, it would be much appreciated.  I feel I've hit a wall with this project :???:

e: Alternatively, how much work would it be to totally redo the GUI with something other than GTK?  I've heard QT is good, would that be easier to compile for Windows?  My only problem with QT is it's C++, and not plain C so I'm worried it would be a fairly significant amount of work to learn and convert my code to C++.

---

### Post by Arndt on 2011-11-12
> **Liiiim said:**
> I've posted about it here before, but now that I actually have some time to work on it I'm coming up with more questions.  My main objective is to create a GUI for a program which will run in Windows.

First - I have the GUI up and running in Linux, using GTK2.  Compiling the program for Windows is a major pain though.  Following [this]("http://ricardo.ecn.wfu.edu/%7Ecottrell/cross-gtk/") guide, I'm running into a problem building the cross-compiler - I get the error

```
../../gcc-4.6.1-1-mingw32-src/gcc-4.6.1/libgcc/../gcc/tsystem.h:87:19: fatal error: stdio.h: No such file or directory
```after a few minutes of compilation.  I have no idea what is causing this error or how to get around it.

So instead of following that guide exactly, I thought I would try installing mingw32 and the necessary glib/Gtk components from the Arch User Repos (I'm doing this all on Arch).  I installed mingw32-glib2, mingw32-gtk2, etc. and tried compiling with 

```
i486-mingw32-gcc -o ./windows/sim -Wall `pkg-config-script --cflags --libs gtk+-2.0` main.c ui.c screen.c parsefile.c machine.c
```where pkg-config-script is this:

```
#! /bin/sh

PKG_CONFIG_LIBDIR=/usr/i486-mingw32/lib/pkgconfig \
PKG_CONFIG_PATH=/usr/i486-mingw32/lib/pkgconfig pkg-config $*
```Running pkg-config-script --cflags --libs gtk+-2.0 gives ```
-mms-bitfields -I/usr/i486-mingw32/include/gtk-2.0 -I/usr/i486-mingw32/lib/gtk-2.0/include -I/usr/i486-mingw32/include/atk-1.0 -I/usr/i486-mingw32/include/cairo -I/usr/i486-mingw32/include/gdk-pixbuf-2.0 -I/usr/i486-mingw32/include/pango-1.0 -I/usr/i486-mingw32/include/glib-2.0 -I/usr/i486-mingw32/lib/glib-2.0/include -I/usr/i486-mingw32/include/pixman-1 -I/usr/i486-mingw32/include -I/usr/i486-mingw32/include/freetype2 -I/usr/i486-mingw32/include/libpng15  -Wl,-luuid -L/usr/i486-mingw32/lib -lgtk-win32-2.0 -lgdk-win32-2.0 -limm32 -lshell32 -lole32 -latk-1.0 -lpangocairo-1.0 -lgio-2.0 -lgdk_pixbuf-2.0 -lpangoft2-1.0 -lpangowin32-1.0 -lgdi32 -lfreetype -lfontconfig -lpango-1.0 -lm -lcairo -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lglib-2.0 -lintl
```Compiling however gives a bunch of undefined references to glib/gtk stuff.  I'm pretty clueless when it comes to compiling programs like this, so does anyone see a problem with my setup?  I imagine it's something to do with the output of pkg-config-script and the linker not being able to find the mingw32-gtk libraries, but I'm not sure.

So if anyone has any advice, it would be much appreciated.  I feel I've hit a wall with this project :???:

e: Alternatively, how much work would it be to totally redo the GUI with something other than GTK?  I've heard QT is good, would that be easier to compile for Windows?  My only problem with QT is it's C++, and not plain C so I'm worried it would be a fairly significant amount of work to learn and convert my code to C++.

For other than very small programs, the compiling and linking phases are usually kept separate, which makes me wonder if the command

```
pkg-config-script --cflags --libs
```

can be used the way you do. I suggest compiling first (make .o files out of the .c files), using pkg-config-script --cflags, and then linking (making an executable out of the .o files), using pkg-config-script --libs.

---

### Post by Liiiim on 2011-11-12
Awesome, compiling and linking separately worked like a charm.

I have my program, with the GUI, running in Windows now.  It's nice, but does anyone have any experience creating GUIs with the native Windows API?  Is it difficult?  Is there an easy editor for it like Glade?  Because with all the Glib/Gtk DLLs, my 56 KB program ends up being 13 MB.

---

### Post by xytron on 2011-11-12
I recommend using[ FLTK ]("http://www.fltk.org")instead.  It's small and it can be linked statically because your executables don't get big.
 
Even though FLTK may not have as many fancy widgets and controls, for the most part it's complete enough.
 
Using FLTK with Visual Studio has been very easy and you can compile the same exact code on Linux often without any modifications at all, or the just very minor ones.
 
Overall I'm satisfied with FLTK for now.  It is C++ but I would say C++ is much preferable in most cases to using C.

---

### Post by Liiiim on 2011-11-12
Thanks, but that seems like it would be a bit much work to switch over to that - it looks like I would have to totally redo the UI, "by hand" without an editor.  I think if I were going to that I might as well just make a version with the native Windows API.

---

