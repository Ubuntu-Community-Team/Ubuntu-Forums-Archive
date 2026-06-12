---
title: "Distributing source problem..."
date: 2007-01-05
forum: Programming Talk
---

### Post by amiga_os on 2007-01-05
I'm trying to package up my source to distribute something I've written in KDevelop.

It's only depends are SDL and Opengl (using SDL_opengl.h).  It compiles, and runs, fine in KDevelop itself, but when I create a source tarball using "Project->Distribution & Publishing->Source Distribution->Create Source Archive", the tarball KDevelop creates won't compile.

Here's what I get when I try:

```
$ ./configure
configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."
$ make
make: *** No targets specified and no makefile found. Stop.
$ automake
configure.in: no proper invocation of AM_INIT_AUTOMAKE was found.
configure.in: You should verify that configure.in invokes AM_INIT_AUTOMAKE,
configure.in: that aclocal.m4 is present in the top-level directory,
configure.in: and that aclocal.m4 was recently regenerated (using aclocal).
configure.in: required file `./install-sh' not found
configure.in: required file `./missing' not found
src/Makefile.am: required file `./depcomp' not found
/usr/share/automake-1.9/am/depend2.am: am__fastdepCXX does not appear in AM_CONDITIONAL
/usr/share/automake-1.9/am/depend2.am: AMDEP does not appear in AM_CONDITIONAL
 
```

I just went with all the defaults in KDevelop, don't know enough about the build process to know what's wrong.  Any help appreciated!

---

### Post by hod139 on 2007-01-05
I've never used kdevelop for producing source tarball distributions, but just so you know if configure fails don't bother trying to run make.  The error from the configure script is that you are missing the install-sh file, maybe there is a why to tell kdevelop to include that file, but I"m not sure.

---

### Post by amiga_os on 2007-01-06
In that case... can anyone point me to a good FAQ / tutorial on what I need to do to produce a compilable source tarball?

---

### Post by amiga_os on 2007-01-06
Half-way there...

The program compiles fine in KDevelop as either debug, default or optimised.  Distribution & Publishing still doesn't work...

However, it links and some of it compiles if I just copy the whole project directory, cp into it and run ./configure, make.

Everything is fine apart from the OpenGL commands, which the compiler says are 'unrecognised'.  I have no idea why SDL links fine and OpenGL doesn't.  I've even tried changing my #includes from "SDL_opengl.h" to "GL.h" (and GL/GL.h, and every variation possible).  They all compile in KDevelop fine, but on the command line the OpenGL commands aren't recognised.

Anybody have any idea what's wrong?

(PS and my project options include -lGL and -GLU linker flags)

---

