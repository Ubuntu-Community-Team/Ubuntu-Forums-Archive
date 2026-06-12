---
title: "help with first Makefile"
date: 2009-07-19
forum: Programming Talk
---

### Post by fredscripts on 2009-07-19
Hi!

I'm trying to make a very simple Makefile of my little C++ program.

The directory tree is as follows:
```

Foosrc/
    Controller/ 
            ... (.hpp and .cpp files)
    Model/
          ...
    View/
          ...
```


I've been googling and I've seen some simple Makefiles where you have to put the targets and all files ended with .o and such.

My question is if I can build a Makefile such that if I add another bar.cpp file either in /Model /View or /Controller, and invoke "make", it will detect it and compile and mount correctly, so I don't have to add "bar.o" on the Makefile. So a make that acts like a "Run" on an IDE.

Thanks so much!

---

### Post by dwhitney67 on 2009-07-19
You should be able to place the Makefile shown below within your Foosrc directory.  Of course, edit it as appropriate for your needs.
```

# Indicate your application name here
APP      = myapp

# Indicate your header file path(s), g++ compiler flags, and g++ linker flags here
INCLUDES = -I./Include
CXXFLAGS = -Wall -pedantic -ansi -c $(INCLUDES)
LDFLAGS  =

# You should not have to edit anything below this line
OBJDIR   = .srcobjs
SRCS    := $(shell find . -name '*.cpp')
SRCDIRS := $(shell find . -name '*.cpp' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS    := $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))


.PHONY: all clean distclean

all: buildrepo $(APP)

$(APP) : $(OBJS)
        @echo "Building $@..."
        @$(CXX) $(OBJS) $(LDFLAGS) -o $@

$(OBJDIR)/%.o: %.cpp
        @echo "Generating dependencies for $<..."
        @$(call make-depend, $<, $@, $(subst .o,.d,$@))
        @echo "Compiling $<..."
        @$(CXX) $(CXXFLAGS) $< -o $@

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


# usage: $(call make-depend,SourceFile, ObjectFile, DependFile)
define make-depend
  $(CXX) -MM -MF $3 -MP -MT $2 $(CXXFLAGS) $1
endef

ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif

```

---

### Post by fredscripts on 2009-07-19
Thanks so much!

How can I tell the Makefile that I'm gonna compile with

```
g++ -lglut -lm 
```

?
Thanks!

---

### Post by djbushido on 2009-07-19
Do you see the line where it says CXX flags? Re-do the line so that it reads:```
CXXFLAGS = -Wall -pedantic -ansi -lglut -lm -c $(INCLUDES)
```

---

### Post by fredscripts on 2009-07-19
amazing! thanks so much to all!

---

### Post by dwhitney67 on 2009-07-19
> **djbushido said:**
> Do you see the line where it says CXX flags? Re-do the line so that it reads:```
CXXFLAGS = -Wall -pedantic -ansi -lglut -lm -c $(INCLUDES)
```

Actually, the -lglut and the -lm are specifiers for OpenGL and the C Math libraries, and they are not used during compilation of the source code.  Thus it should not be part of CXXFLAGS, but instead LDFLAGS.

LDFLAGS is used during the link stage to build the application executable.

---

