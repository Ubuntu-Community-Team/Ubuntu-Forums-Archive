---
title: "[SOLVED] Eclipse CDT, cant include library"
date: 2007-12-01
forum: Programming Talk
---

### Post by juskrey on 2007-12-01
Hello,
I am just making "hello world" app in Eclipse CDT.
I have installed zlib 1.2.3
zlib.h is present an compiler sees it.

"libz.so" is present in /usr/lib

But g++ linker cand resolve external symbol. e.g. "compress"

```
hello.cpp:(.text+0x33e): undefined reference to `compress'
```

Normally, I try to feed linker with libz.so library

I tried to go to Project Properties -> CGG++ linker ->libraries
and to add "libz.so" to libraries and "/usr/lib" to library search path.

Nothing helps.
I get an error
```
Building target: hello
Invoking: GCC C++ Linker
g++ -L/usr/lib -o"hello"  ./hello.o   -llibz.so
/usr/bin/ld: cannot find -llibz.so
```

Without any external references, hello.cpp compiles normally.
Please help, I just cant figure it out. :confused:

---

### Post by geoog on 2007-12-01
Hello,

In Project Properties -> CGG++ linker ->libraries instead of add "libz.so" add just "z".
Normally the "-l" option requires that you "remove" the prefix "lib" and the ".so" from the library that you want to link.
Also, if you environment is working fine you'll not have to use the option "-L/usr/lib"

---

### Post by juskrey on 2007-12-02
Thanks, geoog.
It was the thing that windows programmer, like me, could not imagine :)

Before your answer, I began to worry seriously about my psychic health.

---

### Post by Toroid on 2011-11-28
Wow,  that was an unexpected solution, and a simple fix ~Humility~

---

