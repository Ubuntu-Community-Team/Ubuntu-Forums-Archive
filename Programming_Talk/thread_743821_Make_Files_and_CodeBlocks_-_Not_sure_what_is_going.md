---
title: "Make Files and CodeBlocks - Not sure what is going on"
date: 2008-04-03
forum: Programming Talk
---

### Post by RudolfMDLT on 2008-04-03
Hi there,

I've happily been using code::blocks on windows and linux for almost a year now, and admittedly, I've never written anything advanced.

I now have a project to do for varsity, where the use of an API is required. basically, you have to solve a map and the map generation code is hidden in a dll/.so file.

Codeblocks has always been able to compile and run my work, but now when I run the program I get the following error: 

> rudolf@RudolfLaptop:~/Desktop/example$ ./exampleRover 
./exampleRover: error while loading shared libraries: libRover.so: cannot open shared object file: No such file or directory


The shared object seems to be a file called "libRover.so". I have found two ways to solve this:

1) Copy the .so file into /usr/lib as root and everything runs fine, that is, clicking "build and run" works. and running the program from the terminal also works.
or
2)Remove the .so file from /usr/lib and edit the make file;

Original

> # Makefile for example client code using Rover API
# Created: 2008/03/28
#
# $Id$
#

# Compiler
CC=g++
DOXYGEN=doxygen

# Objects
OBJECTS=exampleRover.o functions.o

[COLOR="Red"]ifeq ($(OSTYPE),linux)                # Linux
  LIBS=-Wl,-rpath,. -L. -lRover
else                                  # Mac OS X
  LIBS=-L. -lRover
endif[/COLOR]

# Executable
TARGET=exampleRover

# Compiler flags
#CPPFLAGS=-Wall -g `sdl-config --cflags`
CPPFLAGS=-Wall -g -m32 -fPIC

# Linker flags
#LDFLAGS=`sdl-config --libs` -lSDL -lSDL_image
LDFLAGS=

all: $(OBJECTS) doxygen
	$(CC) $(LIBS) $(OBJECTS) $(CPPFLAGS) $(LDFLAGS) -o $(TARGET)

%.o: %.cpp
	$(CC) $(CPPFLAGS) -c $< -o $@

doxygen:
	$(DOXYGEN)

# cleanup
clean:
	-rm -rf $(OBJECTS)

distclean:
	-rm -rf $(TARGET) $(TARGET).exe $(OBJECTS) *.log html *.layout *.depend

realclean: distclean
	rm -rf libRover.dll libRover.so Rover.h Surface.h common.h

# EOF

New:

> # Makefile for example client code using Rover API
# Created: 2008/03/28
# Ken Nixon
#
# $Id$
#

# Compiler
CC=g++
DOXYGEN=doxygen

# Objects
OBJECTS=exampleRover.o functions.o

[COLOR="Red"]  LIBS=-Wl,-rpath,. -L. -lRove[/COLOR]r


# Executable
TARGET=exampleRover

# Compiler flags
#CPPFLAGS=-Wall -g `sdl-config --cflags`
CPPFLAGS=-Wall -g -m32 -fPIC

# Linker flags
#LDFLAGS=`sdl-config --libs` -lSDL -lSDL_image
LDFLAGS=

all: $(OBJECTS) doxygen
	$(CC) $(LIBS) $(OBJECTS) $(CPPFLAGS) $(LDFLAGS) -o $(TARGET)

%.o: %.cpp
	$(CC) $(CPPFLAGS) -c $< -o $@

doxygen:
	$(DOXYGEN)

# cleanup
clean:
	-rm -rf $(OBJECTS)

distclean:
	-rm -rf $(TARGET) $(TARGET).exe $(OBJECTS) *.log html *.layout *.depend

realclean: distclean
	rm -rf libRover.dll libRover.so Rover.h Surface.h common.h

# EOF

The IF statements doesn't seem to recognize my OS. For the record I know NOTHING about make files and never needed to use them.

Sorry for the long background, but my question is this: Can I make codeblcoks build the program correctly, or do I need to switch to a new IDE that uses make files(I've experimented with K develop and Netbeans)? 
I know I can get the job done using vi and the make file, but I would appreciate it if I could use the IDE.

I have done some google searching but I'm not really sure what the heck to look for?

Any advice or pointers will be appreciated,

Thanks,

Rudolf

---

### Post by dark-cloud on 2008-10-08
I'm pretty new to both Code::Blocks and Ubuntu and had the same problem as you, to fix it all I did was.

File /etc/ld.so.conf
add /usr/local/lib
(path to search for libaries)
then sudo ldconig

---

