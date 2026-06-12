---
title: "Makefile for an ASM and C project"
date: 2009-10-23
forum: Programming Talk
---

### Post by jimmio on 2009-10-23
Hello all,

I'm currently writing a kernel for an OS project I'm fooling around with. I can't figure out the best way to use a makefile for the project, though I know I need to because at the moment I'm rebuilding all files every time I test something new.

I'm using Assembly and C, and one file must be linked first. How should I go about setting up a makefile? I may know a little bit of assembly, but that still doesn't mean I know anything about Make.

Thanks in advance

-Jim

---

### Post by dwhitney67 on 2009-10-23
A Makefile's construct is similar to that of a script.  You define certain common variables (if any) and then the rules (or steps) that the Makefile must perform.

The first rule listed in a Makefile is the first rule that will be executed, barring any explicit rule on the command line where the 'make' is performed.

Damn, I forgot your question...


I don't know squat about compiling assembly; I thought that died out in the 90's.  A typical Makefile for compiling C source files *might* look like this:
```

APP    = myApp

SRCS   = first.c second.c third.c
OBJS   = $(SRCS:.c=.o)

CFLAGS = -Wall -pedantic -ansi -std=gu99 -c

$(APP) : $(OBJS)
<tab>   $(CC) $^ -o $@

```

---

### Post by jimmio on 2009-10-23
dwhitney, again thank you for your help, you've helped me in the past with Makefiles.

How do I set it up to recompile the C files if the header gets changed?

---

### Post by dwhitney67 on 2009-10-23
> **jimmio said:**
> dwhitney, again thank you for your help, you've helped me in the past with Makefiles.

How do I set it up to recompile the C files if the header gets changed?

Fantastic question.  This is probably one of the best debatable issues facing Makefile developers... how to setup dependencies, such that if one file (regardless if it is a source file or header file) is modified, is the project rebuilt.

There are many ways to "skin the cat", but not every approach works for every conceivable project.  The last couple of projects I have worked on maintain the header files and the .cpp (C++) source files in separate directories.  Apparently some folks like to use the 'cd' command a lot.

Here's a typical way I would set up a Makefile in such situations; perhaps it is adaptable to a flatter directory structure -- I just have not had the time to put down my Bass to find out.

Based on your project, anywhere you see CXX, just use CC; for CPPFLAGS, use CFLAGS; for 'cpp' use 'c', thus allowing you to use a Makefile similar to...
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

.PHONY: all clean distclean

all: buildrepo $(APP)

$(APP) : $(OBJS)
        @echo "Building $@..."
        @$(CXX) $(OBJS) $(LDFLAGS) -o $@

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

ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif

```

---

