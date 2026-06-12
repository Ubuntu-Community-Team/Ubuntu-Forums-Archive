---
title: "Using bzip2 in C"
date: 2010-04-10
forum: Programming Talk
---

### Post by sonicbs on 2010-04-10
Hi,
I am stuck and I can't find any help for this problem online.
I am programming in C and I want to use the bzip2 library.
I installed the latest libbz2-dev package from the repositories, and I made sure that I have all the necessary files (the file bzlib.h resides in /usr/include).
I obviously have an ```
#include <bzlib.h>
``` in the beginning of my program, yet any call I make to a library function I get the error:
```
undefined reference to `func_name`
``` I looked at the file bzlib.h and all the library functions I am trying to call are there, spelling's ok and everything.
I am using Anjuta as my IDE, but just to make sure it's not some strange attributes of the project, I compiled the program as clean as I could as follows (I am using threads):
```
gcc -lpthread server.c
```output:
```
The/tmp/cckq4S20.o: In function `thread_file_operations':
server.c:(.text+0x112): undefined reference to `BZ2_bzCompressInit'
server.c:(.text+0x140): undefined reference to `BZ2_bzCompress'
server.c:(.text+0x19f): undefined reference to `BZ2_bzCompressEnd'
collect2: ld returned 1 exit status
```I tried this both on Lucid (Beta 2) and Karmic. Any (and I mean ANY) help would be MUCH MUCH appreciated. Thanks a lot.

---

### Post by Compyx on 2010-04-10
Are you linking against libbz2? Looks like you forgot to link to the library, try adding -lbz2.

---

### Post by sonicbs on 2010-04-10
Compyx, thanks a lot for the very prompt reply!
I think you may have solved my problem.
If I may ask, I did realize it was a linking problem, but I am very (very!) new to programming (and in Linux in particular), could you please explain what does the -lbz2 flag do?
Or more specifically, what is the difference between #include <stdlib.h> (which does not require anything to be added to the compiling command) and #include <bzlib.h> (which apparently seems to require an explicit linking parameter)?

If I am asking too much, just a quick reference to where I can read more about this would be greatly appreciated!
Thanks again for the very quick help!!

---

### Post by Compyx on 2010-04-10
The C standard library doesn't need explicit linking except for the math library, which needs to linked with -lm. The requirement of linking the math library with -lm is historic; it was done to save space in executables.

The '-lbz2' argument tells the linker to link against libbz2. You specify libraries to link against with -l<library_name>, leaving out the 'lib' prefix: so linking against `libfoo' would become '-lfoo'.

Basically anything that's not in the system's C library needs explicit linking.

---

### Post by sonicbs on 2010-04-10
Compyx, thanks again for answering so thoroughly.
Greatly appreciated!

Marked thread as SOLVED.

---

