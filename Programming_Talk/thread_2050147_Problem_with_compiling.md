---
title: "Problem with compiling"
date: 2012-08-30
forum: Programming Talk
---

### Post by ymag on 2012-08-30
Hello,

I have a C++ program that was working on 10.04 version of Ubuntu. I upgraded to 12.04 and it's not compiling anymore and I get a bunch of errors looking like :

[SIZE=2]undefined reference to `_gfortran..*[/SIZE]

the makefile is :

OBJDIR = $(GARFIELD_HOME)/Object
SRCDIR = $(GARFIELD_HOME)/Source
INCDIR = $(GARFIELD_HOME)/Include
HEEDDIR = $(GARFIELD_HOME)/Heed
LIBDIR = $(GARFIELD_HOME)/Library

# Compiler flags
CFLAGS = -Wall -Wextra -Wno-long-long \
    `root-config --cflags` \
    -O3 -fno-common -c \
    -I$(INCDIR) -I$(HEEDDIR)

# Debug flags
#CFLAGS += -g

LDFLAGS = `root-config --glibs` -lGeom -lm -lgfortran
LDFLAGS += -L$(LIBDIR) -lGarfield

#LDFLAGS += -g

msgc: msgc.C 
    $(CXX) $(CFLAGS) msgc.C
    $(CXX) -o msgc msgc.o $(LDFLAGS)
    rm msgc.o


Maybe I have a problem with gfortran libraries or with the underscore prefix.
Any suggestion?

Thank you.

---

### Post by muteXe on 2012-08-30
[http://qt-project.org/forums/viewthread/19805](http://qt-project.org/forums/viewthread/19805)

any use?

---

