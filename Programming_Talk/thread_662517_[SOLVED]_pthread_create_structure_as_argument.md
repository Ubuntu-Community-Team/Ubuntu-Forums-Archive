---
title: "[SOLVED] pthread_create: structure as argument"
date: 2008-01-09
forum: Programming Talk
---

### Post by nephritiri on 2008-01-09
orig post have been edited

---

### Post by stroyan on 2008-01-09
The compiler error message is because you tried to pass the entire struct instead of its address ```
pthread_create(&th[struct1.x],0,threadRotateFunction, (void *)struct1);
should be
pthread_create(&th[struct1.x],0,threadRotateFunction, (void *)&struct1);
```
You also have no parallelism because the pthread_join is called for each thread before starting any other.  If you tried to move the pthread join to a second loop you would get parallelism and a bug from a race condition as struct1.x is used in threadRotateFunction and modified by the pthread_create loop.  Perhaps you could use a struct2 and launch two threads at a time with different structs.  If you create more parallel threads than you have CPUs (or cores), then you are very likely to slow your program down because of thread management overhead.

Working with threads is very tricky.  Using threads to improve performance is a little bit more tricky.  If you really want to stick with parallel programming for speed then you may have more luck using gcc 4.2 and OpenMP.  See [http://en.wikipedia.org/wiki/OpenMP](http://en.wikipedia.org/wiki/OpenMP) .

---

### Post by nephritiri on 2008-01-09
hi. thanks for the correction. i did what uv sugested but i encountered another problem.

/tmp/ccbN063L.o: In function `main':
test2.cpp:(.text+0x18d): undefined reference to `pthread_join'
collect2: ld returned 1 exit status
make: *** [test2] Error 1

i was told that it ws due to including pthread libs for compiling/linking.
iv already included pthread.h and in fact, hav run some programs with pthreads before and they worked..

d'you hav idea why is that?

---

### Post by Lster on 2008-01-09
Hi

This link should explain how to do it with many common compilers.

[https://computing.llnl.gov/tutorials/pthreads/#Compiling](https://computing.llnl.gov/tutorials/pthreads/#Compiling)

Hope that helps,
Lster

---

### Post by nephritiri on 2008-01-09
hello. thankz. 
i compile my cpp file using make. i haven't any idea how to config pthread in linking/compiling with make.m sort of new to these configs.. anyone who has a suggestion?

thanks in advanz.

---

### Post by Lster on 2008-01-09
Well I'm not too good on make as well. Post your make file and we can probably help.

---

### Post by nephritiri on 2008-01-09
this is the makefile...

[HTML]
# generic makefile 

CC = g++

.SUFFIXES : .cpp .o

.cpp.o :
	$(CC) $(CFLAGS) -c $<

OBJS = binary.o jpegio.o color.o filter.o

JPEGLIB = libjpeg.a

test2 : test2.cpp $(OBJS)
	$(CC) -o $@ $< $(OBJS) $(JPEGLIB)
[/HTML]

those OBJS are already in the class library folder...
i don't have an idea how to deal with pthread here...

---

### Post by monkeyking on 2008-01-09
just add 

-lpthread

that should do it.

---

### Post by nephritiri on 2008-01-10
in compiling files simple c thread programs, i used this command:
 
cc -lpthread pthread1.c

but how will i integrate lpthread in make? anyone know?

---

### Post by dwhitney67 on 2008-01-10
See if the Makefile below works for you.  Btw, where are you obtaining libjpeg.a from?  Is it a library that you are creating?  On my system, all I have is /usr/lib/libjpeg.so.  Therefore the Makefile below may or not work for you.

```
# generic makefile 

SRCS = binary.cpp \
       jpegio.cpp \
       color.cpp \
       filter.cpp

LIBS = -ljpeg -lpthread

OBJS = $(SRCS:.cpp=.o)

test2: test2.cpp $(OBJS)
	$(CC) -o $@ $< $(OBJS) $(LIBS)

.cpp.o:
	$(CC) $(CFLAGS) -c $< -o $@
```

---

### Post by nephritiri on 2008-01-10
hey thanks. 

ive figured out what's missing. i was able to run pthread in make by using the line

[HTML]
test2 : test2.cpp $(OBJS)
	$(CC) -lpthread -o $@ $< $(OBJS) $(JPEGLIB)

instead of 

test2 : test2.cpp $(OBJS)
	$(CC)  -o $@ $< $(OBJS) $(JPEGLIB)
[/HTML]

and it worked.
though, ther's still an error but i think now that it's the cpp code itself. i think i can handle it this time. thanks guys! :)

BTW, libjpeg.a is an archive already included in the class library directory where i am working on.

---

