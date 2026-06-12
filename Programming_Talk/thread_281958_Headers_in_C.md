---
title: "Headers in C"
date: 2006-10-21
forum: Programming Talk
---

### Post by tetsuo84 on 2006-10-21
Hello everyone, I was wondering how can I use my own headers in C.

For example if I have test.h in /home/myaccount/

I did this,

#include </home/myaccount/test.h>

this isn't working, can anyone help?

---

### Post by po0f on 2006-10-21
tetsuo84,

If your source and header file are in the same directory, just include like this:
```
#include "foo.h"
```
When you compile your program, add -I./ to the command:
```
$ gcc -Wall -I./ -o foo foo.c
```
gcc's -I parameter tells gcc to look for included header files in the directory specified, and ./ means the current directory.

Note, those are capital i's, -l (ell) specifies a libray to link with.

---

### Post by JonahRowley on 2006-10-22
It's a bad idea to use absolute paths in includes (if it's even possible).  Some people say it's a bad idea to use any paths, even relative paths.  The point is (as po0f pointed out), use the -I switch.  I wouldn't just dump it in ~ either, your home tends to get cluttered pretty quickly.  I have a **~/code** directory.

So, if I have **socket.h** in **~/code**, I would use **#include "socket.h"** and use the **-I$HOME/code** switch with GCC.  I don't think **-I~/code** will work (~ being expanded in the middle of a string), so be careful there.

---

