---
title: "gstreamer and Makefile"
date: 2009-07-30
forum: Programming Talk
---

### Post by swappo1 on 2009-07-30
Hello,

I am getting a compiler error when running a program with gstreamer.
Makefile
```
PROG     = player
SRCS     = main.c

OBJS     = $(SRCS:.c=.o)
CFLAGS = -O2 -Wall -Werror -ansi `pkg-config gtk+-2.0 gstreamer-0.10 --cflags`
LDLIBS   = -lpthread `pkg-config gtk+-2.0 gstreamer-0.10 --libs`
INCLUDE  =
DEPFILE  = deps.mak

.PHONY: clean

$(PROG): $(OBJS)
		$(CC) $^ $(LDLIBS) -o $@

# How to make the object files:
.c.o:
		$(CC) $(CFLAGS) -c $<

deps:
		$(CC) -MM $(CCFLAGS) $(SRCS) > $(DEPFILE)

# Cleaning target (only works with fileutils):
clean:
		$(RM) $(OBJS) $(PROG)

-include $(DEPFILE)
```
Error
```
cc -O2 -Wall -Werror -ansi `pkg-config gtk+-2.0 gstreamer-0.10 --cflags` -c main.c
Package gstreamer-0.10 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gstreamer-0.10.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gstreamer-0.10' found

```
How do I add gstreamer-0.10 to the PKG_CONFIG_PATH environment variable?

---

### Post by Zugzwang on 2009-07-30
So you have the package "libgstreamer0.10-dev" installed?

---

### Post by swappo1 on 2009-07-30
I have gstreamer installed.  If libgstreamer0.10-dev is part of that package then yes, it is installed.

---

### Post by Zugzwang on 2009-07-30
> **swappo1 said:**
> I have gstreamer installed.  If libgstreamer0.10-dev is part of that package then yes, it is installed.

In Ubuntu, if you want to *compile* things, you also need to have to install the "-dev" packages *separately".

---

### Post by swappo1 on 2009-07-30
Ok, I installed the -dev packages and it compiles.  Thanks.

---

