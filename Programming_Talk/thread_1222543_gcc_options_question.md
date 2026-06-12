---
title: "gcc options question"
date: 2009-07-25
forum: Programming Talk
---

### Post by ooobooontooo on 2009-07-25
Hi,

I was wondering whether there was an easy to way to tell if a certain option for gcc (like -pthread or -fno-stack-pointer) is to be used during compiling or linking or both. So far I've been guessing and adjusting based on gcc output, but I would like to know for sure. Thanks in advance.

---

### Post by manualqr on 2009-07-25
You can decide what flags you want to enable yourself, unless some code you're compiling explicitly depends that certain flags are set (or not set). Most of the time, people mention mandatory flags in release notes.

The best way to tell if you need a flag is to know what it does, and how it changes the output.

For example, -lpthread links code with the POSIX Threading library - enabling multithreading. If the program isn't multithreaded, there's no need for this flag.

---

### Post by ooobooontooo on 2009-07-25
> **manualqr said:**
> You can decide what flags you want to enable yourself, unless some code you're compiling explicitly depends that certain flags are set (or not set). Most of the time, people mention mandatory flags in release notes.

The best way to tell if you need a flag is to know what it does, and how it changes the output.

For example, -lpthread links code with the POSIX Threading library - enabling multithreading. If the program isn't multithreaded, there's no need for this flag.

Yes thank you for you answer, but that wasn't exactly my question. My question if I do need to include some flags, how do I know whether to include it in the compilation stage or the linking stage or both? Is there any indication of this listed for each flag?

---

### Post by dwhitney67 on 2009-07-25
If you are asking if there is a magic solution that will tell you exactly what you need, well in most cases no there is not.  In a few cases, where third-party libraries offer the "pkg-config" (or "sdl-config") support, then these are helpful to obtain the flags for those particular libraries.

As for using gcc, the most commonly used options (note that I do not refer these to "flags"), are the following:
```

For compilation:

   -c          generates an object file
   -o          to specify an alternate object file name (rarely needed)
   -Wall       warn about everything that requires such
   -Werror     treat warnings as errors
   -ansi       code must conform to ISO C/C++
   -pedantic   enforces compliance of ISO C/C++
   -I          for specifying alternate path to locate header file(s)
   -g          for including symbolic info for debug purposes

For linking:
   -L          for specifying alternate path to locate library
   -l          for specifying a library
   -o          for specifying an alternate name for the executable (a.out is the default)
   -On         for specifying the level of optimization (by default, n=0 is used).

```

So, to compile a simple program in two steps (compile and then link):
```

gcc -Wall -ansi -pendantic -c -I/usr/local/simple/include Simple.c
gcc Simple.o -L/usr/local/simple/lib -lsimple -o too_simple

```
Alternatively, to do it all in one step (note that the -c option is not required):
```

gcc -Wall -ansi -pedantic -I/usr/local/simple/Include Simple.c -L/usr/local/simple/lib -lsimple -o too_simple

```

---

### Post by ooobooontooo on 2009-07-26
@dwhitney67
Thanks that's basically the answer I was looking for. I can't combine it to one statement because my makefile automatically creates dependencies and so I was just looking for a way to make sure whether an option had to be added during the compilation stage or the linking stage. Thanks.

EDIT: fixed grammar mistake and change "flags" to "options"

---

