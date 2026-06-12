---
title: "Is there anything similar to g++ -MM that doesn't strip off directories?"
date: 2009-07-01
forum: Programming Talk
---

### Post by stair314 on 2009-07-01
I'm trying to set my project up to have automatically generated dependencies. I'm using the old fashioned approach with just one depend file. The project has source files in several subdirectories, so if I just use g++ -MM, a source file like "subdir/foo.cpp" generates a rule for "foo.o" in my depend file. This is bad, to match "subdir/foo.cpp" it needs to "subdir/foo.o". Is there a different version of the -MM flag that doesn't strip off subdirs? I've been reading through the gcc manual and see all sorts of things for putting different constants before the object file name but haven't found anything that does quite what I want.

---

### Post by dwhitney67 on 2009-07-01
If you have source code in one or more sub-directories of a project, here is one way to build the application (and the dependencies):
```

APP      = myapp

OBJDIR   = .srcobjs

SRCS    := $(shell find . -name '*.cpp')
SRCDIRS := $(shell find . -name '*.cpp' -exec dirname {} \; | uniq)
OBJS    := $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
DEPS     = $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))

INCLUDES = -I./Include
CXXFLAGS = -Wall -pedantic -ansi -c $(INCLUDES)
LDFLAGS  =


all: $(APP)

$(APP) : buildrepo $(OBJS)
        @echo "Building $@..."
        @$(CXX) $(OBJS) $(LDFLAGS) -o $@

$(OBJDIR)/%.o: %.cpp
        @echo "Generating dependencies for $<..."
        @$(call make-depend,$<,$@,$(subst .o,.d,$@))
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


# usage: $(call make-depend,source-file,object-file,depend-file)
define make-depend
  $(CXX) -MM            \
         -MF $3         \
         -MP            \
         -MT $2         \
         $(CXXFLAGS)    \
         $(INCLUDES)    \
         $1
endef

ifneq "$(MAKECMDGOALS)" "clean"
-include $(DEPS)
endif

```
I've attached a sample project that employs the Makefile shown above.  You can give it a try for test purposes.

------------

EDITED:  Oops!  I forgot to add the appropriate Makefile statement to include the dependencies.  That has been corrected now.

---

### Post by stair314 on 2009-07-01
Wow, I didn't expect such a detailed reply! Thanks!

---

