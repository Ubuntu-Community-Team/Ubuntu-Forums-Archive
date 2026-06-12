---
title: "makefile creation"
date: 2011-12-06
forum: Packaging and Compiling Programs
---

### Post by shamjs on 2011-12-06
hi all,

im not having much knowledge on makefile.

here is my makefile

```

APP      = olupxtest
SRCDIR   = olupx/src
SRCS     = $(wildcard $(SRCDIR)/*.cpp)
OBJS     = $(SRCS:.cpp=.o)

CXXFLAGS = -g -fPIC -c
LDFLAGS  =
LIBS     = svm.o -lrt -Xlinker -zmuldefs

.PHONY: all clean


all: $(APP)

$(APP): $(OBJS)
        $(CXX) $(LDFLAGS) $^ $(LIBS) -o $@ 2>&1 | less -S

clean:
        $(RM) $(OBJS) $(APP)


```my .cpp files are in /home/shamjs/source/olupx/src
and my main program is in /home/shamjs/source



1>i need to compile and link one more file svm.cpp ,but its in different directory
its location is /home/shamjs/corenumeric/inc/stat/svmlib

how to adapt these changes in the makefile that i have .......

2>my olupxtest.cpp(main program) is in /home/shamjs/source ,but in makefile itseems that there is no rule to compile olupxtest.cpp ,since im getting error as undefined reference to `main

what are the modifications should i perform in my makefile????????

please guide me ....

waiting for your reply..........

---

