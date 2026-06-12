---
title: "Help with a makefile"
date: 2011-11-17
forum: Programming Talk
---

### Post by Liiiim on 2011-11-17
I'm trying to create a simple makefile for my project, but I'm running into some issues.  Here it is...

```
DIR=./
OBJECTS=$(DIR)main.o $(DIR)ui.o $(DIR)screen.o $(DIR)parsefile.o $(DIR)machine.o $(DIR)instructions.o
CC=gcc
CFLAGS=`pkg-config --cflags gtk+-2.0` -c -Wall
LDFLAGS=`pkg-config --libs gtk+-2.0`
EXE=sim

windows: DIR=./windows/
windows: CC=i486-mingw32-gcc
windows: CFLAGS=`pkg-config-script --cflags gtk+-2.0` -c -mms-bitfields -O2 -mwindows -Wall
windows: LDFLAGS=`pkg-config-script --libs gtk+-2.0`
widnows: EXE=sim.exe
windows: $(OBJECTS)
    $(CC) $(LDFLAGS) $(OBJECTS) -o $(DIR)$(EXE)

all: $(OBJECTS)
    $(CC) $(LDFLAGS) $(OBJECTS) -o $(DIR)$(EXE)

$(DIR)main.o: main.c common.h
    $(CC) $(CFLAGS) main.c -o $(DIR)$@

$(DIR)ui.o: ui.c common.h
    $(CC) $(CFLAGS) ui.c -o $(DIR)$@

$(DIR)parsefile.o: parsefile.c common.h
    $(CC) $(CFLAGS) parsefile.c -o $(DIR)$@

$(DIR)machine.o: machine.c common.h instructions.h
    $(CC) $(CFLAGS) machine.c -o $(DIR)$@

$(DIR)instructions.o: instructions.c instructions.h
    $(CC) $(CFLAGS) instructions.c -o $(DIR)$@

$(DIR)screen.o: screen.c common.h
    $(CC) $(CFLAGS) screen.c -o $(DIR)$@

clean:
    rm *.o
    rm ./windows/*.o
```

It's supposed to let you run 'make all', 'make windows', or 'make clean' to compile the program for Linux, for Windows, or remove the object files.  Running 'make all' works, running 'make clean' works, and running 'make windows' after 'make clean' works, but if I run 'make windows' after 'make all' it doesn't compile new object files.  I assume it's because it's checking the object files as defined originally, without the new value of DIR.  But I tried setting OBJECTS again, with 

```
windows: OBJECTS=$(DIR)main.o $(DIR)ui.o $(DIR)screen.o $(DIR)parsefile.o $(DIR)machine.o $(DIR)instructions.o
``` after setting a new value of DIR and it still doesn't build the object files.  This is the first Makefile I've tried to write, so I'm a little clueless.  Does anyone know how I would accomplish what I'm trying to do?

Any advice is much appreciated :)

---

### Post by MG&amp;TL on 2011-11-17
Tutorial: [http://mrbook.org/tutorials/make/]("http://mrbook.org/tutorials/make/")

For a start, if you leave DIR blank for now, that would be an idea. Makefiles by default use their directory to look for.

---

### Post by Liiiim on 2011-11-17
Thanks, but I've already found that.  It's not really helping with my current issue.  Is there something wrong with how I'm redefining variables for the windows target?  It seems like some of them are being reset but some of them aren't.  I read the [target-specific](http://www.gnu.org/software/make/manual/make.html#Target_002dspecific) variable section of the make guide and I can't figure out what I'm doing differently from the manual (at least when it comes to defining variables in a target).

---

### Post by MG&amp;TL on 2011-11-17
I think it's because you haven't made any changes to the source, and make only recompiles if the source has been changed. I think.

Simple workaround-make it so that the windows target is "make clean" first, then the other stuff (so new object files).

Something like:

```

Windows: clean
Windows: more stuff
      compile here


clean: stuff
     clean here
```

---

### Post by Liiiim on 2011-11-17
I tried that and it works, but I'd rather be able to have both the Windows and Linux executables built at the same time.  Is there not a way to do that?

And thanks for all the help!

---

### Post by MG&amp;TL on 2011-11-17
Back in morning,. ~8hours.

---

### Post by MG&amp;TL on 2011-11-18
> **Liiiim said:**
> I tried that and it works, but I'd rather be able to have both the Windows and Linux executables built at the same time.  Is there not a way to do that?

And thanks for all the help!

How about having separate targets for the build? So windows.o and linux.o?

Bearing in mind that windows typically takes .obj no .o.

And no problem. Intriguing problem you have. :)

---

### Post by Liiiim on 2011-11-18
Alright, I've got it to the point where it works as long as I just build the Windows version before the Linux version, and I think that's good enough for now.

Thanks for the help :)

---

### Post by MG&amp;TL on 2011-11-19
No problem, sorry I couldn't properly solve it.

---

