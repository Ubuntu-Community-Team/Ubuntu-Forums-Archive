---
title: "Make Not Compiling Wildcard Target if no .o file exists"
date: 2011-08-03
forum: Programming Talk
---

### Post by Eosis on 2011-08-03
Am currently in the process of writing my first makefile and am finding that if I try to use a makefile with a wildcard target, I get compiler errors unless the wildcard.o exists already.  The same does not occur if I use an explicit makefile.

Ie. When I try to make the program using

```
make attempt
```and the following makefile:

[PHP]
CC    = g++ -O2 -g -pedantic -Wall -I/home/eosis/c++/fun
RM    = /bin/rm -f

%: %.o add.o multiply.o
    $(CC) $*.o add.o multiply.o -o $*

%.o: %.cc
    $(CC) -c $*.cc

add.o: add.cc
    $(CC) -c add.cc

multiply.o: multiply.cc
    $(CC) -c multiply.cc
[/PHP]I get the following error unless attempt.o exists

```

attempt.cc:(.text+0x21): undefined reference to `add(int, int)'
attempt.cc:(.text+0x49): undefined reference to `multiply(int, int)'

```If attempt.o exists in the directory then make functions as normal.
I've consulted some makefile docs and examples and can't see why it would return this error.

---

### Post by gmargo on 2011-08-03
There are a few problems.  One is that there is no mention of "attempt.*" in the Makefile.  Another is the use of CC which should be reserved for C programs, not C++ programs.

Here is my version of your makefile, which leverages make's built-in rules:

```

[FONT=monospace]CXXFLAGS=-O2 -g -pedantic -Wall -I/home/eosis/c++/fun

OBJS=attempt.o add.o multiply.o

all: attempt

attempt: $(OBJS)
    $(LINK.cc) -o $@ $(OBJS)

clean:
    rm -f attempt $(OBJS)
[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by dwhitney67 on 2011-08-03
An alternative Makefile:
```

APP = myapp

SRCS = $(wildcard *.cpp)
OBJS = $(SRCS:.cpp=.o)

CXXFLAGS = -Wall -pedantic -g -I./

$(APP) : $(OBJS)
        $(CXX) $^ -o $@

clean :
        $(RM) $(OBJS) $(APP)

```
I'm not sure why the -I is used with the original Makefile.  If the source file(s) are not in the same location as the header file(s), then I understand.  However, the path should be specified as relative to the sorce file(s), instead of hard-coded path.  For example, -I../fun

---

