---
title: "First custom Makefile (C++)"
date: 2011-08-20
forum: Programming Talk
---

### Post by OlyPerson on 2011-08-20
I have a project that I want to keep very organized but that organization is proving to be my downfall.  There are a number of things I'd like help with, please!


_1._
I would like my project to be organized into four directories: 
src/
include/
bin/
build/
with the Makefile being at the base dir, but for some reason I can't even get a basic make to work, the big issue is **"-I" not working how I think it will**, apparently.  Here's what I have:
```
TRG := RT_Process
OBJS := Position.o \
		RT_Process.o
CC := g++
DEBUG := -g
CFLAGS := -I./include/ -I./src/ -Wall -c $(DEBUG)
LFLAGS := -Wall $(DEBUG)

$(TRG) : $(OBJS)
	    $(CC) $(LFLAGS) $(OBJS) -o $(TRG)

RT_Process.o : RT_Process.cpp RT_Process.h Position.h
		$(CC) $(CFLAGS) RT_Process.cpp

Position.o : Position.cpp Position.h
		$(CC) $(CFLAGS) Position.cpp

clean:
		\rm *.o *~ $(TRG)
```
I read in the g++ man page that -I includes only header files to be searched, not sure how I'd work with .cpp files then.


_2._
I would like binary files to go into ./bin and the final binary to go into ./build (if that's what's normally done?).  Any hints?


_3._
This could grow quite large, what are the **suggested methods for make dependencies dynamic** so I don't have to manually add them every time I add or remove a dependency?  I've read a couple articles somewhat related but they were around 10 years old and not straight-forward.


Thanks if anyone can help, I've read quite a few tutorials on making Makefiles but can't seem to get past these issues for my own coding.

PS: If you're curious about my project, I'm trying to turn this procedural code I work with for programming robots into object-oriented code as I've noticed it's *extremely* annoying to make any changes to the old code.  Cool project really.

---

### Post by dwhitney67 on 2011-08-20
I'm not sure why you need a build directory; seems to me that the bin directory should suffice.  Regardless, based on the requirements you specified, this Makefile should work for you:
```

APP       = myapp

DEBUG     = -g
INCLUDES  = -I./include
CXXFLAGS  = $(DEBUG) -Wall -pedantic $(INCLUDES) -c
LDFLAGS   =

# There should not be any reason to edit anything below this line
#
SRC_DIR   = src
BIN_DIR   = bin
BUILD_DIR = build
OBJDIR    = .srcobjs

SRCS     := $(shell find $(SRC_DIR) -name '*.cpp')
SRCDIRS  := $(shell find $(SRC_DIR) -name '*.cpp' -exec dirname {} \; | uniq)
OBJS     := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS     := $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))

DEPENDS   = -MT $@ -MD -MP -MF $(subst .o,.d,$@)

SHELL     = /bin/bash

.PHONY: all clean distclean


all: buildrepo $(BIN_DIR)/$(APP)

install: all
	install -m 755 $(BIN_DIR)/$(APP) $(BUILD_DIR)

$(BIN_DIR)/$(APP): $(OBJS)
	$(CXX) $^ $(LDFLAGS) -o $@

$(OBJDIR)/%.o: %.cpp
	$(CXX) $(CXXFLAGS) $(DEPENDS) $< -o $@

clean:
	$(RM) -r $(OBJDIR)
	$(RM) $(BIN_DIR)/$(APP)

distclean: clean
	$(RM) $(BUILD_DIR)/$(APP)

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

### Post by OlyPerson on 2011-08-20
Wow! Thanks!  That's awesome!  Now I just have to go through and understand it all, is that from a template or did you just write all that yourself?  Very impressive, wasn't expecting that.

Essentially I can remove build/ with this, yes?

---

