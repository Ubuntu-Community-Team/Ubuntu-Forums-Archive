---
title: "Compiling simple c++ gtk code (can't do it) :'("
date: 2010-04-27
forum: Packaging and Compiling Programs
---

### Post by tjw09003 on 2010-04-27
```

#include <gtk/gtk.h>

int main(int argc, char *argv[])
{
    GtkWidget *window;

    gtk_init(&argc, &argv);

    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);
    gtk_widget_show(window);

    gtk_main();

    return 0;
}

```Very simple program just a window but I can't compile it. The error message from gcc is 610 lines long lol

Here's a short 36 line sample of the errors. 

> 
In file included from /usr/include/gdk/gdk.h:32,
                 from /usr/include/gtk/gtk.h:32,
                 from gtkHelloWorld.cpp:1:
/usr/include/gdk/gdkapplaunchcontext.h:30:21: error: gio/gio.h: No such file or directory
In file included from /usr/include/gdk/gdkapplaunchcontext.h:31,
                 from /usr/include/gdk/gdk.h:32,
                 from /usr/include/gtk/gtk.h:32,
                 from gtkHelloWorld.cpp:1:
/usr/include/gdk/gdkscreen.h:31:19: error: cairo.h: No such file or directory
In file included from /usr/include/gdk/gdkscreen.h:32,
                 from /usr/include/gdk/gdkapplaunchcontext.h:31,
                 from /usr/include/gdk/gdk.h:32,
                 from /usr/include/gtk/gtk.h:32,
                 from gtkHelloWorld.cpp:1:
/usr/include/gdk/gdktypes.h:36:18: error: glib.h: No such file or directory
/usr/include/gdk/gdktypes.h:37:25: error: pango/pango.h: No such file or directory
/usr/include/gdk/gdktypes.h:38:25: error: glib-object.h: No such file or directory
/usr/include/gdk/gdktypes.h:55:23: error: gdkconfig.h: No such file or directory
In file included from /usr/include/gdk-pixbuf/gdk-pixbuf.h:39,
                 from /usr/include/gdk/gdkpixbuf.h:37,
                 from /usr/include/gdk/gdkcairo.h:28,
                 from /usr/include/gdk/gdk.h:33,
                 from /usr/include/gtk/gtk.h:32,
                 from gtkHelloWorld.cpp:1:
/usr/include/gdk-pixbuf/gdk-pixbuf-io.h:38:21: error: gmodule.h: No such file or directory
In file included from /usr/include/gdk/gdk.h:33,
                 from /usr/include/gtk/gtk.h:32,
                 from gtkHelloWorld.cpp:1:
/usr/include/gdk/gdkcairo.h:29:30: error: pango/pangocairo.h: No such file or directory
In file included from /usr/include/gtk/gtkcontainer.h:35,
                 from /usr/include/gtk/gtkbin.h:35,
                 from /usr/include/gtk/gtkwindow.h:36,
                 from /usr/include/gtk/gtkdialog.h:35,
                 from /usr/include/gtk/gtkaboutdialog.h:32,
                 from /usr/include/gtk/gtk.h:33,
                 from gtkHelloWorld.cpp:1:
Obvioulsy gcc can't find the needed include files, but all of these files are in the /usr/include directory except they are in the wrong folders.

For Example:
GTK include files aren't in /usr/include/gtk/gtk.h
but they are in /usr/include/gtk-2.0/gtk/gtk.h

cairo.h isn't in /usr/include/cairo.h 
but it's in /usr/include/cairo/cairo.h

pango.h isn't in /usr/include/pango/pango.h
but it's in /usr/include/pango-1.0/pango/pango.h

Do you see my problem? Why are the include files placed like this? Should I move all of them?

---

### Post by SevenMachines on 2010-04-27
Dont move system installed headers! The headers, libraries need to be added to the gcc command line. Luckilly a lot of -dev packages deal with this using pkg-config to generate all the right options (usually the more complicated ones especially do this). For the simple example above add 
`pkg-config --cflags --libs gtk+-2.0`
to the command line (note these are backquote ` characters and not single quotes ' )

So a simple example might be
$ gcc  `pkg-config --cflags --libs gtk+-2.0` -o test test.c 

if you run the pkg-config command manually you'll see whats actually added to the command line

$ pkg-config --cflags --libs gtk+-2.0
-D_REENTRANT -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lcairo -lgio-2.0 -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0 

So you can see why pkg-config is a time saver :)

---

### Post by SevenMachines on 2010-04-27
Just an additional note, all the currently installed pkg-config files are in /usr/lib/pkgconfig/ for reference.
To use any of them you just need to drop the extension from the filename so, for example,

$ ls /usr/lib/pkgconfig/ | grep -i ogre
CEGUI-OGRE.pc
OGRE.pc
$ pkg-config --cflags --libs OGRE
-DOGRE_GUI_GLX -DOGRE_CONFIG_LITTLE_ENDIAN -I/usr/include/OGRE  -lOgreMain

---

### Post by SevenMachines on 2010-04-27
hmm, seems there are a handful in /usr/share/pkgconfig/
too :)

---

### Post by tjw09003 on 2010-04-27
Thanks!! that trimmed the 610 errors to 1 error :D

Do you know what this error means?

/tmp/ccH4dwJY.o:(.eh_frame+0x12): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

---

### Post by SevenMachines on 2010-04-27
sorry, i missed you were actually using c++ and not c! Thats the error you get when you try to compile a .cpp file with gcc. Simply change gcc to g++

---

### Post by tjw09003 on 2010-04-27
*facepalm*
wow, I feel like an idiot lol

Thanks, it compiled :D

---

### Post by SevenMachines on 2010-04-27
its not the most informative error message in the world :)

---

### Post by Compyx on 2010-04-27
If you intend to use C++ with GTK+, wouldn't it be more logical to use the C++ bindings to GTK+? Have a look here: [http://www.gtkmm.org/]("http://www.gtkmm.org/").

Gtk+ attempts to provide an object-oriented interface, for which C isn't exactly perfectly suited. C++ on the other hand, with all its OO-features, is a good fit for the OO-nature of many GUI toolkits, so I'd suggest using gtkmm, rather than the C-bindings.

Of course I don't know your requirements, perhaps you have a good reason to use the C-bindings to GTK+ in a C++ program.

HTH

---

