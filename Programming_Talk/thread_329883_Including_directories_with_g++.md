---
title: "Including directories with g++"
date: 2007-01-02
forum: Programming Talk
---

### Post by Cybernetic Being on 2007-01-02
This is no doubt a very basic question, but try as I might I haven't been able to find an answer. When using g++ to compile C++ source files from a terminal in Ubuntu, what options do you add to set the directories that contain header files that you have #included using quotation marks?

Say I have a header file in an "include" directory within the directory of the source file I'm trying to compile. When I add a directory using g++'s -I option, as in "g++ myfile.cpp -I ./include", adding the -v command shows that it has been added under

```
#include <...> search starts here:
```

but not under

```
#include "..." search starts here:
```

and the compiler claims that there is 'no such file or directory' when trying to process #include "..." statements.

What am I doing wrong? I'm still quite new to Linux and haven't got as much experience in C++ as many, so this is probably something really simple...

---

