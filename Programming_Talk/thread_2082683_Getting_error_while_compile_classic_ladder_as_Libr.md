---
title: "Getting error while compile classic ladder as Library"
date: 2012-11-10
forum: Programming Talk
---

### Post by thahir1986 on 2012-11-10
Hi,

I got errors while compiling classic ladder as a library

```

ladderlib.c: In function ‘ladder_init’:
ladderlib.c:48: warning: implicit declaration of function ‘VerifyDirectorySelected’
ladderlib.c:51: error: too few arguments to function ‘ClassicLadder_FreeAll’
ladderlib.c:55: warning: implicit declaration of function ‘LoadProjectFiles’
ladderlib.c:55: error: ‘CurrentProjectFileName’ undeclared (first use in this function)
ladderlib.c:55: error: (Each undeclared identifier is reported only once
ladderlib.c:55: error: for each function it appears in.)
ladderlib.c: In function ‘WriteVar’:
ladderlib.c:139: warning: implicit declaration of function ‘RefreshOneBoolVar’
make: *** [ladderlib.o] Error 1



```

---

### Post by mevun on 2012-11-10
My guess is that you're missing some header file.

I would guess that the Makefile has some include path which does not point to the right place.  So look for something like "-I/some/dir" and make sure all of those directories have files in them and/or are valid.  In fact, generally it will be something like "-I${SOME_HOME}/include" and then maybe the SOME_HOME variable is undefined so that when make is run, it is looking for header files it is looking in /include (because the SOME_HOME part becomes blank).

---

### Post by spjackson on 2012-11-10
I'm guessing that you've downloaded it from here [http://sourceforge.net/projects/classicladder/]("http://sourceforge.net/projects/classicladder/") (0.9.006)

I get the same errors from "make classicladder-lib" as you do.

ladderlib.c was last updated 2007-10-28 and it is not compatible with the headers that have been updated recently. The above "make" works with version 0.7.123. I don't know at which point the headers became incompatible with that source or why that source is no longer maintained.

---

