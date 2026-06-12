---
title: "Need help with the following make file"
date: 2008-02-06
forum: Packaging and Compiling Programs
---

### Post by emp1953 on 2008-02-06
Below is my makefile
It works fine as it is
I want to put all the .o files into the ../bin/ directory  OBJDIR
then upon a clean I want the .o's removed from that directory
I was able to get the executable to go into the ../exe/ directory and it is removed upon a clean.

I cannot get it the .o's to work.  any help would be appreciated.


CC=g++
CFLAGS=-c -Wall
LDFLAGS=
OBJDIR=../bin/
SOURCES=a.cpp \
                  b.cpp \
                  c.cpp \
                  d.cpp \
                  e.cpp
OBJECTS=$(SOURCES:.cpp=.o)
EXECUTABLE=../exe/msg_broker

all: $(SOURCES) $(EXECUTABLE)
	
$(EXECUTABLE): $(OBJECTS) 
	$(CC) $(LDFLAGS) $(OBJECTS) -o $@

.cpp.o:
	$(CC) $(CFLAGS) $< -o $@
	
clean:
	-rm -rf *.o
	-rm -rf $(EXECUTABLE)

---

### Post by stroyan on 2008-02-08
You can use pattern rules to do that.
This changes the definition of OBJECTS, the .o from .cpp rule, and the clean rule.
```
CC=g++
CFLAGS=-c -Wall
LDFLAGS=
OBJDIR=../bin/
SOURCES=a.cpp \
        b.cpp \
        c.cpp \
        d.cpp \
        e.cpp
OBJECTS=$(SOURCES:%.cpp=../bin/%.o)
EXECUTABLE=../exe/msg_broker

all: $(SOURCES) $(EXECUTABLE)

$(EXECUTABLE): $(OBJECTS)
        $(CC) $(LDFLAGS) $(OBJECTS) -o $@

$(OBJDIR)%.o: %.cpp
        $(CC) $(CFLAGS) $< -o $@

clean:
        -rm -rf $(OBJECTS)
        -rm -rf $(EXECUTABLE)
```

---

