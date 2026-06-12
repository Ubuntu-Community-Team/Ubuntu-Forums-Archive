---
title: "g++ opengl and x11 libraries"
date: 2008-02-21
forum: Packaging and Compiling Programs
---

### Post by shreyaspotnis on 2008-02-21
There's a certain program I need to compile which requires the following header files:
```
/* Standard OpenGL/GLX header files */
#include <GL/glx.h>
#include <GL/gl.h>
/* Headers needed for keys used in the program */
#include <X11/extensions/xf86vmode.h>
#include <X11/keysym.h>
```

I have installed the** libx11-dev** package using apt-get but i still don't have glx.h and gl.h header files and libraries.
Can you please tell me what all packages I need to install to get it working.
The make file for the progarm is :
```
#Makefile for GLX_BASE

PROJECT= glx_base
SOURCES= glx_base.c main.c
OBJECTS= glx_base.o main.o
CC= gcc

	
$(PROJECT): $(OBJECTS)
	$(CC) -O2 -g $(OBJECTS) -L/usr/X11R6/lib -lm -lGL -lXxf86vm -o $(PROJECT)
	@echo Compilation Complete

$(OBJECTS): $(SOURCES)
	@echo Compiling Sources
	$(CC) -O2 -Wall -ansi -pedantic -g -c $(SOURCES)

clean:
	@echo Deleting up $(OBJECTS) $(PROJECT)
	rm -f *.o;rm $(PROJECT)

```

I used to have fedora 8 previously and it used to compile without any errors ( all the packages were present ). Now I have switched to Ubuntu 7.10.

Thanks
Shreyas.

---

### Post by shreyaspotnis on 2008-02-21
Sorry.
I got the solution. Just got the libgl1-mesa-dev package and its running perfect:)

---

