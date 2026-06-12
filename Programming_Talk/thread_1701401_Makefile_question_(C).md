---
title: "Makefile question (C)"
date: 2011-03-06
forum: Programming Talk
---

### Post by stefanmi on 2011-03-06
Hello i am making a project and i have the following tree :

projectRoot/

projectRoot/src/
projectRoot/include/
projectRoot/Makefile----------------------(Here is my problem)

projectRoot/src/algo/
projectRoot/src/services/
projectRoot/src/testVoyageurCommerce.c


projectRoot/src/algo/voyageurGlouton.c
projectRoot/src/algo/voyageurRecursif.c
projectRoot/src/algo/voyageurPSE.c

projectRoot/src/services/matrices.c
projectRoot/src/services/chemins.c

projectRoot/include/matrices.h
projectRoot/include/chemins.h
projectRoot/include/voyageurGlouton.h
projectRoot/include/voyageurPSE.h
projectRoot/include/voyageurRecursif.h


I would like my makefile located in "projectRoot/" to compile the whole program with all the .c files located in the sub-directories.
I don't know how to tell my makefile to go search the other .c files in these directories . If u could help me please ;)

Thanks.

---

### Post by stefanmi on 2011-03-07
I need that completed for tomorrow 14pm :( , so if u could please help me to finish my makefile ? Thanks.

here is my makefile :

> CC=gcc
CFLAGS = -g -Wall -Werror -std=c99
LDFLAGS = -lm -I$(LIBDIR)-lservices

SRCDIR = ./src/
INCDIR = ./include/
LIBDIR = ./lib/
BINDIR = ./bin/

OUTFILE = testVoyageurCommerce


SOURCES = $(SRCDIR)algo/voyageurPSE.c $(SRCDIR)algo/voyageurRecursif.c $(SRCDIR)algo/voyageurGlouton.c $(SRCDIR)testVoyageurCommerce.c

OBJS= $(SOURCES:.c=.o)

all: $(OUTFILE) 
testVoyageurCommerce: $(SRCDIR)testVoyageurCommerce.o
	$(CC) $(SRCDIR)testVoyageurCommerce.o $(LDFLAGS) -o testVoyageurCommerce

$(OUTFILE): $(OBJS)

voyageurPSE.o : $(SRCDIR)algo/voyageurPSE.c $(INCDIR)voyageurPSE.h
voyageurRecursif.o :$(SRCDIR)algo/voyageurRecursif.c $(INCDIR)voyageurRecursif.h
voyageurGlouton.o : $(SRCDIR)algo/voyageurGlouton.c $(INCDIR)voyageurGlouton.h
testVoyageurCommerce.o : $(SRCDIR)testVoyageurCommerce.c


clean:
	rm -f $(OBJS) $(OUTFILE) *.out  core
mrproper:
	rm *~ 




it doesn't find the .h files..

("undefined reference to [function]")

---

### Post by Milliways on 2011-03-08
The problem is probably in how you reference the .h files in the .c programs.

---

### Post by dwhitney67 on 2011-03-08
> **stefanmi said:**
> I need that completed for tomorrow 14pm :( , so if u could please help me to finish my makefile ? Thanks.

Are you attempting to build a library, and then link it with your application?  Or do you want to compile all of your modules, and then in turn, link all of these to form the executable?

If you want to merely build all of your code to form an executable, something like this might work:
```

APP      = testVoyageurCommerce

OBJDIR   = .srcobjs

SRCS    := $(shell find . -name '*.c')
SRCDIRS := $(shell find . -name '*.c' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.c,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.c,$(OBJDIR)/%.d,$(SRCS))

DEBUG    = -g
INCLUDES = -I./Include
CFLAGS   = $(DEBUG) -Wall -Werror -pedantic -std=c99 $(INCLUDES) -c
LDFLAGS  = -lm

DEPENDS  = -MT $@ -MD -MP -MF $(subst .o,.d,$@)

SHELL    = /bin/bash

.PHONY: all clean distclean


all: buildrepo $(APP)

$(APP): $(OBJS)
        $(CC) $^ $(LDFLAGS) -o $@

$(OBJDIR)/%.o: %.c
        $(CC) $(CFLAGS) $(DEPENDS) $< -o $@

clean:
        $(RM) -r $(OBJDIR)

distclean: clean
        $(RM) $(APP)

buildrepo:
        @$(call make-repo)

define make-repo
   for dir in $(SRCDIRS); \
   do \
        mkdir -p $(OBJDIR)/$$dir; \
   done
endef

ifneq "$(MAKECMDGOALS)" "distclean"
ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif
endif

```

---

### Post by Milliways on 2011-03-08
> **dwhitney67 said:**
> 
```

INCLUDES = -I./Include
CFLAGS   = $(DEBUG) -Wall -Werror -pedantic -std=c99 $(INCLUDES) -c

```

A question.

When I type gcc --help it does not list the -I flag

Most of my programing has been done in Visual Studio, and I would expect such a flag to exist in a compiler, but I didn't see an equivalent in gcc

---

### Post by dwhitney67 on 2011-03-08
> **Milliways said:**
> A question.

When I type gcc --help it does not list the -I flag


Peruse the *man-page* for gcc.

```

man gcc

```

---

