---
title: "Makefile issues."
date: 2010-05-03
forum: Programming Talk
---

### Post by tw11 on 2010-05-03
This isn't really an urgent issue but I'm trying to learn to make better Makefiles and I've run into an issue and I have no idea why it's happening. I have the following makefile:

```

CC = gcc
CFLAGS = -Wall -g -std=gnu99 -lpthread

.PHONY: all clean

all: tests

tests: timerQueue.o test1.c test2.c
    $(CC) $(CFLAGS) -o test1 test1.c timerQueue.o
    $(CC) $(CFLAGS) -o test2 test2.c timerQueue.o

test1: tests
    echo "Running test 1...\nEnd with ctrl-c"
    ./test1

timerQueue.o: timerQueue.c timerQueue.h
    $(CC) $(CFLAGS) -c -o timerQueue.o timerQueue.c

clean: 
    @rm -f *.o test1 test2 *~
```

Now the 'problem' is that every time I run make, it remakes the tests even if nothing changed. I'm trying to understand why this is happening since the dependencies clearly don't change. any ideas?

---

### Post by dwhitney67 on 2010-05-04
It would seem from the Makefile you posted that you have an indentation problem within the rule-statements.  But other than that, consider simplifying the Makefile to something like:
```

APP1   = test1
APP2   = test2

SRCS1  = test1.c timerQueue.c
SRCS2  = test2.c timerQueue.c

OBJS1  = $(SRCS1:.c=.o)
OBJS2  = $(SRCS2:.c=.o)

CFLAGS = -g -Wall -std=gnu99
LIBS   = -lpthread

.PHONY: all clean


all: $(APP1) $(APP2)

$(APP1) : $(OBJS1)
        $(CC) $^ $(LIBS) -o $@

$(APP2) : $(OBJS2)
        $(CC) $^ $(LIBS) -o $@

clean: 
        @$(RM) $(OBJS1) $(APP1)
        @$(RM) $(OBJS2) $(APP2)

```

Alternatively, you could use a Makefile like this where you specify the version you wish to make by specifying the VER(SION) to make:
```

# Adjust VER from the command line to adjust the default
#
VER    = 1

APP    = test$(VER)

SRCS   = test$(VER).c timerQueue.c

OBJS   = $(SRCS:.c=.o)

CFLAGS = -g -Wall -std=gnu99
LIBS   = -lpthread

.PHONY: all clean


all: $(APP)

$(APP) : $(OBJS)
        $(CC) $^ $(LIBS) -o $@

clean:
        @$(RM) $(OBJS) $(APP)

```
Usage:
```

make          # This compiles test1.c and produces test1
make VER=2    # This compiles test2.c and produces test2

```
In either case, neither of the Makefiles above have real dependency checking.  For that, your Makefile will need a few more rules.  Try to adapt the following Makefile to your needs to obtain the dependency feature:
```

APP      = myapp

OBJDIR   = .srcobjs

SRCS    := $(shell find . -name '*.cpp')
SRCDIRS := $(shell find . -name '*.cpp' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))

INCLUDES = -I./Include
CPPFLAGS = -Wall -pedantic -ansi -c $(INCLUDES)
LDFLAGS  =

SHELL    = /bin/bash

.PHONY: all clean distclean

all: buildrepo $(APP)

$(APP) : $(OBJS)
        @echo "Building $@..."
        @$(CXX) $^ $(LDFLAGS) -o $@

$(OBJDIR)/%.o: %.cpp
        @echo "Generating dependencies for $<..."
        @$(call make-depend, $<, $@, $(subst .o,.d,$@))
        @echo "Compiling $<..."
        @$(CXX) $(CPPFLAGS) $< -o $@

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


# usage: $(call make-depend, SourceFile, ObjectFile, DependFile)
define make-depend
  $(CXX) -MM -MF $3 -MP -MT $2 $(CPPFLAGS) $1
endef

ifneq "$(MAKECMDGOALS)" "distclean"
ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif
endif

```

P.S.  Don't forget that Makefiles are sensitive to tab-spaces; if you copy/paste any of the above, make sure you check that all tab-spaces which were used are preserved.  vim is your best bet for a competent editor in such cases.

---

