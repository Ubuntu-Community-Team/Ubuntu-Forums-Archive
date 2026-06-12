---
title: "Makefiles..."
date: 2011-07-08
forum: Programming Talk
---

### Post by ejohns85 on 2011-07-08
Hello,

I am new to the whole concept of makefiles, and I'm trying to compile and build my program using a makefile template I have found. My project consists of three directories: "source", where my .cpp files are (source1.cpp, source2.cpp, source3.cpp), "include", where my .h files are (header1.h, header2.h, header3.h), and "obj", where the object files are to be stored (obj1.o, obj2.o, obj3.o). In the project root directory is my makefile, which is as follows:
```

EXEC = myexe
CC = g++
IDIR = include
SDIR = source
ODIR = obj
LDIR= -L
LIBS= -l
CFLAGS = -I$(IDIR1) $(LDIR) $(LIBS)

_DEPS = header1.h header2.h header3.h
DEPS = $(patsubst %,$(IDIR)/%,$(_DEPS))

_OBJ = obj1.h obj2.h obj3.h
OBJ = $(patsubst %,$(ODIR)/%,$(_OBJ))

$(ODIR)/%.o: $(SDIR)/%.cpp $(DEPS)
    $(CC) -c -o $@ $< $(CFLAGS)

$(EXEC): $(OBJ)
    $(CC) -o $@ $^ $(CFLAGS) $(LDIR) $(LIBS)

clean:
    rm -f $(ODIR)/*.o *~ core $(INCDIR)/*~

```However, when I try to "make" my program, I get the following error:

"make: *** No rule to make target `obj/obj1.o', needed by `myexe'. Stop."

But as far as I can see, this rule is present, in the line
```

$(ODIR)/%.o: $(SDIR)/%.cpp $(DEPS)
    $(CC) -c -o $@ $< $(CFLAGS)

```Have I made some errors in the makefile, or is it a different problem?

Thanks!

---

### Post by Zugzwang on 2011-07-09
Do you actually have a file named "sources/obj1.cpp" present? I'm asking because you start with a list of header files, compute the "corresponding" object file names from it, but then use a ".cpp"-based rule to compile the object file.

---

### Post by dwhitney67 on 2011-07-09
> **ejohns85 said:**
> Have I made some errors in the makefile, or is it a different problem?


I typically use a Makefile similar to the following as a template when I'm working on a small project.
```

APP      = myapp

OBJDIR   = obj

SRCS    := $(shell find . -name '*.cpp')
SRCDIRS := $(shell find . -name '*.cpp' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))

DEBUG    = -g
INCLUDES = -I./include
CXXFLAGS = $(DEBUG) -Wall -pedantic $(INCLUDES) -c
LDFLAGS  =

DEPENDS  = -MT $@ -MD -MP -MF $(subst .o,.d,$@)

SHELL    = /bin/bash

.PHONY: all clean distclean


all: buildrepo $(APP)

$(APP): $(OBJS)
	$(CXX) $^ $(LDFLAGS) -o $@

$(OBJDIR)/%.o: %.cpp
	$(CXX) $(CXXFLAGS) $(DEPENDS) $< -o $@

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
If you have any questions, let me know.

---

