---
title: "Help setting up gtk+ on Ubuntu 12.04"
date: 2013-04-29
forum: Packaging and Compiling Programs
---

### Post by captaincactuz on 2013-04-29
Hello, I am relatively inexperienced with ubuntu and I am trying to compile a simple gtk app in Ubuntu 12.04. I believe I have gtk installed because when I type:

$ dpkg -l libgtk[0-9]* | grep ^i
ii  libgtk2-perl                                                2:1.223-1build3                         Perl interface to the 2.x series of the Gimp Toolkit library
ii  libgtk2.0-0                                                 2.24.10-0ubuntu6                        GTK+ graphical user interface library
ii  libgtk2.0-bin                                               2.24.10-0ubuntu6                        programs for the GTK+ graphical user interface library
ii  libgtk2.0-cil                                               2.12.10-2ubuntu4                        CLI binding for the GTK+ toolkit 2.12
ii  libgtk2.0-common                                            2.24.10-0ubuntu6                        common files for the GTK+ graphical user interface library

Yet when I try to compile: 

$ gcc main.c
main.c:2:21: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.

I was wondering if someone could give me a comprehensive description of how to set up GTK or if I have to update my PATH, etc. And if possible, anything else I need to do to be able to compile and run GTK in code::blocks. As I said I am fairly inexperienced with linux.

:confused:Thank you! :confused:

---

### Post by steeldriver on 2013-04-29
To build gtk apps (as opposed to just running them) you will likely need the corresponding -dev package e.g. for gtk2.0 it's libgtk2.0-dev

```
sudo apt-get install libgtk2.0-dev
```

Then you would probably want to use pkg-config to expand the required include paths and libs on the gcc command line - something like

```
gcc `pkg-config --cflags gtk+-2.0` -o *yourprog yourprog*.c `pkg-config --libs gtk+-2.0`
```

---

### Post by captaincactuz on 2013-05-01
Thank you, that worked. Is there any way to permanently update the path so I do not have to type all of that every time?

---

### Post by steeldriver on 2013-05-01
Probably the best way in the long run is to put together a little Makefile - it can grow with you as your projects get more complicated - I am *NOT* a Makefile expert but something like

```

MYAPP = gtkhello

SRCS = gtkhello.c

OBJS = $(SRCS:.c=.o)

CFLAGS := -Wall 
CFLAGS += $(shell pkg-config --cflags gtk+-2.0)

LDFLAGS :=
LIBS := 
LIBS += $(shell pkg-config --libs gtk+-2.0)

.PHONY = all clean

all : $(MYAPP)

$(MYAPP) : $(OBJS)
    $(CC) $^ $(LDFLAGS) $(LIBS) -o $@

clean :
    $(RM) $(OBJS) $(MYAPP)

```

Then you can just type 'make'

---

### Post by captaincactuz on 2013-05-01
haha that's a little over my head, but thanks for your help

---

