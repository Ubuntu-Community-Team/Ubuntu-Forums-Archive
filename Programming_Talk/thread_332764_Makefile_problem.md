---
title: "Makefile problem"
date: 2007-01-06
forum: Programming Talk
---

### Post by maddog39 on 2007-01-06
Hello all,

I am trying to run some example makefiles from my C++ but they wont work. Here is the makefile macro:
```

main.o: main.cpp
    $(CC) -c main.cpp -o main.o $(CFLAGS)

otherfunc.o: otherfunc.cpp
    $(CC) -c otherfunc.cpp -o otherfunc.o $(CFLAGS)

OBJ = main.o otherfunc.o

```
When I run 'make', it only compiles main.cpp and exits. Although when I compile manually it works fine. What's the problem?

Thanks
-maddog39

---

### Post by moma on 2007-01-06
Your Makefile is missing a top-level rule and rule that links "main.o" and "otherfunc.o" to an executable program (main).

> CC = g++
LD = g++

# Compiler flags go here.
CFLAGS = -g -Wall

# Linker flags go here. Currently there aren't any, but if we'll switch to
# code optimization, we might add "-s" here to strip debug info and symbols.
LDFLAGS =

OBJS = main.o otherfunc.o

PROG = main 

# top-level rule, to compile everything.
all: $(PROG)

# rule to link the program
$(PROG): $(OBJS)
^^^^        $(LD) $(LDFLAGS) $(OBJS) -o $(PROG)

main.o: main.cpp
^^^^    $(CC) -c main.cpp -o main.o $(CFLAGS)

otherfunc.o: otherfunc.cpp
^^^^    $(CC) -c otherfunc.cpp -o otherfunc.o $(CFLAGS)

[COLOR="Red"]Note: ^^^^ in the above listing denotes a TAB character.[/COLOR]

Run your program
./main 

Study the examples here:
[http://users.actcom.co.il/%7Echoo/lupg/tutorials/writing-makefiles/writing-makefiles.html](http://users.actcom.co.il/%7Echoo/lupg/tutorials/writing-makefiles/writing-makefiles.html)

---

### Post by maddog39 on 2007-01-06
Okay I got it working, thanks. My original makefile was the example from the book which is kinda wierd.

---

