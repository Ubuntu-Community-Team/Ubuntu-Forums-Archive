---
title: "Simple Makefile, but still can't get it to link."
date: 2007-01-12
forum: Programming Talk
---

### Post by evster on 2007-01-12
Hello,

I am starting a new project and I am starting with two files, pretty much as simple as I can get it.  One (main.cpp) contains the mainline, the other (MainWindow.cpp) will contain the main window as it might suggest.  Right now the MainWindow is just an empty class with a constructor and a destructor and my main line just constructs a MainWindow and doesn't do anything with it.  My Makefile is pretty simple so I don't think there is anything wrong with it.

```
CC=gcc 
CFLAGS=
OBJ=main.o MainWindow.o

main: $(OBJ)
	$(CC) -o main $(OBJ)

main.o:  MainWindow.h
	gcc -c main.cpp
  
MainWindow.o:  MainWindow.h
	gcc -c MainWindow.cpp

clean:
	rm -f main $(OBJ)
```

Anyway, when I try to build it it compiles the files fine but then I get this error:

```
gcc -c main.cpp
gcc -c MainWindow.cpp
gcc  -o main main.o MainWindow.o
main.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
make: *** [main] Error 1

```

Any ideas?

---

### Post by stoffe on 2007-01-12
I'm far from an expert (or even good) at compiling stuff, but it doesn't look like a problem with the makefile per se, but rather some problem with the linking (would give same result from commandline). Are you using any external libraries? If so, you must specify those in the makefile when linking. If it's a properly installed library, most likely adding a [FONT="Courier New"]-l*library_name*[/FONT] (that's lowercase "L") switch to the main rule should be sufficient. For clarity, that should probably go in CFLAGS and  $(CFLAGS) be included instead.

Hope that gives some help on the way.

---

### Post by supirman on 2007-01-12
use g++ to compile c++ (.cpp) files.

---

### Post by Houman on 2007-01-12
hi there,

I see several mistakes, one of which being what supirman mentioned, use g++ to compile cpp files, and also some others, here is my rewrite with the red parts denoting the additions:

```

CPP=[COLOR="Red"]g++[/COLOR]
[COLOR="Red"]CPPFLAGS = -g -O2 -Wall[/COLOR]
OBJ=main.o MainWindow.o

main: $(OBJ)
	$(CPP) [COLOR="Red"]$(CPPFLAGS)[/COLOR] -o main $(OBJ)

clean:
	rm -f main $(OBJ)

```

some of it is cosmetic, but i think the source of the error is just the incorrect use of gcc instead of g++. I omitted the compilation rules for the individual cpp files because they will get built by [implicit rules]("http://web.mit.edu/6.033/labdoc/make_10.html")[mit.edu]. Also I added the CPPflags, it will give you some optimization, lots of warnings and will include debugging information IF you want to debug your program later on. 

regards

Houman

---

### Post by evster on 2007-01-12
Thanks for the help.  I got it working (for now ;) ).

---

