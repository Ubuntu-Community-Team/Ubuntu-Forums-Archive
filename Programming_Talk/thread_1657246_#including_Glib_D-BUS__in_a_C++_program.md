---
title: "#including Glib D-BUS  in a C++ program"
date: 2011-01-01
forum: Programming Talk
---

### Post by Deepfriedice on 2011-01-01
I have been trying to write a download program in c++, and will need to use D-BUS to get it working. In order to figure out how to use D-BUS properly, I am trying to put together some small test programs.


The Problem:

Whenever I try to compile a program containing #include <dbus/dbus-glib.h> the compiler complains that it doesn't exist. When I checked out /usr/include/ by hand, the path to dbus-glib.h is actually /dbus-1.0/dbus/dbus-glib.h  .


So I change the path in the #include to <dbus-1.0/dbus/dbus-glib.h>:

Then the compiler claims that glib-object.h doesn't exist, despite that several of the header files in dbus need it (and several related files). The glib files are actually located in /usr/include/glib-2.0/  .


So I copy D-BUS library from /usr/include/dbus-1.0/dbus/ to /usr/include/dbus/  , change all the #includes in it from <glib-SOMETHING> to <glib2.0/glib-SOMETHING> and set the #include in my program back to <dbus-1.0/dbus/dbus-glib.h>:
 
Now it turns out /usr/include/glib-2.0/glib-object.h needs /usr/include/gobject/gbinding.h. *Which doesn't exist.*


At this point I'm almost ready to give up. Am I missing something important? or is my whole install screwed up?
Because I'm in danger of breaking this if go on any further without help.

---

### Post by MadCow108 on 2011-01-01
the folder structure of these headers requires you to set include paths for the compiler with -I
luckily libdbus-glib-1-dev provides a pkg-config file with this information.

so doing this will set up everything correctly:
g++ `pkg-config --cflags --libs dbus-glib-1` yourfile

pkg-config --cflags --libs dbus-glib-1 prints:
```

-pthread -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  -pthread -L/lib -ldbus-glib-1 -ldbus-1 -lpthread -lgobject-2.0 -lgthread-2.0 -lrt -lglib-2.0

```
so #include <dbus/dbus-glib.h> should now work

---

### Post by Deepfriedice on 2011-01-01
annnd... it compiles perfectly!

  	Thanks MadCow108, that really helped.

---

