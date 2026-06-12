---
title: "Automake using wrong directory"
date: 2008-11-11
forum: Programming Talk
---

### Post by snikrot on 2008-11-11
Hi all, I've a little problem with automake. It seems to try and make an object file (.o) in the wrong directory. After this make fails.

Can somebody tell me what to change to make it work?

Makefile.am
```

LDFLAGS=-lGL -lglut
bin_PROGRAMS = Test

Test_SOURCES =Src/Window/OpenGLWindow.h Src/Window/OpenGLWindow.cpp [COLOR="DarkOrange"]Src/Window/Glut/GlutWindow.cpp [/COLOR]

```

make -d
Which result in the error:
```

GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu
Reading makefiles...
Reading makefile `Makefile'...
Reading makefile `.deps/GlutWindow.Po' (search path) (no ~ expansion)...
Reading makefile `.deps/OpenGLWindow.Po' (search path) (no ~ expansion)...
Updating makefiles....
 Considering target file `.deps/OpenGLWindow.Po'.
  Looking for an implicit rule for `.deps/OpenGLWindow.Po'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/OpenGLWindow.Po.cpp'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/OpenGLWindow.Po.o'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/OpenGLWindow.Po,v'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po,v'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/s.OpenGLWindow.Po'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/SCCS/s.OpenGLWindow.Po'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/OpenGLWindow.Po.cpp'.
  Looking for a rule with intermediate file `.deps/OpenGLWindow.Po.cpp'.
   Avoiding implicit rule recursion.
   Trying pattern rule with stem `OpenGLWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/OpenGLWindow.Po.cpp,v'.
   Trying pattern rule with stem `OpenGLWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po.cpp,v'.
   Trying pattern rule with stem `OpenGLWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po.cpp'.
   Trying pattern rule with stem `OpenGLWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/s.OpenGLWindow.Po.cpp'.
   Trying pattern rule with stem `OpenGLWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/SCCS/s.OpenGLWindow.Po.cpp'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/OpenGLWindow.Po.o'.
  Looking for a rule with intermediate file `.deps/OpenGLWindow.Po.o'.
   Avoiding implicit rule recursion.
   Trying pattern rule with stem `OpenGLWindow.Po'.
   Rejecting impossible implicit prerequisite `.deps/OpenGLWindow.Po.cpp'.
   Trying pattern rule with stem `OpenGLWindow.Po.o'.
   Trying implicit prerequisite `.deps/OpenGLWindow.Po.o,v'.
   Trying pattern rule with stem `OpenGLWindow.Po.o'.
   Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po.o,v'.
   Trying pattern rule with stem `OpenGLWindow.Po.o'.
   Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po.o'.
   Trying pattern rule with stem `OpenGLWindow.Po.o'.
   Trying implicit prerequisite `.deps/s.OpenGLWindow.Po.o'.
   Trying pattern rule with stem `OpenGLWindow.Po.o'.
   Trying implicit prerequisite `.deps/SCCS/s.OpenGLWindow.Po.o'.
  No implicit rule found for `.deps/OpenGLWindow.Po'.
  Finished prerequisites of target file `.deps/OpenGLWindow.Po'.
 No need to remake target `.deps/OpenGLWindow.Po'.
 Considering target file `.deps/GlutWindow.Po'.
  Looking for an implicit rule for `.deps/GlutWindow.Po'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/GlutWindow.Po.cpp'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/GlutWindow.Po.o'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/GlutWindow.Po,v'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/RCS/GlutWindow.Po,v'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/RCS/GlutWindow.Po'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/s.GlutWindow.Po'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/SCCS/s.GlutWindow.Po'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/GlutWindow.Po.cpp'.
  Looking for a rule with intermediate file `.deps/GlutWindow.Po.cpp'.
   Avoiding implicit rule recursion.
   Trying pattern rule with stem `GlutWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/GlutWindow.Po.cpp,v'.
   Trying pattern rule with stem `GlutWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/RCS/GlutWindow.Po.cpp,v'.
   Trying pattern rule with stem `GlutWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/RCS/GlutWindow.Po.cpp'.
   Trying pattern rule with stem `GlutWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/s.GlutWindow.Po.cpp'.
   Trying pattern rule with stem `GlutWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/SCCS/s.GlutWindow.Po.cpp'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/GlutWindow.Po.o'.
  Looking for a rule with intermediate file `.deps/GlutWindow.Po.o'.
   Avoiding implicit rule recursion.
   Trying pattern rule with stem `GlutWindow.Po'.
   Rejecting impossible implicit prerequisite `.deps/GlutWindow.Po.cpp'.
   Trying pattern rule with stem `GlutWindow.Po.o'.
   Trying implicit prerequisite `.deps/GlutWindow.Po.o,v'.
   Trying pattern rule with stem `GlutWindow.Po.o'.
   Trying implicit prerequisite `.deps/RCS/GlutWindow.Po.o,v'.
   Trying pattern rule with stem `GlutWindow.Po.o'.
   Trying implicit prerequisite `.deps/RCS/GlutWindow.Po.o'.
   Trying pattern rule with stem `GlutWindow.Po.o'.
   Trying implicit prerequisite `.deps/s.GlutWindow.Po.o'.
   Trying pattern rule with stem `GlutWindow.Po.o'.
   Trying implicit prerequisite `.deps/SCCS/s.GlutWindow.Po.o'.
  No implicit rule found for `.deps/GlutWindow.Po'.
  Finished prerequisites of target file `.deps/GlutWindow.Po'.
 No need to remake target `.deps/GlutWindow.Po'.
 Considering target file `Makefile'.
   Considering target file `Makefile.in'.
     Considering target file `Makefile.am'.
      Looking for an implicit rule for `Makefile.am'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `Makefile.am.cpp'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `Makefile.am.o'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `Makefile.am,v'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `RCS/Makefile.am,v'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `RCS/Makefile.am'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `s.Makefile.am'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `SCCS/s.Makefile.am'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `Makefile.am.cpp'.
      Looking for a rule with intermediate file `Makefile.am.cpp'.
       Avoiding implicit rule recursion.
       Trying pattern rule with stem `Makefile.am.cpp'.
       Trying implicit prerequisite `Makefile.am.cpp,v'.
       Trying pattern rule with stem `Makefile.am.cpp'.
       Trying implicit prerequisite `RCS/Makefile.am.cpp,v'.
       Trying pattern rule with stem `Makefile.am.cpp'.
       Trying implicit prerequisite `RCS/Makefile.am.cpp'.
       Trying pattern rule with stem `Makefile.am.cpp'.
       Trying implicit prerequisite `s.Makefile.am.cpp'.
       Trying pattern rule with stem `Makefile.am.cpp'.
       Trying implicit prerequisite `SCCS/s.Makefile.am.cpp'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `Makefile.am.o'.
      Looking for a rule with intermediate file `Makefile.am.o'.
       Avoiding implicit rule recursion.
       Trying pattern rule with stem `Makefile.am'.
       Rejecting impossible implicit prerequisite `Makefile.am.cpp'.
       Trying pattern rule with stem `Makefile.am.o'.
       Trying implicit prerequisite `Makefile.am.o,v'.
       Trying pattern rule with stem `Makefile.am.o'.
       Trying implicit prerequisite `RCS/Makefile.am.o,v'.
       Trying pattern rule with stem `Makefile.am.o'.
       Trying implicit prerequisite `RCS/Makefile.am.o'.
       Trying pattern rule with stem `Makefile.am.o'.
       Trying implicit prerequisite `s.Makefile.am.o'.
       Trying pattern rule with stem `Makefile.am.o'.
       Trying implicit prerequisite `SCCS/s.Makefile.am.o'.
      No implicit rule found for `Makefile.am'.
      Finished prerequisites of target file `Makefile.am'.
     No need to remake target `Makefile.am'.
     Considering target file `configure.ac'.
      Looking for an implicit rule for `configure.ac'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `configure.ac.cpp'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `configure.ac.o'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `configure.ac,v'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `RCS/configure.ac,v'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `RCS/configure.ac'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `s.configure.ac'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `SCCS/s.configure.ac'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `configure.ac.cpp'.
      Looking for a rule with intermediate file `configure.ac.cpp'.
       Avoiding implicit rule recursion.
       Trying pattern rule with stem `configure.ac.cpp'.
       Trying implicit prerequisite `configure.ac.cpp,v'.
       Trying pattern rule with stem `configure.ac.cpp'.
       Trying implicit prerequisite `RCS/configure.ac.cpp,v'.
       Trying pattern rule with stem `configure.ac.cpp'.
       Trying implicit prerequisite `RCS/configure.ac.cpp'.
       Trying pattern rule with stem `configure.ac.cpp'.
       Trying implicit prerequisite `s.configure.ac.cpp'.
       Trying pattern rule with stem `configure.ac.cpp'.
       Trying implicit prerequisite `SCCS/s.configure.ac.cpp'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `configure.ac.o'.
      Looking for a rule with intermediate file `configure.ac.o'.
       Avoiding implicit rule recursion.
       Trying pattern rule with stem `configure.ac'.
       Rejecting impossible implicit prerequisite `configure.ac.cpp'.
       Trying pattern rule with stem `configure.ac.o'.
       Trying implicit prerequisite `configure.ac.o,v'.
       Trying pattern rule with stem `configure.ac.o'.
       Trying implicit prerequisite `RCS/configure.ac.o,v'.
       Trying pattern rule with stem `configure.ac.o'.
       Trying implicit prerequisite `RCS/configure.ac.o'.
       Trying pattern rule with stem `configure.ac.o'.
       Trying implicit prerequisite `s.configure.ac.o'.
       Trying pattern rule with stem `configure.ac.o'.
       Trying implicit prerequisite `SCCS/s.configure.ac.o'.
      No implicit rule found for `configure.ac'.
      Finished prerequisites of target file `configure.ac'.
     No need to remake target `configure.ac'.
     Considering target file `aclocal.m4'.
       Pruning file `configure.ac'.
      Finished prerequisites of target file `aclocal.m4'.
      Prerequisite `configure.ac' is older than target `aclocal.m4'.
     No need to remake target `aclocal.m4'.
    Finished prerequisites of target file `Makefile.in'.
    Prerequisite `Makefile.am' is older than target `Makefile.in'.
    Prerequisite `configure.ac' is older than target `Makefile.in'.
    Prerequisite `aclocal.m4' is older than target `Makefile.in'.
   No need to remake target `Makefile.in'.
   Considering target file `config.status'.
     Considering target file `configure'.
       Pruning file `configure.ac'.
       Pruning file `aclocal.m4'.
      Finished prerequisites of target file `configure'.
      Prerequisite `configure.ac' is older than target `configure'.
      Prerequisite `aclocal.m4' is older than target `configure'.
     No need to remake target `configure'.
    Finished prerequisites of target file `config.status'.
    Prerequisite `configure' is older than target `config.status'.
   No need to remake target `config.status'.
  Finished prerequisites of target file `Makefile'.
  Prerequisite `Makefile.in' is older than target `Makefile'.
  Prerequisite `config.status' is older than target `Makefile'.
 No need to remake target `Makefile'.
Updating goal targets....
Considering target file `all'.
 File `all' does not exist.
  Considering target file `config.h'.
    Considering target file `stamp-h1'.
      Considering target file `config.h.in'.
        Pruning file `configure.ac'.
        Pruning file `aclocal.m4'.
       Finished prerequisites of target file `config.h.in'.
       Prerequisite `configure.ac' is older than target `config.h.in'.
       Prerequisite `aclocal.m4' is older than target `config.h.in'.
      No need to remake target `config.h.in'.
      Pruning file `config.status'.
     Finished prerequisites of target file `stamp-h1'.
     Prerequisite `config.h.in' is older than target `stamp-h1'.
     Prerequisite `config.status' is older than target `stamp-h1'.
    No need to remake target `stamp-h1'.
   Finished prerequisites of target file `config.h'.
   Prerequisite `stamp-h1' is newer than target `config.h'.
  Must remake target `config.h'.
Putting child 0x08087710 (config.h) PID 18634 on the chain.
Live child 0x08087710 (config.h) PID 18634 
Reaping winning child 0x08087710 PID 18634 
Removing child 0x08087710 PID 18634 from chain.
  Successfully remade target file `config.h'.
 Finished prerequisites of target file `all'.
Must remake target `all'.
make  all-am
Putting child 0x08081bd0 (all) PID 18635 on the chain.
Live child 0x08081bd0 (all) PID 18635 
GNU Make 3.81
Copyright (C) 2006  Free Software Foundation, Inc.
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.

