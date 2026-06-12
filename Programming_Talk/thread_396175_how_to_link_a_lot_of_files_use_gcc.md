---
title: "how to link a lot of files use gcc"
date: 2007-03-29
forum: Programming Talk
---

### Post by LaoLiulaoliu on 2007-03-29
I have wrote a program and generated some files:
a.h     a.cpp     b.h      b.cpp     c.h      c.cpp      main.cpp   
how to compile and link them in g++.

---

### Post by Docter on 2007-03-29
This is from memory, about a decade ago, but from the command line...

g++ 1.cpp 2.cpp 3.cpp -o programname --flags --libs

making sure that you've got all your *.h files as '#include's.


hmmm.. I think that's right. Or you need a makefile.

---

### Post by LaoLiulaoliu on 2007-03-29
> **Docter said:**
> 

g++ 1.cpp 2.cpp 3.cpp -o programname
.

That's all right!Thank you!

---

### Post by ssam on 2007-03-29
create a file called Makefile in your source directory.

in it put ...
```

CC=g++
CFLAGS=-g -Wall

all: main

main: a.o b.o c.o main.o
    $(CC) $(CFLAGS) -o main main.o a.o b.o c.o

main.o: a.h b.h c.h main.cpp
    $(CC) $(CFLAGS) -c main.cpp

a.o: a.ccp a.h
    $(CC) $(CFLAGS) -c a.cpp

b.o: b.ccp b.h
    $(CC) $(CFLAGS) -c c.cpp

c.o: c.cpp c.h
    $(CC) $(CFLAGS) -c c.cpp

clean:
    rm main main.o a.o b.o c.o


```

now run

```
make
```
and it will build your program.

if you make changes to the code it will rebuild only the files that it needs to.

```
make clean
```
cleans up all the compiled files.

---

