---
title: "Using external C++ libs, how?"
date: 2008-05-29
forum: Programming Talk
---

### Post by jonface on 2008-05-29
Using external Java libs I understand, just get some lib .jar file, place in classpath and when you compile your program, BAM, it works.

But C++? I'm trying to use [http://www.datareel.com/download.htm](http://www.datareel.com/download.htm) but I don't get it.

I followed the instructions, did a "make -f linux.mak" (it comes with various make files for different archs) and it did it's thing, made a .so file and the .a file but now what? The examples were compiled during this process but how would I go about now using this library myself? If I try using in a cpp program,

#include "gxdlcode.h"

it's not going to work and doesn't, fair enough, how does the compiler know where to find the file. Then again, how does it know where to find something like <iostream> for example? This part shouldn't be the hardest, surely the coding should be!

Thanks for any help or advice.

BTW I'm using Ubuntu 8.04.


Extract from README
-----------------------
The UNIX makefiles require you to build the UNIX static/shared libraries located in the unixlib subdirectory. To build the library using the UNIX make utility execute the following command for one of the supported UNIX platforms:

% make -f linux.mak <--- used this
% make -f solaris.mak
% make -f hpux10.mak
% make -f hpux11.mak

This will generate the "libgxcode.a" static 32-bit library and the "libgxcode.so.4.X" shared 32-bit library.

---

### Post by issih on 2008-05-29
never used anything other than the standard libraries for quite some time, but if I remember rightly you have to tell the compiler to look in the directory where they are with a -I <dir> flag.

Basically tells the compiler to look in that directory for includes.

Not sure how well that works with compiled libraries...anyone else want to weigh in on that?

---

### Post by dwhitney67 on 2008-05-30
To link with external libraries, the two important GCC options that come to mind are the '-L' and the '-l'.

The '-L' is used to specify the path of where the library of interest resides.

The '-l' is used to specify the name of the library, minus the 'lib' and the file extension parts.

So, for example, if you wanted to compile a file with the name of "MyProg.cpp", with a library called "libSpecial.a" which is located in "/usr/local/foo/lib", then you would use a statement like:

```
$ g++ MyProg.cpp -L/usr/local/foo/lib -lSpecial
```

This should produce an "a.out" file.  Of course, other GCC options may be used (e.g. "-o" to specify executable name), but the gist of what is required is shown above.

I hope this helps.

---

### Post by jonface on 2008-05-30
Guys thanks for your help. I can't check right now as I've just upgraded to 8.10 and it's giving me grief. Will let you know if it works when I get round to it,

Thanks,

Jon.

---

### Post by jonface on 2008-06-08
Thanks guys!

---

