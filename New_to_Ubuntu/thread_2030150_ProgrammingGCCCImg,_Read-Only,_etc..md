---
title: "Programming/GCC/CImg, Read-Only, etc."
date: 2012-07-20
forum: New to Ubuntu
---

### Post by lemmingrebel on 2012-07-20
My program, which does nothing:

> 
#include "CImg.h"
using namespace cimg_library;

  int main() {
    CImg<unsigned char> image("test.jpg");
  }


... is not compiling.  The error I get:

> In file included from imagetest.c:1:0:
/usr/include/CImg.h:72:18: fatal error: cstdio: No such file or directory


Well in CImg.h, we have this:

> 
// Include required standard C++ headers.
#include <cstdio>
#include <cstdlib>
#include <cstdarg>
#include <cstring>
#include <cmath>
#include <ctime>
#include <exception>


Apparently I need to change these to reference .h files, but I am locked from being able to do so in this directory.

Do I need to change my permissions and edit this file, or am I using an incorrect CImg.h?  WHat to do?


THanks,
B

---

### Post by lemmingrebel on 2012-07-20
I'm a new user so I posted in Beginner Talk ... maybe this belongs in the Programming forum?

---

### Post by steeldriver on 2012-07-20
Hi yes I think this question would get better responses in the Programming subforum

What build packages did you install (only gcc? g++? build-essential?)

FWIW your code compiles for me with the libs suggested here

[http://cimg.sourceforge.net/reference/group__cimg__overview.html](http://cimg.sourceforge.net/reference/group__cimg__overview.html)

i.e.

```
g++ -o cimg cimg.cpp -L/usr/X11R6/lib -lm -lpthread -lX11
```

---

