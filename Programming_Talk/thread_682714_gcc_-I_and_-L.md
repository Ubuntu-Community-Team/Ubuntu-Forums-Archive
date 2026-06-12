---
title: "gcc -I and -L"
date: 2008-01-30
forum: Programming Talk
---

### Post by keeler1 on 2008-01-30
I was trying to compile some example code given to me by one of my professors but in their makefile it contains gcc options -I and -L both with no spaces after them but with just directories after them.

When I run this makefile (that was given to me by my professor) 

```
# path to PIXIE
PIXIEROOT = /home/matt/Pixie

# program to render from .rib
RENDRIB  = $(PIXIEROOT)/bin/rndr

# compiler information
CXX = /usr/bin/gcc
CFLAGS = -I$(PIXIEROOT)/include  -g
LDLIBS = -L$(PIXIEROOT)/lib 

# files and intermediate files we create
OBJS  = cube.o unitcube.o
PROG  = cube
RIB   = cube.rib
IMAGE = cube.tif

# rules for building -- ordered from final output to original .c for no
# particular reason other than that the first rule is the default

# image from .rib
$(IMAGE): $(RIB)
	$(RENDRIB) $(RIB)

# .rib from program
$(RIB): $(PROG)
	./$(PROG)

# program from .o
$(PROG): $(OBJS)
	$(CXX) -o $(PROG) $(OBJS) $(CFLAGS) $(LDLIBS) -lri -lm

# .o from .c
cube.o: cube.c unitcube.h
	$(CXX) -c cube.c $(CFLAGS)

unitcube.o: unitcube.c unitcube.h
	$(CXX) -c unitcube.c $(CFLAGS)


# remove everything but rib and final output image
.PHONY: clean
clean:
	rm -f *~ $(OBJS) $(PROG)

# remove everything including rib and final output
.PHONY: cleanest
cleanest: clean
	rm -f $(RIB) $(IMAGE)
```

It says it needs a file which is in the $(PIXIEROOT)/lib directory.

I am not quite sure what the -I and -L do and I hope knowledge of it will help me understand how to remedy it.

---

### Post by Zugzwang on 2008-01-30
> **keeler1 said:**
> 
It says it needs a file which is in the $(PIXIEROOT)/lib directory.

What's the name of the file? The option -L defines a directory in which the linker should search for libraries (in addition to the standard paths). The option -l<LIB> declares that the file "lib<LIB>.so" or "lib<LIB>.a" (or similarly) should be linked against your executable. So it assumes that your library name starts with a "lib". Maybe this is not the case?

Anyway, please also post the *exact* error message here. :-\"

---

### Post by keeler1 on 2008-01-30
well when I compile the code with the makefile here is what I get.

```
/usr/bin/gcc -o cube cube.o unitcube.o -I/home/matt/Pixie/include  -g -L/home/matt/Pixie/lib  -lri -lm
/usr/bin/ld: warning: libpixiecommon.so.0, needed by /home/matt/Pixie/lib/libri.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libtiff.so.3, needed by /home/matt/Pixie/lib/libri.so, not found (try using -rpath or -rpath-link)
/home/matt/Pixie/lib/libri.so: undefined reference to `osCreateDir(char const*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFWriteTile'
/home/matt/Pixie/lib/libri.so: undefined reference to `rotatem(float*, float const*, float)'
/home/matt/Pixie/lib/libri.so: undefined reference to `osDeleteFile(char const*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `identityMatrix'
/home/matt/Pixie/lib/libri.so: undefined reference to `osEnvironment(char const*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFGetFieldDefaulted'
/home/matt/Pixie/lib/libri.so: undefined reference to `osCreateThread(void* (*)(void*), void*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFSetDirectory'
/home/matt/Pixie/lib/libri.so: undefined reference to `osModuleError()'
/home/matt/Pixie/lib/libri.so: undefined reference to `translatem(float*, float, float, float)'
/home/matt/Pixie/lib/libri.so: undefined reference to `osDeleteMutex(pthread_mutex_t&)'
/home/matt/Pixie/lib/libri.so: undefined reference to `skewm(float*, float, float, float, float, float, float, float)'
/home/matt/Pixie/lib/libri.so: undefined reference to `osUnloadModule(void*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `osProcessEscapes(char*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `determinantm(float const*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFClose'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFSetErrorHandler'
/home/matt/Pixie/lib/libri.so: undefined reference to `osTempname(char const*, char const*, char*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFGetField'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFOpen'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFWriteDirectory'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFIsTiled'
/home/matt/Pixie/lib/libri.so: undefined reference to `osDeleteDir(char const*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `scalem(float*, float, float, float)'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFSetField'
/home/matt/Pixie/lib/libri.so: undefined reference to `osCPUTime()'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFReadTile'
/home/matt/Pixie/lib/libri.so: undefined reference to `osTime()'
/home/matt/Pixie/lib/libri.so: undefined reference to `osLoadModule(char const*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `osCreateMutex(pthread_mutex_t&)'
/home/matt/Pixie/lib/libri.so: undefined reference to `invertm(float*, float const*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFSetWarningHandler'
/home/matt/Pixie/lib/libri.so: undefined reference to `osEnumerate(char const*, int (*)(char const*, void*), void*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `identitym(float*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `osWaitThread(unsigned long)'
/home/matt/Pixie/lib/libri.so: undefined reference to `rotatem(float*, float, float, float, float)'
/home/matt/Pixie/lib/libri.so: undefined reference to `osFileExists(char const*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `osFixSlashes(char*)'
/home/matt/Pixie/lib/libri.so: undefined reference to `TIFFReadScanline'
/home/matt/Pixie/lib/libri.so: undefined reference to `osResolve(void*, char const*)'
collect2: ld returned 1 exit status
make: *** [cube] Error 1

```

My directory structure is as follows

```
Pixie
   -bin
   -displays
   -doc
   -include
   -lib
       -libpixiecommon.so.0
       -other libraries
   -modules
   -shaders
```

As far as the libtiff.so.3 goes, according to synaptic i have libtiff4 in my /usr/lib directory but it is not libtiff.so.3 it is libtiff.so.4 and libtiff.so.4.2.1

What do I need to do to make this work?

---

