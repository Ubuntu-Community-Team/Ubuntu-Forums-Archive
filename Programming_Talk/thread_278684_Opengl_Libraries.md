---
title: "Opengl Libraries"
date: 2006-10-16
forum: Programming Talk
---

### Post by AngryShaman on 2006-10-16
umm right basically im fairly a n00b with linux

at the mo, im doing a computer science course which involves programming C and opengl in linux.

I've gotten the gcc compiler working on it but i dont know about the opengl libraries

i asked my lecturer and the libraries im after are:=
XII - X Window System
glut - GL utility tool kit
Gl - Graphics language library
Glu - Graphics language utilities
M - Maths

i dunno if these come included with ubuntu or what, as i say im a complete n00b with linux but id like to be able to use it. is there any way to install them/or if you could tell me where they're stored would be great.

---

### Post by duff on 2006-10-16
If you already have gcc, then you have the math library.
```
sudo apt-get install freeglut3-dev
```
will give you glut,glu,gl,and x11

---

### Post by AngryShaman on 2006-10-17
Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
  amsn: Depends: tcltls but it is not installable
  freeglut3-dev: Depends: xlibmesa-gl-dev but it is not installableor
                          libgl-dev
                 Depends: xlibmesa-glu-dev but it is not installableor
                          libglu-dev
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a s olution).


thats what i get when i try that, am i missing some libraries or something?

---

### Post by hod139 on 2006-10-17
To me (and I might be wrong) it looks like you have left over issues from trying to install amsn.

> **AngryShaman said:**
> Reading package lists... Done
Building dependency tree... Done
You might want to run ‘apt-get -f install’ to correct these:
The following packages have unmet dependencies.
**   amsn: Depends: tcltls but it is not installable**
  freeglut3-dev: Depends: xlibmesa-gl-dev but it is not installableor
                          libgl-dev
                 Depends: xlibmesa-glu-dev but it is not installableor
                          libglu-dev
E: Unmet dependencies. Try ‘apt-get -f install’ with no packages (or specify a s olution).


What happens if you try removing amsn and running apt-get -f install?

---

### Post by AngryShaman on 2006-10-18
right, ive actually fixed that problem, the libraries installed fine i think, but, i have a makefile now from my uni linux machines, when i try to use it, it says it cant find -lX11

here it is:
[B]INCDIRS = -I/usr/X11R6/include/ 
LIBDIRS = -L/usr/X11R6/lib -L/usr/local/lib -L/usr/lib     
CC = gcc
CFLAGS = -g $(INCDIRS)
LIBS = -lX11 -lXi   -lglut -lGL -lGLU -lm 
.c.o:
	$(CC) $(INCDIRS) -g -c $*.c -o $*.o

all: firstprog  q2 

clean:
	rm *.o

firstprog: firstprog.o
	$(CC) $(CFLAGS) -o $@ $< $(LIBDIRS) $(LIBS)  

q2: q2.o
	$(CC) $(CFLAGS) -o $@ $< $(LIBDIRS) $(LIBS)  [/B]


i think it may have something to do with the directory of where they r located but i dont know where they are? :/

---

### Post by hod139 on 2006-10-18
Why are you linking against:
[B]-lX11 -lXi
[/B]Unless you explicity are using those libraries, you don't need to link against them.  If you really need those libraries, then you will have to install the packages libx11-dev and libxi-dev

---

