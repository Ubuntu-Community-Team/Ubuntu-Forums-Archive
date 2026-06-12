---
title: "Compiling GTK+ projects in Eclipse"
date: 2009-02-26
forum: Programming Talk
---

### Post by cph05a on 2009-02-26
I've been very happy with the eclipse IDE in java, and I've just started using it for my c/c++ projects, but I can't figure out how to change the build settings to compile a gtk+ project. 

Does anyone have any experience compiling gtk+ projects in the eclipse CDT?

---

### Post by cabalas on 2009-02-26
I'm assuming here that you are using a makefile for compiling you code (at least that was they 'preferred' way when I was using the CDT in eclipse admittedly that was a couple of years ago). Here is the generic makefile I use for simple projects, I have modified it so that it includes and links to all the gtk stuff.

```

# Compiler Information
CC := gcc -c
LINK := gcc -o

CFLAGS := $(shell pkg-config --cflags gtk+-2.0)
LIBS := $(shell pkg-config --libs gtk+-2.0)

# Project info
APP_NAME := app_name
OBJ := $(patsubst %.c, %.o, $(wildcard *.c))


# Makefile stuff
.PHONEY: all clean

all:
	$(MAKE) $(APP_NAME)

clean:
	rm -f $(APP_NAME) *.o

$(APP_NAME): $(OBJ)
	$(LINK) $(APP_NAME) $(OBJ) $(LIBS)

# Compile all the .c files
%.o: %.c
	$(CC) $< $(CFLAGS)

```

Hopefully replacing your existing makefile with this one and setting APP_NAME to something appropriate works for you.

---

### Post by cph05a on 2009-02-26
Thanks! it works now :)

---

