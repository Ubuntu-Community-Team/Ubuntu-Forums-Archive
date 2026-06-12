---
title: "g++ including and linking in Ubuntu"
date: 2009-09-06
forum: Programming Talk
---

### Post by kumoshk on 2009-09-06
I've noticed many issues with linking in Ubuntu, and one important one with including.

I've figured out how to work around the include problem, which is this:
I have to reference the *full* path to the header files. For instance, instead of typing
#include "lua.h"
I have to type
#include "/usr/include/lua5.1/lua.h"

How do I fix this? It's kind of annoying when I have to do this and it seems everyone else and their dog thinks it's second nature to do it the other way. I have two completely different installations of Ubuntu (both Jaunty, one 32 bit on my desktop and the other 64 bit on my laptop), and they both behave the same way. Plus, I'm curious why doesn't it seem like this issue is ever addressed if Ubuntu ships like this out of the box: do you all know something I don't? I guess so.

With linking, however, it seems that no matter what example program I'm trying to compile, some library or other will not link, regardless of whether I have it installed. Unfortunately, I don't even know a workaround for that, but I'm guessing it's a similar problem. I'm not very familiar at all with linking—so if you could tell me something useful, feel free. The error message is gives just tells that it can't find the library or some such (I'm not in a position to find the exact message at the moment, but perhaps later).

Any ideas?

---

### Post by TheStatsMan on 2009-09-06
For the example you gave include -I/usr/include/lua5.1/ and for libraries same idea except use -L . You probably should set up a makefile if it is for a project you will be using regularly

---

### Post by TheStatsMan on 2009-09-06
I am assuming you are compiling from the command line. 

Edit: This was mean to be an added to my first post. I cannot work out how to delete this one.

---

### Post by bhagabhi on 2009-09-06
For a portable way to solve this (in the case of the described LUA problem), you should use something like

```
`pkg-config lua-5.1 --cflags`
``` when compiling, and

```
`pkg-config lua-5.1 --libs`
``` when linking. Not all packages uses the pkg-config system though.

---

### Post by dwhitney67 on 2009-09-06
> **bhagabhi said:**
> ...
Not all packages uses the pkg-config system though.

That's correct; thus I think it would be helpful if the OP were given the basics so that he could build any application.

GCC (which includes 'gcc' and 'g++') can accept the following command line options (amongst many others not noted below):

```

-I<path>       This is used to specify the path to a header file.
-L<path>       This is used to specify the path to a library (shared or static).
-l<lib>        This is used to specify a library (w/o 'lib' and w/o file extension part of the library name).

```
So for example, if you have a library for the Foo toolkit, and this library has header files in /opt/include/foo and a shared-object library in /opt/lib, you could use the following statement to compile an application that depends on this.
```

g++ -I/opt/include FooApp.cpp -L/opt/lib -lfoo

```
or alternatively
```

g++ -I/opt/include -c FooApp.cpp
g++ FooApp.o -L/opt/lib -lfoo

```
Within FooApp.cpp, the header file would be included as such (note that the path is the relative location from /opt/include; this is the most common way to include non-standard header files):
```

#include <foo/foo.h>
...

```

When a shared-object library is *not* in a typical location (eg. /usr/lib), then it is necessary to either 1) augment the ldconfig cache with the non-standard path where this library resides, or 2) set LD_LIBRARY_PATH before running the application.

Augmenting the ldconfig cache requires root privileges, which not every user has.  To do this, one needs to create a file in /etc/ld.so.conf.d which contains the path to our library, which if using the example above, would be /opt/lib.  After creating/saving the file, then ldconfig is executed to update the cache:
```

sudo ldconfig

```

The alternative is using the LD_LIBRARY_PATH, for which you can do something like:
```

export LD_LIBRARY_PATH=/opt/lib:$LD_LIBRARY_PATH

./a.out

```
or
```

LD_LIBRARY_PATH=/opt/lib:$LD_LIBRARY_PATH ./a.out

```

Hopefully this lengthy reply answers the OP's question.

---

### Post by kumoshk on 2009-09-07
Ah, thanks for all the information everyone. That should be quite helpful.

I do, however, think that some of my libraries are hard to find.

I'm pretty sure I have OpenGL installed, but I can't seem to find the C or C++ libraries, whichever they are. I can, however, find them for all sorts of other languages (Python, D, etc.). I can, also, find the Windows versions I have installed:
~/.wine/drive_c/MinGW/lib/libopengl32.a
~/.wine/drive_c/windows/system32/opengl32.dll
/usr/i586-mingw32msvc/lib/libopengl32.a

Maybe I don't have it installed. Is it FreeGlut I need, or something else? I thought I had the mesa stuff installed already.

---

