---
title: "Test SDL graphics primitive routines"
date: 2007-03-05
forum: Programming Talk
---

### Post by dave_567 on 2007-03-05
This should be a simple question for the right people.  I'm trying to compile the example programs from the SDL_gfx library. 

Source web page:
      [http://www.ferzkopp.net/joomla/content/view/19/14/](http://www.ferzkopp.net/joomla/content/view/19/14/)

I'm not able to get the example to compile.  I have installed the library from the package manager, copied the examples into a shared directory, and created the following make file.

> 
# the compiler to use
CC = gcc 

# Compiler flags
#CFLAGS =   #-Wall -ansi

# Libraries to include
LIBS = -lSDL  -lSDL_gfxPrimitives

# Folders to search for header files
INCLUDE =  -I/usr/include/SDL -I/usr/include/SDL_gfxPrimitives

# Source file
SOURCES = SDL_gfxPrimitives.c

# Converts all source file names to object file names
OBJS    = ${SOURCES:.c=.o}

# final executable name
PACKAGE = Primitives


#####################################################
# getting things to compile and link

all : ${OBJS}
	${CC} ${OBJS} -o ${PACKAGE} ${INCLUDE} ${LIBS} 

.c.o:
	${CC} ${CFLAGS} ${INCLUDE} -c ${SOURCES} 


and the header from the source code

```


#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>
#include <time.h>

#include "SDL.h"

#include "SDL_gfxPrimitives.h"


```

I get the following error when I run the make file:

```

make
gcc  TestGfxPrimitives.o -o Primitives -I/usr/include/SDL -I/usr/include/SDL_gfxPrimitives -lSDL  -lSDL_gfxPrimitives
/usr/bin/ld: cannot find -lSDL_gfxPrimitives
collect2: ld returned 1 exit status
make: *** [all] Error 1

```

What am I missing here??? :confused:

---

### Post by Wybiral on 2007-03-05
I believe you need to compile with the library "SDL_gfx"

The library itself is "libSDL_gfx.a" even though the header file is "SDL_gfxPrimitives.h"

Try compiling without the "Primitives" part.

---

### Post by dave_567 on 2007-03-05
Got it working with this change to the libaries.  :-)   Thanks very much!

```

# Libraries to include
LIBS = -lSDL  -lSDL_gfx

``` 

Now how was I suppose to get to this library link?  It was not in any of the readings or online references that I read.

---

