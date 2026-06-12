---
title: "Problems configuring gnu-mprf"
date: 2012-06-06
forum: Packaging and Compiling Programs
---

### Post by prasanmouli on 2012-06-06
[FONT=Comic Sans MS][SIZE=2]I've  been installing software packages as a part of developing for the AVR  micro-controllers. In the process, I successfully built and installed  gmp-4.3.2
As a next step, I went on to build mpfr.2.4.2 

My command was like:
[FONT=Courier New]prasan@ubuntu:~/Downloads/mpfr-2.4.2$ ./configure --prefix=/usr/local/AVR[/FONT]
[/SIZE][/FONT][FONT=Comic Sans MS]
But I got an error as follows: [/FONT]
......
[FONT=Courier New]checking for gmp.h... no
configure: error: gmp.h can't be found, or is unusable.
[/FONT]
[FONT=Comic Sans MS]I even checked in the /usr/local/AVR/include[/FONT] directory for a gmp.h file and it was there. 
[FONT=Comic Sans MS]Help me please![/FONT]

---

### Post by prasanmouli on 2012-06-06
[FONT=Comic Sans MS]Well! I googled for some time and found this link really helpful. It solved the problem.
[http://www.opencobol.org/modules/newbb/viewtopic.php?topic_id=1240&forum=1](http://www.opencobol.org/modules/newbb/viewtopic.php?topic_id=1240&forum=1)
CFLAGS were used to set some additional switches and it worked just fine then. No errors. 
[/FONT]
./configure CFLAGS=-I/usr/local/include LDFLAGS=-L/usr/local/lib

[FONT=Comic Sans MS][SIZE=2]The thing is I don't know what LDFLAGS are or what they do. Can someone please help me with this? [/SIZE][/FONT]

---

### Post by MadCow108 on 2012-06-06
CFLAGS are the compiler flags for C, they are passed to gcc
LDFLAGS are linker flags (the linker executable is ld) they are normally also passed to gcc which passes them on to the linker
another important variable is LIBS which sets the libraries to link with (e.g. LIBS=-lxy link with libxy.so)
less important but sometimes used flags are CPPFLAGS for preprocessor flags and CXXFLAGS for c++ flags.

-I sets include search paths
-L sets library search paths
they are required when the files are not in the location the compiler looks by default (/usr/include and /usr/lib)

see the manpages of gcc

---

### Post by prasanmouli on 2012-06-07
> **MadCow108 said:**
> CFLAGS are the compiler flags for C, they are passed to gcc
LDFLAGS are linker flags (the linker executable is ld) they are normally also passed to gcc which passes them on to the linker
another important variable is LIBS which sets the libraries to link with (e.g. LIBS=-lxy link with libxy.so)
less important but sometimes used flags are CPPFLAGS for preprocessor flags and CXXFLAGS for c++ flags.

-I sets include search paths
-L sets library search paths
they are required when the files are not in the location the compiler looks by default (/usr/include and /usr/lib)

see the manpages of gcc

Can you give me an example command that would explain the syntax for using LIBS?

---

