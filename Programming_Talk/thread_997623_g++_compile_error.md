---
title: "g++ compile error"
date: 2008-11-30
forum: Programming Talk
---

### Post by Buttink on 2008-11-30
ok so here is my make file (problem is further down :) )

[PHP]# Make file thingy!!!

CC = g++
FLAGS = `sdl-config --cflags` -c
NAME = MainProg

main: main.o video.o
	$(CC) -o main.o video.o -lSDL $(NAME)

main.o: main.cpp video.h
	$(CC) $(FLAGS) main.cpp

video.o: video.h[/PHP]

Btw, its a simple SDL program. Both video and main will compile, but when it tries to link them i get errors such as ...

```
MainProg: In function `_start':
(.text+0x0): multiple definition of `_start'
/usr/lib/gcc/i486-linux-gnu/4.2.4/../../../../lib/crt1.o:(.text+0x0): first defined here
MainProg:(.rodata+0x0): multiple definition of `_fp_hw'
/usr/lib/gcc/i486-linux-gnu/4.2.4/../../../../lib/crt1.o:(.rodata+0x0): first defined here
MainProg: In function `_fini':
/build/buildd/glibc-2.7/build-tree/i386-libc/csu/crti.S:41: multiple definition of `_fini'
/usr/lib/gcc/i486-linux-gnu/4.2.4/../../../../lib/crti.o:/build/buildd/glibc-2.7/build-tree/i386-libc/csu/crti.S:41: first defined here
MainProg:(.rodata+0x4): multiple definition of `_IO_stdin_used'
/usr/lib/gcc/i486-linux-gnu/4.2.4/../../../../lib/crt1.o:(.rodata.cst4+0x0): first defined here
MainProg: In function `InitVideo()':
(.text+0xec): multiple definition of `InitVideo()'
video.o:video.cpp:(.text+0x15a): first defined here
MainProg: In function `__data_start':
(.data+0x0): multiple definition of `__data_start'
/usr/lib/gcc/i486-linux-gnu/4.2.4/../../../../lib/crt1.o:(.data+0x0): first defined here

```

Im assuming this is something simple, but I haven't been able to find anything about it. Im probably typing wrong keywords for search. Well any help would be appreciated. If you want me to post the contents of main.cpp or video.cpp, I would be glad to.

---