This program built for i486-pc-linux-gnu
Reading makefiles...
Reading makefile `Makefile'...
Reading makefile `.deps/GlutWindow.Po' (search path) (no ~ expansion)...
Reading makefile `.deps/OpenGLWindow.Po' (search path) (no ~ expansion)...
Updating makefiles....
 Considering target file `.deps/OpenGLWindow.Po'.
  Looking for an implicit rule for `.deps/OpenGLWindow.Po'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/OpenGLWindow.Po.cpp'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/OpenGLWindow.Po.o'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/OpenGLWindow.Po,v'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po,v'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/s.OpenGLWindow.Po'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/SCCS/s.OpenGLWindow.Po'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/OpenGLWindow.Po.cpp'.
  Looking for a rule with intermediate file `.deps/OpenGLWindow.Po.cpp'.
   Avoiding implicit rule recursion.
   Trying pattern rule with stem `OpenGLWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/OpenGLWindow.Po.cpp,v'.
   Trying pattern rule with stem `OpenGLWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po.cpp,v'.
   Trying pattern rule with stem `OpenGLWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po.cpp'.
   Trying pattern rule with stem `OpenGLWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/s.OpenGLWindow.Po.cpp'.
   Trying pattern rule with stem `OpenGLWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/SCCS/s.OpenGLWindow.Po.cpp'.
  Trying pattern rule with stem `OpenGLWindow.Po'.
  Trying implicit prerequisite `.deps/OpenGLWindow.Po.o'.
  Looking for a rule with intermediate file `.deps/OpenGLWindow.Po.o'.
   Avoiding implicit rule recursion.
   Trying pattern rule with stem `OpenGLWindow.Po'.
   Rejecting impossible implicit prerequisite `.deps/OpenGLWindow.Po.cpp'.
   Trying pattern rule with stem `OpenGLWindow.Po.o'.
   Trying implicit prerequisite `.deps/OpenGLWindow.Po.o,v'.
   Trying pattern rule with stem `OpenGLWindow.Po.o'.
   Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po.o,v'.
   Trying pattern rule with stem `OpenGLWindow.Po.o'.
   Trying implicit prerequisite `.deps/RCS/OpenGLWindow.Po.o'.
   Trying pattern rule with stem `OpenGLWindow.Po.o'.
   Trying implicit prerequisite `.deps/s.OpenGLWindow.Po.o'.
   Trying pattern rule with stem `OpenGLWindow.Po.o'.
   Trying implicit prerequisite `.deps/SCCS/s.OpenGLWindow.Po.o'.
  No implicit rule found for `.deps/OpenGLWindow.Po'.
  Finished prerequisites of target file `.deps/OpenGLWindow.Po'.
 No need to remake target `.deps/OpenGLWindow.Po'.
 Considering target file `.deps/GlutWindow.Po'.
  Looking for an implicit rule for `.deps/GlutWindow.Po'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/GlutWindow.Po.cpp'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/GlutWindow.Po.o'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/GlutWindow.Po,v'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/RCS/GlutWindow.Po,v'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/RCS/GlutWindow.Po'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/s.GlutWindow.Po'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/SCCS/s.GlutWindow.Po'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/GlutWindow.Po.cpp'.
  Looking for a rule with intermediate file `.deps/GlutWindow.Po.cpp'.
   Avoiding implicit rule recursion.
   Trying pattern rule with stem `GlutWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/GlutWindow.Po.cpp,v'.
   Trying pattern rule with stem `GlutWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/RCS/GlutWindow.Po.cpp,v'.
   Trying pattern rule with stem `GlutWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/RCS/GlutWindow.Po.cpp'.
   Trying pattern rule with stem `GlutWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/s.GlutWindow.Po.cpp'.
   Trying pattern rule with stem `GlutWindow.Po.cpp'.
   Trying implicit prerequisite `.deps/SCCS/s.GlutWindow.Po.cpp'.
  Trying pattern rule with stem `GlutWindow.Po'.
  Trying implicit prerequisite `.deps/GlutWindow.Po.o'.
  Looking for a rule with intermediate file `.deps/GlutWindow.Po.o'.
   Avoiding implicit rule recursion.
   Trying pattern rule with stem `GlutWindow.Po'.
   Rejecting impossible implicit prerequisite `.deps/GlutWindow.Po.cpp'.
   Trying pattern rule with stem `GlutWindow.Po.o'.
   Trying implicit prerequisite `.deps/GlutWindow.Po.o,v'.
   Trying pattern rule with stem `GlutWindow.Po.o'.
   Trying implicit prerequisite `.deps/RCS/GlutWindow.Po.o,v'.
   Trying pattern rule with stem `GlutWindow.Po.o'.
   Trying implicit prerequisite `.deps/RCS/GlutWindow.Po.o'.
   Trying pattern rule with stem `GlutWindow.Po.o'.
   Trying implicit prerequisite `.deps/s.GlutWindow.Po.o'.
   Trying pattern rule with stem `GlutWindow.Po.o'.
   Trying implicit prerequisite `.deps/SCCS/s.GlutWindow.Po.o'.
  No implicit rule found for `.deps/GlutWindow.Po'.
  Finished prerequisites of target file `.deps/GlutWindow.Po'.
 No need to remake target `.deps/GlutWindow.Po'.
 Considering target file `Makefile'.
   Considering target file `Makefile.in'.
     Considering target file `Makefile.am'.
      Looking for an implicit rule for `Makefile.am'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `Makefile.am.cpp'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `Makefile.am.o'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `Makefile.am,v'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `RCS/Makefile.am,v'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `RCS/Makefile.am'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `s.Makefile.am'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `SCCS/s.Makefile.am'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `Makefile.am.cpp'.
      Looking for a rule with intermediate file `Makefile.am.cpp'.
       Avoiding implicit rule recursion.
       Trying pattern rule with stem `Makefile.am.cpp'.
       Trying implicit prerequisite `Makefile.am.cpp,v'.
       Trying pattern rule with stem `Makefile.am.cpp'.
       Trying implicit prerequisite `RCS/Makefile.am.cpp,v'.
       Trying pattern rule with stem `Makefile.am.cpp'.
       Trying implicit prerequisite `RCS/Makefile.am.cpp'.
       Trying pattern rule with stem `Makefile.am.cpp'.
       Trying implicit prerequisite `s.Makefile.am.cpp'.
       Trying pattern rule with stem `Makefile.am.cpp'.
       Trying implicit prerequisite `SCCS/s.Makefile.am.cpp'.
      Trying pattern rule with stem `Makefile.am'.
      Trying implicit prerequisite `Makefile.am.o'.
      Looking for a rule with intermediate file `Makefile.am.o'.
       Avoiding implicit rule recursion.
       Trying pattern rule with stem `Makefile.am'.
       Rejecting impossible implicit prerequisite `Makefile.am.cpp'.
       Trying pattern rule with stem `Makefile.am.o'.
       Trying implicit prerequisite `Makefile.am.o,v'.
       Trying pattern rule with stem `Makefile.am.o'.
       Trying implicit prerequisite `RCS/Makefile.am.o,v'.
       Trying pattern rule with stem `Makefile.am.o'.
       Trying implicit prerequisite `RCS/Makefile.am.o'.
       Trying pattern rule with stem `Makefile.am.o'.
       Trying implicit prerequisite `s.Makefile.am.o'.
       Trying pattern rule with stem `Makefile.am.o'.
       Trying implicit prerequisite `SCCS/s.Makefile.am.o'.
      No implicit rule found for `Makefile.am'.
      Finished prerequisites of target file `Makefile.am'.
     No need to remake target `Makefile.am'.
     Considering target file `configure.ac'.
      Looking for an implicit rule for `configure.ac'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `configure.ac.cpp'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `configure.ac.o'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `configure.ac,v'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `RCS/configure.ac,v'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `RCS/configure.ac'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `s.configure.ac'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `SCCS/s.configure.ac'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `configure.ac.cpp'.
      Looking for a rule with intermediate file `configure.ac.cpp'.
       Avoiding implicit rule recursion.
       Trying pattern rule with stem `configure.ac.cpp'.
       Trying implicit prerequisite `configure.ac.cpp,v'.
       Trying pattern rule with stem `configure.ac.cpp'.
       Trying implicit prerequisite `RCS/configure.ac.cpp,v'.
       Trying pattern rule with stem `configure.ac.cpp'.
       Trying implicit prerequisite `RCS/configure.ac.cpp'.
       Trying pattern rule with stem `configure.ac.cpp'.
       Trying implicit prerequisite `s.configure.ac.cpp'.
       Trying pattern rule with stem `configure.ac.cpp'.
       Trying implicit prerequisite `SCCS/s.configure.ac.cpp'.
      Trying pattern rule with stem `configure.ac'.
      Trying implicit prerequisite `configure.ac.o'.
      Looking for a rule with intermediate file `configure.ac.o'.
       Avoiding implicit rule recursion.
       Trying pattern rule with stem `configure.ac'.
       Rejecting impossible implicit prerequisite `configure.ac.cpp'.
       Trying pattern rule with stem `configure.ac.o'.
       Trying implicit prerequisite `configure.ac.o,v'.
       Trying pattern rule with stem `configure.ac.o'.
       Trying implicit prerequisite `RCS/configure.ac.o,v'.
       Trying pattern rule with stem `configure.ac.o'.
       Trying implicit prerequisite `RCS/configure.ac.o'.
       Trying pattern rule with stem `configure.ac.o'.
       Trying implicit prerequisite `s.configure.ac.o'.
       Trying pattern rule with stem `configure.ac.o'.
       Trying implicit prerequisite `SCCS/s.configure.ac.o'.
      No implicit rule found for `configure.ac'.
      Finished prerequisites of target file `configure.ac'.
     No need to remake target `configure.ac'.
     Considering target file `aclocal.m4'.
       Pruning file `configure.ac'.
      Finished prerequisites of target file `aclocal.m4'.
      Prerequisite `configure.ac' is older than target `aclocal.m4'.
     No need to remake target `aclocal.m4'.
    Finished prerequisites of target file `Makefile.in'.
    Prerequisite `Makefile.am' is older than target `Makefile.in'.
    Prerequisite `configure.ac' is older than target `Makefile.in'.
    Prerequisite `aclocal.m4' is older than target `Makefile.in'.
   No need to remake target `Makefile.in'.
   Considering target file `config.status'.
     Considering target file `configure'.
       Pruning file `configure.ac'.
       Pruning file `aclocal.m4'.
      Finished prerequisites of target file `configure'.
      Prerequisite `configure.ac' is older than target `configure'.
      Prerequisite `aclocal.m4' is older than target `configure'.
     No need to remake target `configure'.
    Finished prerequisites of target file `config.status'.
    Prerequisite `configure' is older than target `config.status'.
   No need to remake target `config.status'.
  Finished prerequisites of target file `Makefile'.
  Prerequisite `Makefile.in' is older than target `Makefile'.
  Prerequisite `config.status' is older than target `Makefile'.
 No need to remake target `Makefile'.
Updating goal targets....
Considering target file `all-am'.
 File `all-am' does not exist.
  Pruning file `Makefile'.
  Considering target file `Test'.
   File `Test' does not exist.
    Considering target file `OpenGLWindow.o'.
     Looking for an implicit rule for `OpenGLWindow.o'.
     Trying pattern rule with stem `OpenGLWindow'.
     Trying implicit prerequisite `OpenGLWindow.cpp'.
     Trying pattern rule with stem `OpenGLWindow.o'.
     Trying implicit prerequisite `OpenGLWindow.o,v'.
     Trying pattern rule with stem `OpenGLWindow.o'.
     Trying implicit prerequisite `RCS/OpenGLWindow.o,v'.
     Trying pattern rule with stem `OpenGLWindow.o'.
     Trying implicit prerequisite `RCS/OpenGLWindow.o'.
     Trying pattern rule with stem `OpenGLWindow.o'.
     Trying implicit prerequisite `s.OpenGLWindow.o'.
     Trying pattern rule with stem `OpenGLWindow.o'.
     Trying implicit prerequisite `SCCS/s.OpenGLWindow.o'.
     Trying pattern rule with stem `OpenGLWindow'.
     Trying implicit prerequisite `OpenGLWindow.cpp'.
     Looking for a rule with intermediate file `OpenGLWindow.cpp'.
      Avoiding implicit rule recursion.
      Trying pattern rule with stem `OpenGLWindow.cpp'.
      Trying implicit prerequisite `OpenGLWindow.cpp,v'.
      Trying pattern rule with stem `OpenGLWindow.cpp'.
      Trying implicit prerequisite `RCS/OpenGLWindow.cpp,v'.
      Trying pattern rule with stem `OpenGLWindow.cpp'.
      Trying implicit prerequisite `RCS/OpenGLWindow.cpp'.
      Trying pattern rule with stem `OpenGLWindow.cpp'.
      Trying implicit prerequisite `s.OpenGLWindow.cpp'.
      Trying pattern rule with stem `OpenGLWindow.cpp'.
      Trying implicit prerequisite `SCCS/s.OpenGLWindow.cpp'.
     No implicit rule found for `OpenGLWindow.o'.
      Considering target file `Src/Window/OpenGLWindow.cpp'.
       Looking for an implicit rule for `Src/Window/OpenGLWindow.cpp'.
       Trying pattern rule with stem `OpenGLWindow.cpp'.
       Trying implicit prerequisite `Src/Window/OpenGLWindow.cpp,v'.
       Trying pattern rule with stem `OpenGLWindow.cpp'.
       Trying implicit prerequisite `Src/Window/RCS/OpenGLWindow.cpp,v'.
       Trying pattern rule with stem `OpenGLWindow.cpp'.
       Trying implicit prerequisite `Src/Window/RCS/OpenGLWindow.cpp'.
       Trying pattern rule with stem `OpenGLWindow.cpp'.
       Trying implicit prerequisite `Src/Window/s.OpenGLWindow.cpp'.
       Trying pattern rule with stem `OpenGLWindow.cpp'.
       Trying implicit prerequisite `Src/Window/SCCS/s.OpenGLWindow.cpp'.
       No implicit rule found for `Src/Window/OpenGLWindow.cpp'.
       Finished prerequisites of target file `Src/Window/OpenGLWindow.cpp'.
      No need to remake target `Src/Window/OpenGLWindow.cpp'.
      Considering target file `Src/Window/OpenGLWindow.h'.
       Looking for an implicit rule for `Src/Window/OpenGLWindow.h'.
       Trying pattern rule with stem `OpenGLWindow.h'.
       Trying implicit prerequisite `Src/Window/OpenGLWindow.h.cpp'.
       Trying pattern rule with stem `OpenGLWindow.h'.
       Trying implicit prerequisite `Src/Window/OpenGLWindow.h.o'.
       Trying pattern rule with stem `OpenGLWindow.h'.
       Trying implicit prerequisite `Src/Window/OpenGLWindow.h,v'.
       Trying pattern rule with stem `OpenGLWindow.h'.
       Trying implicit prerequisite `Src/Window/RCS/OpenGLWindow.h,v'.
       Trying pattern rule with stem `OpenGLWindow.h'.
       Trying implicit prerequisite `Src/Window/RCS/OpenGLWindow.h'.
       Trying pattern rule with stem `OpenGLWindow.h'.
       Trying implicit prerequisite `Src/Window/s.OpenGLWindow.h'.
       Trying pattern rule with stem `OpenGLWindow.h'.
       Trying implicit prerequisite `Src/Window/SCCS/s.OpenGLWindow.h'.
       Trying pattern rule with stem `OpenGLWindow.h'.
       Trying implicit prerequisite `Src/Window/OpenGLWindow.h.cpp'.
       Looking for a rule with intermediate file `Src/Window/OpenGLWindow.h.cpp'.
        Avoiding implicit rule recursion.
        Trying pattern rule with stem `OpenGLWindow.h.cpp'.
        Trying implicit prerequisite `Src/Window/OpenGLWindow.h.cpp,v'.
        Trying pattern rule with stem `OpenGLWindow.h.cpp'.
        Trying implicit prerequisite `Src/Window/RCS/OpenGLWindow.h.cpp,v'.
        Trying pattern rule with stem `OpenGLWindow.h.cpp'.
        Trying implicit prerequisite `Src/Window/RCS/OpenGLWindow.h.cpp'.
        Trying pattern rule with stem `OpenGLWindow.h.cpp'.
        Trying implicit prerequisite `Src/Window/s.OpenGLWindow.h.cpp'.
        Trying pattern rule with stem `OpenGLWindow.h.cpp'.
        Trying implicit prerequisite `Src/Window/SCCS/s.OpenGLWindow.h.cpp'.
       Trying pattern rule with stem `OpenGLWindow.h'.
       Trying implicit prerequisite `Src/Window/OpenGLWindow.h.o'.
       Looking for a rule with intermediate file `Src/Window/OpenGLWindow.h.o'.
        Avoiding implicit rule recursion.
        Trying pattern rule with stem `OpenGLWindow.h'.
        Rejecting impossible implicit prerequisite `Src/Window/OpenGLWindow.h.cpp'.
        Trying pattern rule with stem `OpenGLWindow.h.o'.
        Trying implicit prerequisite `Src/Window/OpenGLWindow.h.o,v'.
        Trying pattern rule with stem `OpenGLWindow.h.o'.
        Trying implicit prerequisite `Src/Window/RCS/OpenGLWindow.h.o,v'.
        Trying pattern rule with stem `OpenGLWindow.h.o'.
        Trying implicit prerequisite `Src/Window/RCS/OpenGLWindow.h.o'.
        Trying pattern rule with stem `OpenGLWindow.h.o'.
        Trying implicit prerequisite `Src/Window/s.OpenGLWindow.h.o'.
        Trying pattern rule with stem `OpenGLWindow.h.o'.
        Trying implicit prerequisite `Src/Window/SCCS/s.OpenGLWindow.h.o'.
       No implicit rule found for `Src/Window/OpenGLWindow.h'.
       Finished prerequisites of target file `Src/Window/OpenGLWindow.h'.
      No commands for `Src/Window/OpenGLWindow.h' and no prerequisites actually changed.
      No need to remake target `Src/Window/OpenGLWindow.h'.
      Pruning file `Src/Window/OpenGLWindow.cpp'.
      Pruning file `Src/Window/OpenGLWindow.h'.
     Finished prerequisites of target file `OpenGLWindow.o'.
     Prerequisite `Src/Window/OpenGLWindow.cpp' is older than target `OpenGLWindow.o'.
     Prerequisite `Src/Window/OpenGLWindow.h' is older than target `OpenGLWindow.o'.
     Prerequisite `Src/Window/OpenGLWindow.cpp' is older than target `OpenGLWindow.o'.
     Prerequisite `Src/Window/OpenGLWindow.h' is older than target `OpenGLWindow.o'.
    No commands for `OpenGLWindow.o' and no prerequisites actually changed.
    No need to remake target `OpenGLWindow.o'.
    Considering target file `GlutWindow.o'.
     File `GlutWindow.o' does not exist.
     Looking for an implicit rule for `GlutWindow.o'.
     Trying pattern rule with stem `GlutWindow'.
     Trying implicit prerequisite `GlutWindow.cpp'.
     Trying pattern rule with stem `GlutWindow.o'.
     Trying implicit prerequisite `GlutWindow.o,v'.
     Trying pattern rule with stem `GlutWindow.o'.
     Trying implicit prerequisite `RCS/GlutWindow.o,v'.
     Trying pattern rule with stem `GlutWindow.o'.
     Trying implicit prerequisite `RCS/GlutWindow.o'.
     Trying pattern rule with stem `GlutWindow.o'.
     Trying implicit prerequisite `s.GlutWindow.o'.
     Trying pattern rule with stem `GlutWindow.o'.
     Trying implicit prerequisite `SCCS/s.GlutWindow.o'.
     Trying pattern rule with stem `GlutWindow'.
     Trying implicit prerequisite `GlutWindow.cpp'.
     Looking for a rule with intermediate file `GlutWindow.cpp'.
      Avoiding implicit rule recursion.
      Trying pattern rule with stem `GlutWindow.cpp'.
      Trying implicit prerequisite `GlutWindow.cpp,v'.
      Trying pattern rule with stem `GlutWindow.cpp'.
      Trying implicit prerequisite `RCS/GlutWindow.cpp,v'.
      Trying pattern rule with stem `GlutWindow.cpp'.
      Trying implicit prerequisite `RCS/GlutWindow.cpp'.
      Trying pattern rule with stem `GlutWindow.cpp'.
      Trying implicit prerequisite `s.GlutWindow.cpp'.
      Trying pattern rule with stem `GlutWindow.cpp'.
      Trying implicit prerequisite `SCCS/s.GlutWindow.cpp'.
     No implicit rule found for `GlutWindow.o'.
      Considering target file `Src/Window/GlutWindow.cpp'.
       [COLOR="Red"]File `Src/Window/GlutWindow.cpp' does not exist.[/COLOR]
       Looking for an implicit rule for `Src/Window/GlutWindow.cpp'.
       Trying pattern rule with stem `GlutWindow.cpp'.
       Trying implicit prerequisite `Src/Window/GlutWindow.cpp,v'.
       Trying pattern rule with stem `GlutWindow.cpp'.
       Trying implicit prerequisite `Src/Window/RCS/GlutWindow.cpp,v'.
       Trying pattern rule with stem `GlutWindow.cpp'.
       Trying implicit prerequisite `Src/Window/RCS/GlutWindow.cpp'.
       Trying pattern rule with stem `GlutWindow.cpp'.
       Trying implicit prerequisite `Src/Window/s.GlutWindow.cpp'.
       Trying pattern rule with stem `GlutWindow.cpp'.
       Trying implicit prerequisite `Src/Window/SCCS/s.GlutWindow.cpp'.
       No implicit rule found for `Src/Window/GlutWindow.cpp'.
       Finished prerequisites of target file `Src/Window/GlutWindow.cpp'.
[COLOR="Red"]      Must remake target `Src/Window/GlutWindow.cpp'.[/COLOR]
make[1]: Entering directory `/mnt/data/java/workspace/Test'
make[1]: Leaving directory `/mnt/data/java/workspace/Test'
Reaping losing child 0x08081bd0 PID 18635 
Removing child 0x08081bd0 PID 18635 from chain.

```

---

