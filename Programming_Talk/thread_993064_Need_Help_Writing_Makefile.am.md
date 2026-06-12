---
title: "Need Help Writing Makefile.am"
date: 2008-11-25
forum: Programming Talk
---

### Post by aaaantoine on 2008-11-25
I'm trying to GNUify a package that I want to distribute.

Because I can't figure out Makefiles, I write a quick bash file that does the compiling for me.  So I tried to read over the documentation for Automake... And I find it rather confusing.

So, how do I convert this...
```
#!/bin/bash

gcc $(pkg-config --cflags --libs libpanelapplet-2.0 libwnck-1.0) -o taskdock-applet taskdock.c
sudo cp taskdock-applet /usr/lib/gnome-panel
sudo cp TaskdockApplet_Factory.server /usr/lib/bonobo/servers

```...into a Makefile.am?

Note: After pkg-config is run, the data expands to...
```
#!/bin/bash

gcc -DORBIT2=1 -pthread -I/usr/include/panel-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/include/libwnck-1.0 -I/usr/include/startup-notification-1.0  -pthread -lpanel-applet-2 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomevfs-2 -lgconf-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lbonobo-2 -lbonobo-activation -lORBit-2 -lgthread-2.0 -lrt -lwnck-1 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lgio-2.0 -lcairo -lpango-1.0 -lfreetype -lz -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lglib-2.0 -o taskdock-applet taskdock.c
sudo cp taskdock-applet /usr/lib/gnome-panel
sudo cp TaskdockApplet_Factory.server /usr/lib/bonobo/servers

```
I figured out that the -I fields get attached to an INCLUDES variable, like so:
```
INCLUDES = -I/usr/include/panel-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/gail-1.0 -I/usr/include/libwnck-1.0 -I/usr/include/startup-notification-1.0
```

But the rest I don't know about.

---

### Post by dwhitney67 on 2008-11-25
I also do not know anything about AutoMake.  Makefiles on the other hand, are easy to put together.

Here's a Makefile that should work, but since I do not have the packages libpanelappley-2.0 nor libwnck-1.0 on my system, I could not test it.

Be careful if you copy/paste the example below.  Tab-spaces need to be preserved.

```

APPNAME  = taskdock-applet
SERVER   = TaskdockApplet_Factor.server

SRCS     = taskdock.c
DEST1    = /usr/lib/gnome-panel
DEST2    = /usr/lib/bonobo/servers

CFLAGS   = -Wall -pedantic `pkg-config --cflags libpanelapplet-2.0 libwnck-1.0`
LIBS     = `pkg-config --libs libpanelapplet-2.0 libwnck-1.0`

OBJS     = $(SRCS:.c=.o)
DEP_FILE = .depend

.PHONY: all clean distclean


all: depend $(APPNAME)

install: all
        @echo Installing $(APPNAME) and $(SERVER)
        @install -m 755 $(APPNAME) $(DEST1)
        @install -m 755 $(SERVER) $(DEST2)

$(APPNAME): $(OBJS)
        @echo Linking $@
        @$(CC) $^ $(LIBS) -o $@

.c.o:
        @echo Compiling $<
        @$(CC) $(CFLAGS) -c $< -o $@

clean:
        $(RM) $(OBJS)
        $(RM) $(APPNAME)
        $(RM) $(DEP_FILE)

distclean: clean
        $(RM) $(DEST1)/$(APPNAME)
        $(RM) $(DEST2)/$(SERVER)

depend: $(DEP_FILE)
        @touch $(DEP_FILE)

$(DEP_FILE):
        @echo Building dependencies in: $@
        @$(CC) -E -MM $(CFLAGS) $(SRCS) >> $(DEP_FILE)

ifeq (,$(findstring clean,$(MAKECMDGOALS)))
ifeq (,$(findstring distclean,$(MAKECMDGOALS)))
-include $(DEP_FILE)
endif
endif

```

---

### Post by Luggy on 2008-11-25
If you are having trouble figuring out makefiles, or if you just wish there was a simpler way I would recommend trying out [CMake]("http://www.cmake.org/").

It's a makefile generation tool, similar to QMake (which is packaged with QT) that gives you the strength of using makefiles without any of the headache.

I believe that CMake is in the repos.

---

### Post by aaaantoine on 2008-11-25
Thanks, dwhitney67.  It seems to be working fine.  Hopefully I should be able to learn from this file as well.

Also, thanks Luggy.  I'll check out CMake when I get a chance.

---

### Post by monkeyking on 2009-01-03
This thread might be outdated, 
I've spend a big part of my day trying to figure out how autoconf automake works. So anyone listening in might not waste half a day like i did

Most of the documentation on the web is very outdated,
and this is quite a problem since the innerworkings of autotool apparantly change overnight.

So if you want the program to crosscompile with auto* this is how you should do it.

Basicly you only need to create 3 files plus a README.

Make a small file called README, make a subdir in this folder,
copy your source files to this folder.
Have a Makefile.am in both the src and the ../src

The Makefile.am in src should look like
[PHP]
bin_PROGRAMS = taskdock-applet
taskdock-applet_SOURCES = taskdock.c
[/PHP]

The Makefile in ../src should look like
[PHP]
SUBDIRS = src
dist_doc_DATA = README
[/PHP]

The last one is configure.ac, this can be autogenerated with autoscan, but don't bother.

This configure.ac in your ../src should look like

```

AC_INIT([taskdock-applet], [0.3], [contact@gnu.org])
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
AC_PROG_CC
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES([
           Makefile
           src/Makefile
          ])
AC_OUTPUT

AC_CHECK_LIB(libpanelapplet-2.0 libwnck-1.0,,echo "ERROR: Required library pcre++ not found" && exit)

```

thats it now you generate all the needed files with 
autoreconf --install

the --install flag tells the program to make default files of the files that are needed.

now you can run 
./configure
make
make install

If you want to change the install dir you can use 

./configure --prefix

or for a complete list check
./configure --help

---

