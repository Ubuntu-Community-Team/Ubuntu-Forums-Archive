---
title: "Problem compiling ODE code"
date: 2009-02-06
forum: Packaging and Compiling Programs
---

### Post by gustavocm on 2009-02-06
Hi,

i'm trying to compile an ODE example with this:

```
g++ code.cpp -lode -ldrawstuff -I/home/odin/sources/ode-0.11/include/ -L/home/odin/sources/ode-0.11/drawstuff/src/ -L/home/odin/sources/ode-0.11/ode/src/
```

and i am getting this error:

```
/usr/bin/ld: cannot find -ldrawstuff
collect2: ld returned 1 exit status

```

I guess drawstuff is in the ode-0.11/drawstuff/src directory. Am I missing something?

---

### Post by geraldm on 2009-02-07
There is no need to guess.  Look in that directory and see if the library name exists.  If it is there as libdrawstuff.so.1.0.2 then be sure that there are links to be able to access it: libdrawstuff.so.1 and libdrawstuff.so .
You may also need to access -ldl  which should be in /usr/lib/ or /lib/
Sometimes it is helpful to set the environment variable LD_LIBRARY_PATH to include the library directories.
In the string passed to the compiler, you only need to mention the -L/.. library once, and as a rule, it should preceed the -l.. library that it is to use.

good luck,
Gerald

---

### Post by gustavocm on 2009-02-07
There is no libdrawstuff.so in that directory. There is only libdrawstuff.la, drawstuff.o and drawstuff.lo

Should it have a libdrawstuff.so?

---

### Post by gustavocm on 2009-02-10
I succeeded in compiling the code with this:

```
 g++ code.cpp -lode -lglut -I ~/sources/ode-0.11/include/ ~/sources/ode-0.11/drawstuff/src/drawstuff.o ~/sources/ode-0.11/drawstuff/src/x11.o 
```

---

### Post by Daniel K. O. on 2009-02-11
Just a note: drawstuff is a library created for the sole purpose of compiling the ODE demos. It's buggy, slow, and might just break "compatibility" at any time.

That said, you'll find the libraries hidden in a .libs subdirectory, of both drawstuff and ode/src; that's how libtool works.

---

