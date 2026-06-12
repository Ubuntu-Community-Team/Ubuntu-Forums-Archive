---
title: "undefined reference to `main' -- but main is defined"
date: 2010-10-28
forum: Packaging and Compiling Programs
---

### Post by pavel989 on 2010-10-28
hey all,
I have a very simple C++ program:
```
pavel@pavel-desktop:~/programming/screen manager$ cat main.cpp
//#include <string>
//#include <iostream>
#include <stdio.h>

class Main {

        int main(int argc, const char* argv[]) {
                printf( "\nHello World\n\n" );
                return 1;
        }

};

```


that i cannot figure out how to compile. I understand that this is in the linking stage...

```
pavel@pavel-desktop:~/programming/screen manager$ g++ main.cpp -o hello.exe
/usr/lib/gcc/x86_64-linux-gnu/4.4.5/../../../../lib/crt1.o: In function `_start':
(.text+0x20): undefined reference to `main'
collect2: ld returned 1 exit status
```


but i defined a main, maybe im compiling wrong?

---

### Post by Tyr42 on 2010-12-29
I have the same error.  Is it due to a 64 bit version of linux?

---

### Post by MadCow108 on 2010-12-29
if you have the exact same problem:
c++ is not java
the main function must not be in a class

but more likely you just forget the main function or do not want to compile an executable.
In the latter case compile with -c:
g++ somefile.cpp -o output.o -c

---

