---
title: "undefined reference to 'pthread_create' from linker"
date: 2010-07-07
forum: Programming Talk
---

### Post by CrazyDavy on 2010-07-07
I am having trouble linking the pthread library.
Using Code::Blocks 8.02
I have -lpthread -lm as options for the GNU GCC compiler.

Build Log
------------------------------------------------------------
Compiling: main.c
Compiling: matrix.c
Compiling: newmalloc.c
Linking console executable: bin/Release/optimizer-4
obj/Release/main.o: In function `main':
main.c:(.text+0x132): undefined reference to `pthread_attr_setstacksize'
main.c:(.text+0x224): undefined reference to `pthread_create'
main.c:(.text+0x35b): undefined reference to `pthread_join'
collect2: ld returned 1 exit status
Process terminated with status 1 (0 minutes, 1 seconds)
3 errors
-------------------------------------------------------------
library search:
dlyon@dlyon-desktop2:~$ ls /usr/lib |grep pthread
libgpgme-pthread.so.11
libgpgme-pthread.so.11.7.0
libpthread.a
libpthread_nonshared.a
libpthread.so
dlyon@dlyon-desktop2:~$ 
-------------------------------------------------------------

Any ideas would be greatly appreciated!  Thanks!

---

### Post by dwhitney67 on 2010-07-07
How do you know you are linking with -lpthread?  I can't tell from the information you posted.

Unfortunately this thread boils down to a configuration problem with Code::blocks, something that you could probably have figured out on your own if only you had chosen to learn how to build an application without using an IDE.

If you want to build your application from the command-line (ie from a terminal), go to where your source code resides, and enter the following commands:
```

gcc -c main.c
gcc -c matrix.c
gcc -c newmalloc.c
gcc main.o matrix.o newmalloc.o -lpthread -lm

```

P.S.  If you have header files for matrix.c and newmalloc.c which are not in the same directory as their corresponding .c files, then use the -I compiler option to specify where they are located at.  For example:
```

gcc -I../include -c main.c

```

P.S. #2  Typically libraries (ie pthread and m) are added to LDFLAGS in a Makefile.  Perhaps you can correlate this with whatever Code::Blocks is offering you.

---

### Post by MadCow108 on 2010-07-07
you should also use -pthread instead of -lpthread as that also sets up preprocessor directives suitable for multithreaded programs (e.g. _REENTRANT)

---

### Post by dwhitney67 on 2010-07-07
> **MadCow108 said:**
> you should also use -pthread instead of -lpthread as that also sets up preprocessor directives suitable for multithreaded programs (e.g. _REENTRANT)
I thought the _REENTRANT was a Solaris dependency; not Linux?

I've never had issues with merely using -lpthread for any of my multi-threaded Linux apps.

---

### Post by Wolfgang Griech on 2012-10-09
> **MadCow108 said:**
> you should also use -pthread instead of -lpthread as that also sets up preprocessor directives suitable for multithreaded programs (e.g. _REENTRANT)

thx, at least solved my issue, tried to compile libnodave with gcc under kubuntu 12.04-x64 and got the same error message:

cc -lpthread ibhsim5.o openSocket.o nodave.o -o ibhsim5
ibhsim5.o: In function `main':
ibhsim5.c:(.text+0x372f): undefined reference to `pthread_create'
ibhsim5.c:(.text+0x38a0): undefined reference to `pthread_create'
collect2: ld returned 1 exit status

setting the pthread option as proposed without changing anything else just ran fine:

cc -pthread ibhsim5.o openSocket.o nodave.o -o ibhsim5
cc -Wall -Winline -DLINUX -DDAVE_LITTLE_ENDIAN -fPIC -Wall -Winline -DLINUX -DDAVE_LITTLE_ENDIAN  -c -o isotest4.o isotest4.c

taking the pthread option completely out results in the error..

and the pthread stub is being installed:

wgr@wgr-PB:~/Development/libmodbus/src$ dpkg -l *pthread*
ii  libpthread-stubs0     0.3-3                 pthread stubs not provided by native libc
ii  libpthread-stubs0-dev 0.3-3                 pthread stubs not provided by native libc, development fil

would be interesting to know what the reason for this is..

and btw, am familiar with command line compiling and Makefile.. ;)

---

### Post by MadCow108 on 2012-10-09
the reason is the linker option --as-needed which is default since ubuntu 11.10

with that flag it scans the command line from left to right and drops what is not needed
if you have the library before the object needing it will be dropped as not needed and you get a linker error (similar to how static linking works).
solution:
move all libraries behind the objects needing them.

```
cc  ibhsim5.o openSocket.o nodave.o -o ibhsim5 -lpthread
```

---

### Post by amartya_hatua on 2013-09-10
Let, the name of the program is thread.c Then type the following lines in your command line....
gcc -pthread -c thread.c
gcc -pthread -o th thread.c
./th

---

