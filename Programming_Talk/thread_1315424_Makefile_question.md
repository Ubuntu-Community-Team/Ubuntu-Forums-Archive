---
title: "Makefile question"
date: 2009-11-05
forum: Programming Talk
---

### Post by maxxjr on 2009-11-05
I have inherited a project with a "Makefile" strategy already in place.  There is a root Makefile, and there are full Makefiles in sub-directories.  Each file has its own COMPILE command line defined, so that if I want to change a compiler option, I have to edit both the root Makefile and the Makefiles in the subdirectories.  I would like to change things so that if I change a compiler option in the root Makefile, it is propagated to the Makefiles in the subdirectories.


In the root makefile, these sub-directory makefiles are called like so:

@(cd <DIR>/;$(MAKE) -f <DIR>.mak CFG=$(CFG))

Where CFG and MAKE are simple, such as "Debug" and "make" respectively.  

COMPILE=g++ -c "-DUNIX" -O2

If I try passing the $COMPILE variable in a similar fashion:

@(cd <DIR>/;$(MAKE) -f <DIR>.mak CFG=$(CFG) COMPILE=$(COMPILE))

I get an error, because the COMPILE string gets broken up, and $(MAKE) chokes on arguments that it does not recognize.

Any suggestions on how to get a change to propagate?

Thanks!

---

### Post by dwhitney67 on 2009-11-05
If you have a directory structure, with a root-dir and then subdirs, you can define your common Makefile defs and rules in a file within the root-dir, and then include this file (or files) within the subdir Makefile.

For example...

root-dir/common-defs.mk:
```

SRCS     = $(wildcard *.cpp)
OBJS     = $(SRCS:.cpp=.o)

CXXFLAGS = -Wall -ansi -pedantic -c
LDPATH   = -L/usr/local/lib
LIBS     = -lmyLib

```

root-dir/common-rules.mk:
```

.PHONY: all clean distclean

all: $(APP)

$(APP): $(OBJS)
<tab>$(CXX) $^ $(LDPATH) $(LIBS) -o $@

.cpp.o:
<tab>$(CXX) $(CXXFLAGS) $<

clean:
<tab>$(RM) $(OBJS)

distclean: clean
<tab>$(RM) $(APP)

```

root-dir/sub-dir/Makefile:
```

include ../common-defs.mk

APP       = myAppName
CXXFLAGS += -g

include ../common-rules.mk

```

root-dir/Makefile:
```

SUBDIRS = sub-dir

all:
<tab>@for dir in $SUBDIRS; do \
<tab><tab>make -C $$dir; \
<tab>done

```

P.S.  I did not test any of the above, but it should work.  Replace <tab> with an actual tab-space.

---

