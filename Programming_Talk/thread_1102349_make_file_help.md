---
title: "make file help"
date: 2009-03-21
forum: Programming Talk
---

### Post by nbo10 on 2009-03-21
Hi All,
Ive been trying to write a makefile that does the following

```

g++ -Wall -c filename.cpp
 g++ -o file.o filename.o  -lgsl -lgslcblas -lm

```

I get nothing but  *** missing separator. errors with anything I try.
My best attempt was 
```
CC=g++
CFLAGS=-Wall -c
LDFLAGS= -lgsl -lgslcblas -lm
  $(CC) $(CFLAGS) $(LDFLAGS) -o file.o filename.cpp 
```

Can anyone offer insight? Thanks

---

### Post by geirha on 2009-03-21
```

CC = g++
CFLAGS = -Wall -c
LDFLAGS = -lgsl -lgslcblas -lm

# The following rule tells make how to create a .o-file from a .cpp file:
# Note that there must be a tab before the $(CC)
.cpp.o:
	$(CC) $(CFLAGS) -o $@ $<

```
With that makefile, you can run ```
make file.o
``` to compile file.cpp into file.o

Add another rule to link:
```

myprog: file.o main.o
	$(CC) $(LDFLAGS) -o $@ file.o

```

Now you can run ```
make myprog
``` to compile the binary myprog. It will first check if file.o and main.o are compiled, and compile them if necessary, then link.

Add an all-rule just above the .cpp.o:. 
```
all: myprog
```
Now, typing ```
make
``` will trigger the all-rule, which will compile and link everything needed to make the myprog binary.

It's common to also make a clean-rule
```
clean:
	-rm -v myprog file.o main.o

```

---

