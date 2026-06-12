---
title: "[SOLVED] can u save c++ header to a diff location"
date: 2008-10-21
forum: Programming Talk
---

### Post by AceDip on 2008-10-21
I dont like the tedious task of everytime saving your c++ header files in /usr/include/c++/4.2
instead i would want to save them in the same folder as with my other c++ programs.

---

### Post by CptPicard on 2008-10-21
Why do you need to do that?

Just #include "yourheader.h" and it's looked for in the current directory...

---

### Post by dwhitney67 on 2008-10-21
> **AceDip said:**
> I dont like the tedious task of everytime saving your c++ header files in /usr/include/c++/4.2
...
:shock:   WTF?

Save your header file within your current working directory (as CptPicard noted).  If you need to store it elsewhere, then specify the location using the -I option when you compile.  For example:

Headers are in /home/programbo/headers.  Code in /home/programbo/code.

compile file1.cpp using:
```
g++ -I/home/programbo/headers file1.cpp -o myprog
```

---

### Post by AceDip on 2008-10-21
thanks man

---

