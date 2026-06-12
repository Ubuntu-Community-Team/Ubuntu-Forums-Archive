---
title: "makefile question"
date: 2010-11-12
forum: Programming Talk
---

### Post by audit on 2010-11-12
I always use a generic makefile when I write a C++ program, but I would like
if it would place all my object files in a directory called objects.

This is what I tried(but it did not work):
```

CXX=g++ 
CXXFLAGS=-c -Wall  
LIBS= 
LDFLAGS= 
SOURCES=$(shell ls *.cpp) 
OBJECTS=$(SOURCES:.cpp=.o) 
EXECUTABLE=main_test 
 
all: $(SOURCES) $(EXECUTABLE) 
     
$(EXECUTABLE): objects/$(OBJECTS)  
    $(CXX) $(LDFLAGS) $(OBJECTS) $(LIBS) -o $@ 
 
objects/%.o: %.cpp 
    $(CXX) $(CXXFLAGS) $< -o $@ 
 
clean: 
    rm -f $(OBJECTS)
```

Is there an "if" statement I could use to check for a directory and if it is not there create it?

---

### Post by dwhitney67 on 2010-11-12
Don't worry about using an "if"... just use "mkdir -p objects".

Btw, consider the following:
```

APP      = main_test

OBJDIR   = obj

SRCS     = $(wildcard *.cpp)
SRCDIRS  = ./
OBJS     = $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))

INCLUDE  =
DEBUG    = -g
CXXFLAGS = -Wall -pedantic $(INCLUDE) $(DEBUG)  

LDFLAGS  =
LIBS     =

.PHONY: all clean

 
all : makerepo $(APP) 
     
$(APP) : $(OBJS)  
        $(CXX) $(LDFLAGS) $^ $(LIBS) -o $@ 
 
$(OBJDIR)/%.o : %.cpp
        $(CXX) $(CXXFLAGS) -c $< -o $@ 
 
clean :
        $(RM) -r $(OBJDIR)

makerepo :
        @mkdir -p $(OBJDIR)

```

---

### Post by audit on 2010-11-12
Thank you very much--this will become my new generic makefile.

---

### Post by dwhitney67 on 2010-11-12
Also, add the following items marked in bold to the Makefile.  This will set your Makefile up to support file dependencies.
```

...
OBJS     = $(patsubst %.cpp,$(OBJDIR)/%.o,$(SRCS))
**DEPS     = $(patsubst %.cpp,$(OBJDIR)/%.d,$(SRCS))**

...

CXXFLAGS = $(INCLUDE) $(DEBUG) -Wall -pedantic **-MMD -MP**

...

makerepo :
        @mkdir -p $(OBJDIR)

[B]ifeq (,$(findstring clean,$(MAKECMDGOALS)))
-include $(DEPS)
endif
[/B]

```

---

