---
title: "Error in compilation, problem with linker?"
date: 2010-02-04
forum: Packaging and Compiling Programs
---

### Post by chandlerjunior on 2010-02-04
Hi everyone, I'm new with linux and programming so forgive me if I ask something unusually easy or trivial.

Lately I'm trying to compile some program to do some numerical stuff

```
gcc -o hum hum.c -L/usr/lib/sse2  -llapack_atlas -llapack_atlas -llapack -lblas -latlas -lm

```

The compilation is sucessful and the program runs fine, but when I try to use a makefile instead of typing all that gibberish, all I get is this error.

```
cc     hum.c   -o hum
/tmp/ccRbHNGQ.o: In function `main':
hum.c:(.text+0xa7): undefined reference to `clapack_dgesv'
collect2: ld returned 1 exit status
make: *** [hum] Error 1

```

The makefile I used:

```
LIB_LOCATION=/usr/lib/sse2
FLAGS=-L$(LIB_LOCATION) -llapack_atlas -llapack -lblas -latlas -lm

hum : hum.o 
    gcc $(FLAGS) -o hum hum.o 

hum.o : hum.c clapack.h
    gcc $(FLAGS) -c hum.c  

```

I don't understand why I get this error, it shoud be the same as manually inserting the commands, maybe the linker doesn't like the makefile?

---

### Post by gmargo on 2010-02-04
It's not a problem with the linker.  I think it's a problem with the name of your makefile.

It is clear from your output that make is not reading your makefile. Instead make is using the default rule to build an executable directly from a .c file - just what it does if no makefile is present.  Just to make sure you know: the makefile should be named "makefile" or "Makefile" or "GNUmakefile", or else you need to specify the filename with the -f option.

You can simplify your makefile to the following, which uses standard definition names (CC, CFLAGS, LDFLAGS) to take advantage of the built-in rules:

```

CC=gcc
CFLAGS=-O
LIB_LOCATION=/usr/lib/sse2
LDFLAGS=-L$(LIB_LOCATION) -llapack_atlas -llapack -lblas -latlas -lm

hum : hum.o 
hum.o : hum.c clapack.h

```When I run "make -n" I get:
```

gcc -O   -c -o hum.o hum.c
gcc -L/usr/lib/sse2 -llapack_atlas -llapack -lblas -latlas -lm  hum.o   -o hum

```

---

### Post by chandlerjunior on 2010-02-05
Thanks! That did the trick, the problem was in the name of the makefile.

---

