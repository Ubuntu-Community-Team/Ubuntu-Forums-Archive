---
title: "Compilation error while executing make"
date: 2013-02-14
forum: Packaging and Compiling Programs
---

### Post by koustavpal on 2013-02-14
The compiler being used is gcc and the application i am trying to install is mpiBLAST, well actually its dependencies, halfway through I get this error

gcc -pipe -D_FILE_OFFSET_BITS=64 -D_LARGEFILE64_SOURCE -D_GNU_SOURCE -DNDEBUG -O3 -c  -I../include -I/usr/X11R6/include -L/usr/X11R6/lib -DWIN_MOTIF ncbienv.c
In file included from ncbienv.c:309:0:
/usr/local/include/pwd.h:8:1: error: unknown type name ‘LIST’
ncbienv.c: In function ‘s_GetHomeByUID’:
ncbienv.c:618:19: error: storage size of ‘pwd’ isn’t known
ncbienv.c:633:30: error: dereferencing pointer to incomplete type
ncbienv.c:635:34: error: dereferencing pointer to incomplete type
ncbienv.c: In function ‘s_GetHomeByLOGIN’:
ncbienv.c:648:19: error: storage size of ‘pwd’ isn’t known
ncbienv.c:681:30: error: dereferencing pointer to incomplete type
ncbienv.c:683:34: error: dereferencing pointer to incomplete type
make: *** [ncbienv.o] Error 1

the file being called to is pwd.h

which is in usr/local/include/

this is the file


/* Copyright Vladimir Prus 2002. Distributed under the Boost */
/* Software License, Version 1.0. (See accompanying */
/* file LICENSE_1_0.txt or copy at [http://www.boost.org/LICENSE_1_0.txt](http://www.boost.org/LICENSE_1_0.txt)) */

#ifndef PWD_H
#define PWD_H

LIST * pwd( void );
void   pwd_done( void );

#endif


It would be really helpful if someone can suggest a workaround

---

### Post by schragge on 2013-02-14
Just to be sure, have you applied the patch for newer GCC versions listed on [the download page]("http://www.mpiblast.org/Downloads/Stable")?

---

### Post by oldos2er on 2013-02-14
Moved to Packaging and Compiling Programs.

---

### Post by koustavpal on 2013-02-15
No i haven't, but what I got from that error is that the particular file being called from Boost is calling a function LIST which it cannot access.

I'll apply the patch and see if it works

---

### Post by schragge on 2013-02-15
LIST is not a function, but probably a type declared in one of the header files. I guess the order in which -I options are specified on the gcc command line is significant.

Try to *grep -r --include=\*.h LIST [color=green]/path/to/source[/color]/mpiblast-1.6.0/* to find out where it's being declared.

---

