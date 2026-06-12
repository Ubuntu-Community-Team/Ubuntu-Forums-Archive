---
title: "Problem with 'make 3.81'."
date: 2013-04-22
forum: Programming Talk
---

### Post by akvino on 2013-04-22
What is wrong with this:

SHELL = /bin/sh
CC    = gcc
FLAGS        = -std=gnu99 -Iinclude
CFLAGS       = -fPIC -pedantic -Wall -Wextra -march=native -ggdb3
DEBUGFLAGS   = -O0 -D _DEBUG
RELEASEFLAGS = -O2 -D NDEBUG -combine -fwhole-program

TARGET  = bsm.so
SOURCES = $(shell echo src/*.c)
HEADERS = $(shell echo include/*.h)
OBJECTS = $(SOURCES:.c=.o)

PREFIX = $(DESTDIR)/usr/local
BINDIR = $(PREFIX)/bin

all: $(TARGET)

$(TARGET): $(OBJECTS) 
[there is TAB here]$(CC) $(FLAGS) $(CFLAGS) $(DEBUGFLAGS) -o $(TARGET) $(OBJECTS) 



ERROR:
BSM]$ make
Makefile:19: *** missing separator.  Stop

---

### Post by akvino on 2013-04-22
Eh my vim was not settings TAB properly had to do it in geany

---

### Post by schragge on 2013-04-22
Check that TAB is really a TAB. Try
```
cat -T Makefile
```
It should display tabs as **^I**

---

### Post by akvino on 2013-04-22
That is the best piece of advice I got this far. I was about to burst into flames editing makefile.

---

