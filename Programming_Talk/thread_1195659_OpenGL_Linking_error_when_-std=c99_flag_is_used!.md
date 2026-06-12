---
title: "OpenGL: Linking error when -std=c99 flag is used!"
date: 2009-06-24
forum: Programming Talk
---

### Post by nfm on 2009-06-24
Hi guys,
I'm really clueless :(. Once I comment out '-std=c99' in my Makefile some function **does not link**. It's a really nice demo of plane model, I'm using GLUT so you can rotate the figure. Please try it out. Does anybody know why this is happening? Also my original plan was to have 'm3dCrossProduct' function in math3d.h since it is inlined so I'm reckoning it is more efficient to have short, inlined functions within .h files.

Quick look at the Makefile:
```
PROG = litjet
OBJS = $(PROG).o math3d.o
CC = gcc
DEBUG = -g
CFLAGS = -Wall #-std=c99
LFLAGS = -lglut -lGL -lGLU -lm

$(PROG): $(OBJS)
	$(CC) $(LFLAGS) $(OBJS) -o $(PROG)

math3d.o: math3d.c
	$(CC) -c $(CFLAGS) math3d.c

$(PROG).o: $(PROG).c
	$(CC) -c $(CFLAGS) $(PROG).c

clean:
	rm -f *.o ./$(PROG)
```

Error:
```
[nfm@phenon litjet]$ make
gcc -c -Wall -std=c99 litjet.c
math3d.h:11: warning: inline function &#8216;m3dCrossProduct&#8217; declared but never defined
math3d.h:11: warning: inline function &#8216;m3dCrossProduct&#8217; declared but never defined
gcc -c -Wall -std=c99 math3d.c
gcc -lglut -lGL -lGLU -lm litjet.o math3d.o -o litjet
math3d.o: In function `m3dFindNormal':
math3d.c:(.text+0xe1): undefined reference to `m3dCrossProduct'
collect2: ld returned 1 exit status
make: *** [litjet] Error 1
[nfm@phenon litjet]$
```

**undefined reference to `m3dCrossProduct'**, huh? I'm including math3d.h at the top where the prototype is :confused:.

---

### Post by Zugzwang on 2009-06-24
I don't know how this is connected to the "c99" standard, but in general, inline functions should be defined in header files before using them (hence the warnings when compiling litjet.c) and not put separately into a ".c" file. The reason is that the compiler needs to know the implementation in order to inline it and the C compiler usually works in a single-pass system.

Therefore, when compiling math3d.c, the function "m3dCrossProduct" will not be put into math3d.o (since you declared it to be inlined) and will not be found by the linker. 

Solution: If you declare a function to be inlined, put the implementation into the header file where you declare it as well.

---

### Post by nfm on 2009-06-24
I fixed this issue by moving func prototype of m3dCrossProduct from math3d.h to math3d.c, otherwise it won't work. Also the prototype can't have inline keyword, I didn't know that, trial and error ;).

---

### Post by cyberslayer on 2009-06-24
Inline functions are not supported in C89 (the default) but are supported in C99.  The compiler also is not required to actually inline functions defined as inline but it has the option to do so.  In gcc, the inline keyword in legal in C89 mode but doesn't do anything.  The reason you got an error when you commented out -std=c99 is due to due your Makefile.  This is because when you commented out -std=c99 the Makefile was effectively as follows:
```
PROG = litjet
OBJS = $(PROG).o math3d.o
CC = gcc
DEBUG = -g
CFLAGS = -Wall #-std=c99
LFLAGS = -lglut -lGL -lGLU -lm

$(PROG): $(OBJS)
	$(CC) $(LFLAGS) $(OBJS) -o $(PROG)

math3d.o: math3d.c
	$(CC) -c -Wall #-std=c99 math3d.c

$(PROG).o: $(PROG).c
	$(CC) -c -Wall #-std=c99 $(PROG).c

clean:
	rm -f *.o ./$(PROG)


```
Thus, math3d.c was not compiled.  Probably, you already had a $(PROG).o file so the $(PROG) target still linked with the .o files which resulted in the error.

---

### Post by nfm on 2009-06-24
cyberslayer thanks for the input, I now solved the issue :). Inlined functions should not be prototyped, all I needed was to declare inline function as static to avoid namespace pollution or multiple redefinitions! irc #c ftw!

---

