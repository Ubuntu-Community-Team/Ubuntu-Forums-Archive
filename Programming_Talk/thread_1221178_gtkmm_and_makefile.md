---
title: "gtkmm and makefile"
date: 2009-07-23
forum: Programming Talk
---

### Post by swappo1 on 2009-07-23
Hello,

I can't figure out how to incorporate the following into my makefile to run gtkmm programs.
I need to put this line in the makefile
```
`pkg-config gtkmm-2.4 --cflags --libs`
```

Makefile
```
CXXFLAGS = -O2 -Wall -Werror -ansi
LDLIBS = -lpthread 
INCLUDE = .
PROG = hello
NAME = hello
SRCS = main.cpp hello_world.cpp
OBJS = main.o hello_world.cpp

$(PROG): $(OBJS)
		$(CXX) -o $(PROG) $(OBJS) $(LDLIBS)
		#mv $(PROG) ..

# How to make the object files:

-include deps.mak

deps:
		$(CXX) -MM $(SRCS) > deps.mak

# Cleaning target (only works with fileutils):

clean:
		$(RM) $(OBJS) $(PROG)


```

---

### Post by MadCow108 on 2009-07-23
just split it:
CXXFLAGS = -O2 -Wall -Werror -ansi `pkg-config gtkmm-2.4 --cflags`
LDLIBS = -lpthread `pkg-config gtkmm-2.4 --libs`
or
CXXFLAGS = -O2 -Wall -Werror -ansi $(shell pkg-config gtkmm-2.4 --cflags)
LDLIBS = -lpthread $(shell pkg-config gtkmm-2.4 --libs)

also you don't actually seem to use CXXFLAGS.

---

### Post by dwhitney67 on 2009-07-23
@ the OP

You do not have a specific rule to compile your source files to generate object files, thus 'make' will use it's built-in rule to make the object files.  This rule uses CFLAGS, thus as MadCow pointed out, since you do not use CXXFLAGS, you may want to consider renaming it to CFLAGS.

If you wish to continue using CXXFLAGS, here's a cleaned up Makefile:
```

PROG     = hello

#SRCS     = $(wildcard *.cpp)
SRCS     = main.cpp hello_world.cpp

OBJS     = $(SRCS:.cpp=.o)
CXXFLAGS = -O2 -Wall -Werror -ansi `pkg-config gtkmm-2.4 --cflags`
LDLIBS   = -lpthread `pkg-config gtkmm-2.4 --libs`
INCLUDE  =
DEPFILE  = deps.mak

.PHONY: clean

$(PROG): $(OBJS)
        $(CXX) $^ $(LDLIBS) -o $@

# How to make the object files:
.cpp.o:
        $(CXX) $(CXXFLAGS) -c $<

deps:
        $(CXX) -MM $(CXXFLAGS) $(SRCS) > $(DEPFILE)

# Cleaning target (only works with fileutils):
clean:
        $(RM) $(OBJS) $(PROG)

-include $(DEPFILE)

```

---

