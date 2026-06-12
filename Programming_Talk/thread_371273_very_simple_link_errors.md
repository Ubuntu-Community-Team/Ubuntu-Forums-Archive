---
title: "very simple link errors"
date: 2007-02-26
forum: Programming Talk
---

### Post by bryan.taylor on 2007-02-26
I have encountered a very basic undefined symbols problem while trying to compile one of the examples for [annie](http://annie.sourceforge.net/).  To simplify the problem I did the following:

created 1 header file: Foo.h
```
int Foo(int thing);
```

created 2 source files: Foo.cpp
```
#include "Foo.h"

int Foo(int thing)
{
	return thing+1;
}
```

and: main.cpp
```
#include "Foo.h"
#include <iostream>

int main()
{
	int i = 0;
	std::cout << i << std::endl;
	i = Foo(i);
	std::cout << i << std::endl;
	
	return 0;
}
```

I compiled Foo.cpp like this:
```
g++ -c Foo.cpp
```

I made a library like this:
```
ar r libFoo.a Foo.o
```
I also tried running ranlib on the libary.

I *tried* to compile main.cpp like this:
```
g++ -I./ -L./lib -lFoo -o main main.cpp
```

and g++ spits out this:
```
/tmp/ccdlDQMO.o: In function `main':
main.cpp:(.text+0xb4): undefined reference to `Foo(int)'
collect2: ld returned 1 exit status
```

objdump tells me that the contents of libFoo.a are this:
```
objdump -x -C ./lib/libFoo.a 
In archive ./lib/libFoo.a:

Foo.o:     file format elf32-i386
rw-r--r-- 1000/1000    742 Feb 26 17:12 2007 Foo.o
architecture: i386, flags 0x00000010:
HAS_SYMS
start address 0x00000000

Sections:
Idx Name          Size      VMA       LMA       File off  Algn
  0 .text         0000000b  00000000  00000000  00000034  2**2
                  CONTENTS, ALLOC, LOAD, READONLY, CODE
  1 .data         00000000  00000000  00000000  00000040  2**2
                  CONTENTS, ALLOC, LOAD, DATA
  2 .bss          00000000  00000000  00000000  00000040  2**2
                  ALLOC
  3 .comment      00000041  00000000  00000000  00000040  2**0
                  CONTENTS, READONLY
  4 .note.GNU-stack 00000000  00000000  00000000  00000081  2**0
                  CONTENTS, READONLY
SYMBOL TABLE:
00000000 l    df *ABS*  00000000 Foo.cpp
00000000 l    d  .text  00000000 .text
00000000 l    d  .data  00000000 .data
00000000 l    d  .bss   00000000 .bss
00000000 l    d  .note.GNU-stack        00000000 .note.GNU-stack
00000000 l    d  .comment       00000000 .comment
00000000 g     F .text  0000000b Foo(int)
00000000         *UND*  00000000 __gxx_personality_v0
```

What am I doing wrong?

---

### Post by WW on 2007-02-26
The -L option gives a **directory**, but you have not put libFoo.a in a subdirectory called lib.

Also, put main.cpp before the reference to the library in the g++ command.  This will compile and link main:
> $ g++  main.cpp -L./ -lFoo -o main
(Since Foo.h is in the current directory, you don't actually need the option **-I./**)

---

### Post by bryan.taylor on 2007-02-26
Thanks, swapping the order worked :)  I actually had put libFoo.a in the lib subdirectory, but I forgot to mention it.

---

