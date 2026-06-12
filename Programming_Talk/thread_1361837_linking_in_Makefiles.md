---
title: "linking in Makefiles"
date: 2009-12-22
forum: Programming Talk
---

### Post by 10nitro on 2009-12-22
I have a series of .cc C++ files, that are each complete programs, when linked against the library I put in `/usr/local/lib/librawpod.a'
I compile them (roughly) like:
```
g++ -o appname appname.cc -L/usr/local/lib -lrawpod
```

Now, I would like to know the standard way of doing this in my Makefile.  It appears that this is what LDFLAGS is for, but the implicit rule puts $(LDFLAGS) first, so when I add ```
LDFLAGS += -L$(libdir) -lrawpod
``` it runs (roughly):
```
g++ -L/usr/local/lib -lrawpod -o appname appname.cc
```
which doesn't work because the order matters with linking options.

Currently I get around this by ```
$(APPS): %: %.cc
	$(CXX) $(CXXFLAGS) -o $@ $<	$(LDFLAGS)

```This works, but it seams like this is a kludge, and would be common enough that there is a better way, that uses the default implicit rules.

---

### Post by dwhitney67 on 2009-12-22
Your 'kludge' is similar to what I always do, so don't feel bad.

Typically I define my Makefiles such as:
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
I generate dependencies and compile a module before I attempt to link; you seem to do it all at once (which is fine for simple apps).

---

### Post by 10nitro on 2009-12-22
> **dwhitney67 said:**
> I generate dependencies and compile a module before I attempt to link; you seem to do it all at once (which is fine for simple apps).

I do generate dependencies first, it first generates a set of appname.d files, which it includes.
But yeah, I compile at link all at once, mostly because that's what the previous maintainer did. Since each app is only one file, it seemed like a good idea, and changing it doesn't appear to fix anything.

---

