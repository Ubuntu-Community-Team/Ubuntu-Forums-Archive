---
title: "GNU C++ struct _attribute_ packed...compile error"
date: 2013-02-16
forum: Packaging and Compiling Programs
---

### Post by gtyler on 2013-02-16
I'm having difficulty correcting the following compile error.
Any help would be appreciated.

Source.....

#include <stdio.h>
#include <stdlib.h>
#include <stdint.h>
using namespace std;

struct strA
{ char a;
  int b;
} _attribute_ ((packed,aligned (8)));

int main(int argc, char **argv)
{
 int mainrc=0;
 return mainrc;
}

Compiler.......

g++ --version
g++ (Ubuntu/Linaro 4.7.2-2ubuntu1) 4.7.2
Copyright (C) 2012 Free Software Foundation, Inc.

ERROR.........

g++ -std=c++11 /home/arcdeveloper/csrc/structatt.c++
/home/arcdeveloper/csrc/structatt.c++:9:17: error: ‘packed’ was not declared in this scope
/home/arcdeveloper/csrc/structatt.c++:9:34: error: ‘aligned’ was not declared in this scope

Thanks in advance, gtyler

---

### Post by MadCow108 on 2013-02-17
its __attribute__ with two underscores

what are you trying to archive here? a char followed by a 8 byte aligned int?

that would be written like this:
```
 struct strA
 { char a ;
 int b __attribute__((aligned (8)));
 } __attribute__((packed));
```
but the structure will still be 16byte large, I think you need to use explicit padding to get it to 12 byte.

---

### Post by gtyler on 2013-02-17
Thanks MADCOW108.

My eyes must not be what they used to be.

---

