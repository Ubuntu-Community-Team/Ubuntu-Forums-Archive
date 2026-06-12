---
title: "MINGW Cross Compile Linker problems"
date: 2009-09-30
forum: Packaging and Compiling Programs
---

### Post by TheDude7053 on 2009-09-30
i run in to this when i try to link prboom cross compiling in Ubuntu

make  all-recursive
make[1]: Entering directory `/home/sean/Desktop/prboom-2.5.0'
Making all in doc
make[2]: Entering directory `/home/sean/Desktop/prboom-2.5.0/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sean/Desktop/prboom-2.5.0/doc'
Making all in data
make[2]: Entering directory `/home/sean/Desktop/prboom-2.5.0/data'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/sean/Desktop/prboom-2.5.0/data'
Making all in src
make[2]: Entering directory `/home/sean/Desktop/prboom-2.5.0/src'
Making all in SDL
make[3]: Entering directory `/home/sean/Desktop/prboom-2.5.0/src/SDL'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/sean/Desktop/prboom-2.5.0/src/SDL'
Making all in POSIX
make[3]: Entering directory `/home/sean/Desktop/prboom-2.5.0/src/POSIX'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/sean/Desktop/prboom-2.5.0/src/POSIX'
Making all in MAC
make[3]: Entering directory `/home/sean/Desktop/prboom-2.5.0/src/MAC'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/sean/Desktop/prboom-2.5.0/src/MAC'
make[3]: Entering directory `/home/sean/Desktop/prboom-2.5.0/src'
i586-mingw32msvc-gcc  -g -O2 -Wall -Wno-unused -Wno-switch -march=native -Wextra -Wno-missing-field-initializers -Winline -Wwrite-strings -Wundef -Wbad-function-cast -Wcast-align -Wcast-qual -Wdeclaration-after-statement -ffast-math -O2 -fomit-frame-pointer -I../src -I/usr/local/cross-tools/i386-mingw32/include/SDL -D_GNU_SOURCE=1 -Dmain=SDL_main   -o prboom-game-server.exe d_server.o POSIX/libposixdoom.a SDL/i_network.o -lSDL_net -L/usr/local/cross-tools/i386-mingw32/lib -lmingw32 -lSDLmain -lSDL -mwindows -lSDL_mixer -lm 
POSIX/libposixdoom.a(i_system.o): In function `I_uSleep':
/home/sean/Desktop/prboom-2.5.0/src/POSIX/i_system.c:62: undefined reference to `_select'
SDL/i_network.o: In function `I_WaitForPacket':
/home/sean/Desktop/prboom-2.5.0/src/SDL/i_network.c:116: undefined reference to `_I_UpdateConsole'
collect2: ld returned 1 exit status
make[3]: *** [prboom-game-server.exe] Error 1
make[3]: Leaving directory `/home/sean/Desktop/prboom-2.5.0/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sean/Desktop/prboom-2.5.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sean/Desktop/prboom-2.5.0'
make: *** [all] Error 2

---

### Post by DemonTPx on 2009-10-01
These are the errors:

```
POSIX/libposixdoom.a(i_system.o): In function `I_uSleep':
/home/sean/Desktop/prboom-2.5.0/src/POSIX/i_system.c:62: undefined reference to `_select'
SDL/i_network.o: In function `I_WaitForPacket':
/home/sean/Desktop/prboom-2.5.0/src/SDL/i_network.c:116: undefined reference to `_I_UpdateConsole'
```

It looks to me that you need to link to some extra library, but I'm not sure which one that is. Perhaps stdc++?

---

