---
title: "Makefile doesn't find files"
date: 2010-02-04
forum: Programming Talk
---

### Post by kahumba on 2010-02-04
Hi,
this is my makefile
```

CC = g++
VPATH = src
SRC_FILES = main.cpp Frame.cpp
OBJ_FILES=$(patsubst %.c, %.o, ${SRC_FILES})
CFLAGS=-O1 `pkg-config --libs --cflags gtkmm-2.4`

main: ${SRC_FILES}
    ${CC} ${CFLAGS} -o main ${OBJ_FILES}

%.o:%.cpp
    ${CC} ${CFLAGS} -o $@ $

clean:
    rm *.o main

```When I run "make" I get:
```

g++ -O1 `pkg-config --libs --cflags gtkmm-2.4` -o main main.cpp Frame.cpp
g++: main.cpp: No such file or directory
g++: Frame.cpp: No such file or directory
make: *** [main] Error 1

```The makefile is in the current folder and the source files in a "src" subfolder.
It only works if I replace "SRC_FILES = main.cpp Frame.cpp"
with "SRC_FILES = src/main.cpp src/Frame.cpp"
but I'd really like to automate that with VPATH=src, but for some reason I think it doesn't work. So what do I do for VPATH=src to work as expected?

---

### Post by linebp on 2010-02-04
I am no expert on make, but your problem is not that make can not find your files but that g++ can not find your files. The VPATH variable is used by make to find the files named in your rules. I am guessing that VPATH is not used for the command part.

---

### Post by kahumba on 2010-02-04
I see, so what do people do in this case? Hardcode the "src" folder into each entry of SRC_FILES? Like this?
SRC_FILES = src/main.cpp src/Frame.cpp

I really thought make allows for some magic to avoid this.

---

### Post by dwhitney67 on 2010-02-04
Try this Makefile in your project directory; it will search it for the source files:
```

APP      = myapp

OBJDIR   = .srcobjs

SRCS    := $(shell find . -name '*.cpp')
SRCDIRS := $(shell find . -name '*.cpp' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))

INCLUDES = `pkg-config --cflags gtkmm-2.4`
CPPFLAGS = -Wall -pedantic -ansi -c $(INCLUDES)
LDFLAGS  = `pkg-config --libs gtkmm-2.4`

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

### Post by kahumba on 2010-02-04
Thanks a lot
PS: Looks like learning creating good makefiles is like learning C from scratch

PPS: where did you learn about Makefiles if not a secret?

---

