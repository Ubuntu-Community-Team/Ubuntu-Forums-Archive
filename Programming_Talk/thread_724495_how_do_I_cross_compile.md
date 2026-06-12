---
title: "how do I cross compile?"
date: 2008-03-14
forum: Programming Talk
---

### Post by Zeotronic on 2008-03-14
Can someone tell me how to cross compile? The more generalized response I get the better, unless any of you are familure with the GP2X? (the target platform). I admit I would also like to know how to cross compile for Windows and Mac, but the GP2X is the important one.

---

### Post by Fbot1 on 2008-03-14
It depends on the compiler.

---

### Post by WW on 2008-03-14
This looks like a good place to start: [http://wiki.gp2x.org/wiki/Setting_up_a_development_environment_%28Linux%29](http://wiki.gp2x.org/wiki/Setting_up_a_development_environment_%28Linux%29)
It's part of [the GP2X wiki](http://wiki.gp2x.org/).

---

### Post by Zeotronic on 2008-03-27
How do I cross compile though, for Windows and Mac?

---

### Post by WW on 2008-03-27
To compile a Windows program (i.e. to create a .exe file) from within Linux, I use the mingw32 compiler.  Check out the post by scourge in [this thread](http://ubuntuforums.org/showthread.php?t=734799).

To start, you'll need to install these packages: **mingw32**, **mingw32-binutils**, **mingw32-runtime**.

Another useful link: [http://www.profv.de/mingw_cross_env/](http://www.profv.de/mingw_cross_env/)
It is probably better to not run the script given in that link, since it will build the mingw32 compilers (at least that's what I think it does).  In Ubuntu, you can get them by installing the above packages.  Read the script for hints about cross-compiling libraries that you may need in your cross-compiled program.

---

### Post by WW on 2008-03-27
Here's a really simple example of cross-compiling a "Hello, world!" program in C:

**hello.c**
```

#include <stdio.h>

int main(int argc, char *argv[])
    {
    printf("Hello, world!\n");
    return 0;
    }

```
Compile it with the mingw32 compiler, and run it with wine:
> 
$ i586-mingw32msvc-gcc hello.c -o hello.exe
$ ls
hello.c  hello.exe
$ wine hello.exe 
Hello, world!

It gets more complicated when you use external libraries (such as a GUI), because you must cross-compile the libraries, too.

---

### Post by Zeotronic on 2008-03-28
Ok, but how do I cross compile for a Mac?

---

