---
title: "Undefined reference while using fdlib.h - shared library"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by tanmanh0707 on 2014-05-02
I've downloaded a Facedetect shared library at [http://people.kyb.tuebingen.mpg.de/kienzle/facedemo/facedemo.htm](http://people.kyb.tuebingen.mpg.de/kienzle/facedemo/facedemo.htm) linux version - zip file.

Then I extracted it by using right click + Extract here, all I got is a fdlib_linux folder, inside that there're 4 files: fdlib.dat, fdlib.h (with 3 public functions), fdtest.cpp (example of using library) and libfd.so

I created a C file to test library:
```
#include <stdio.h>#include <stdlib.h>
#include <malloc.h> 
#include "fdlib.h"


int main() {
	unsigned char* graydata = malloc(640*480);
	unsigned char w = 480, h = 640, threshold = 0;
	fdlib_detectfaces(graydata, w, h, threshold);	
	return 0;
}

```

and put this main.c in fdlib_linux folder and compiled in terminal with command:

```
gcc -I /home/tanmanh/Desktop/fdlib_linux -L /home/tanmanh/Desktop/fdlib_linux -Wall main.c -o app -lfd
```

I got an error

```
/tmp/ccbYf1wP.o: In function `main':main.c:(.text+0x4b): undefined reference to `fdlib_detectfaces'
collect2: ld returned 1 exit status

```

I tried to put libfd.so to /usr/lib and recompiled but the same error orrured.

Please tell me how to use that library. Thanks all.

---

### Post by steeldriver on 2014-05-02
Hello and welcome to the forums. A couple of things I noticed:

1. the software you downloaded appears to be a C++ library (not C) - based on the provided fdtest.cpp example file, your test code should probably look something like 

```

#include "fdlib.h"

int main() {
  int w = 480, h = 640, threshold = 0;
  unsigned char * graydata = new unsigned char[w*h];
  fdlib_detectfaces(graydata, w, h, threshold);
  return 0;
}
```

and be compiled with g++ not gcc

2. the libfd.so library appears to have been compiled against an old version of the C++ standard library, libstdc++5 so you will probably need to add that to your system. On my 12.04 box that was possible from the standard repository apparently without any conflicts but ymmv.

Aside for using libstdc++5, the project does not appear to be active since about 2008 - unless there are compelling reasons otherwise, you might want to consider using something more current such as OpenCV. Hope this helps.

---

