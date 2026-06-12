---
title: "Anjuta can't find any header files"
date: 2007-02-27
forum: Programming Talk
---

### Post by idn on 2007-02-27
Hi, I am trying out anjuta for the first time but I am having trouble getting it to find some of the libraries I want to use. I want to use dbus, I have install dbus-dev and all the build-essential and gnome development packages as I can compile applications fine outside of anjuta

The trouble is everytime I try to compile my project I get 

```

make main.o
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -DPACKAGE_SRC_DIR=\""."\" -DPACKAGE_DATA_DIR=\""/usr/local/share"\"    -Wall -g -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c
/home/idn/Projects/gtask/src/main.c:26:25: error: "dbus/dbus.h": No such file or directory
/home/idn/Projects/gtask/src/main.c:27:37: error: dbus/dbus-glib-bindings.h: No such file or directory
make: *** [main.o] Error 1
Completed... unsuccessful
Total time taken: 0 secs

```

The include statement looks like
 
```

#include "dbus/dbus-glib.h"
#include <dbus/dbus-glib-bindings.h>

```

When I type in a terminal

```

idn@idn-laptop:~$ locate dbus-glib.h
/usr/include/dbus-1.0/dbus/dbus-glib.h

```

So the header file is there, I guess anjuta doesnt know about it or something, any ideas?

---

### Post by jpeddicord on 2007-02-27
Change the quotes in the first include statement to <> and it should solve at least one error, if not all. :)

---

### Post by idn on 2007-02-27
> **jacobmp92 said:**
> Change the quotes in the first include statement to <> and it should solve at least one error, if not all. :)

No I'm affraid it didn't :), it still says it cant find the directory. Could it be anything else maybe?

---

### Post by j_g on 2007-02-27
What happens if you just use:

#include <dbus-glib.h>
#include <dbus-glib-bindings.h>

---

### Post by idn on 2007-02-27
> **j_g said:**
> What happens if you just use:

#include <dbus-glib.h>
#include <dbus-glib-bindings.h>

```

make main.o
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DPACKAGE_LOCALE_DIR=\""/usr/local/share/locale"\" -DPACKAGE_SRC_DIR=\""."\" -DPACKAGE_DATA_DIR=\""/usr/local/share"\"    -Wall -g -g -O2 -MT main.o -MD -MP -MF ".deps/main.Tpo" -c -o main.o main.c
/home/idn/Projects/gtask/src/main.c:26:23: error: dbus-glib.h: No such file or directory
/home/idn/Projects/gtask/src/main.c:27:32: error: dbus-glib-bindings.h: No such file or directory
make: *** [main.o] Error 1
Completed... unsuccessful
Total time taken: 0 secs

```

No luck im afraid :( Other things dont seem to work like 
```

#include <gnome.h>

```

Either :(

---

### Post by lnostdal on 2007-02-27
always use pkg-config for this stuff when you can; it will always work and be portable

```

lars@ibmr52:~/programming/lisp$ pkg-config --list-all|grep dbus
ndesk-dbus-glib-1.0   NDesk.DBus.GLib - GLib integration for NDesk.DBus, the D-Bus IPC library
dbus-glib-1           dbus-glib - GLib integration for the free desktop message bus
ndesk-dbus-1.0        NDesk.DBus - Managed D-Bus IPC protocol library and CLR binding
dbus-sharp            DBus - DBus
dbus-python           dbus-python - Python bindings for D-Bus
dbus-1                dbus - Free desktop message bus

lars@ibmr52:~/programming/lisp$ pkg-config --cflags dbus-glib-1
-I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  

lars@ibmr52:~/programming/lisp$ pkg-config --libs dbus-glib-1
-ldbus-glib-1 -ldbus-1 -lgobject-2.0 -lglib-2.0  

```

as you can see it spits out the correct compiler and linker arguments ..

your IDE should be able to handle this if you enter `pkg-config --cflags dbus-glib-1` with backquotes (edit: well, not really sure how this would work with anjuta) as shown for compiler and linker arguments

here's how i do this stuff from a different setup/ide/environment: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/)

---

### Post by runningwithscissors on 2007-02-28
I agree with the suggestion to use pkg-config.

Or, you could simply include **/usr/include/dbus-1.0** in your includes path. I don't know how that is done in Ajunta. But from the command line, you simply add a **-I/usr/include/dbus-1.0** to your compile command.

---

### Post by kanem on 2007-02-28
Anjuta has a GUI dialog for telling it what libraries you want to use. I'm not in front of my computer right now, so I can't say exactly where they are. I'll post later with the info.

Edit: well, I haven't used this thing since they went to 2.0. A lot has changed. I installed it and tried to find where you specify libraries, but had no luck. Sorry.

---

