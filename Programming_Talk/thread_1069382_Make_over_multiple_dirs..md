---
title: "Make over multiple dirs."
date: 2009-02-13
forum: Programming Talk
---

### Post by Thesuperchang on 2009-02-13
I have the following setup as a test run. However I cannot seem to get it to work at all.
[PHP]
Root
   + Makefile
   + core.h
   + main.cxx
   + /one
   |    + Makefile.one
   |     `one.cxx  
   |
    `/two
        + Makefile.two
         `two.cxx[/PHP]

Makefile
[PHP]CC = g++
CFLAGS = -Wall
INC = -I.
OBJ = main.o
BIN = prog

include one/Makefile.one
include two/Makefile.two

all : $(BIN)

$(BIN) : $(BIN)
	$(CC) $(CFLAGS) $(INC) $(LNK) -o $(BIN) $(OBJ)

main.o : main.cxx
	$(CC) $(CFLAGS) $(INC) -c -o main.o main.cxx[/PHP]

Makefile.one
[PHP]OBJ := one.o $(OBJ)
INC := -I./one $(INC)

one.o : one.cxx
	$(CC) $(CFLAGS) -c -o one.o one.cxx[/PHP]

Makefile.two
[PHP]OBJ := two.o $(OBJ)
INC := -I./two $(INC)

two.o : two.cxx
	$(CC) $(CFLAGS) -c -o two.o two.cxx[/PHP]

Any help would be greatly appreciated.

Thanks in advance,
C. Anderson.

---

### Post by dwhitney67 on 2009-02-14
I tried the Makefile combination like you attempted, even added my own sprinkle of skill to it, and I still could not get it to work.

Below is a typical style of Makefile that I've used in the past to build source code that has been deposited into different directories, of which practice I do not like, unless each directory will have its own Makefile to build a library.

```

BIN = prog

SRCS = one/one.cxx \
       two/two.cxx \
       main.cxx

INCLUDES = -I${PWD}

CXXFLAGS = -Wall -ansi -pedantic

OBJS = $(SRCS:.cxx=.o)

$(BIN): $(OBJS)
        $(CXX) $(OBJS) -o $@

%.o: %.cxx
        $(CXX) $(CXXFLAGS) $(INCLUDES) -c $^ -o $@

clean:
        $(RM) $(OBJS)
        $(RM) $(BIN)

```

Note, when linking object files together, you do not have to specify CXXFLAGS (or CFLAGS) or the INCLUDES; these are only used when compiling.

---

