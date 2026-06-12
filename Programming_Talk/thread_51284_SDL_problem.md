---
title: "SDL problem"
date: 2005-07-23
forum: Programming Talk
---

### Post by Vurdak829 on 2005-07-23
Hi all! I'm a completely newbie with programming (schools teach only teory :( )but i've a problem with SDL and a very simple program.
```

#include "SDL/SDL.h" 
#include <stdio.h>
int main() {
    printf("Initializing SDL.\n");
    if((SDL_Init(SDL_INIT_VIDEO|SDL_INIT_AUDIO)==-1)) { 
        printf("Could not initialize SDL: %s.\n", SDL_GetError());
        exit(-1);
    }
    printf("SDL initialized.\n");
    printf("Quiting SDL.\n");
    SDL_Quit();
    printf("Quiting....\n");
    exit(0);
}
```

I get this errors: ```
example.c:24:2: warning: no newline at end of file
/tmp/ccUQ7KJs.o(.text+0x24): In function `main':
: undefined reference to `SDL_Init'
/tmp/ccUQ7KJs.o(.text+0x2e): In function `main':
: undefined reference to `SDL_GetError'
/tmp/ccUQ7KJs.o(.text+0x67): In function `main':
: undefined reference to `SDL_Quit'
collect2: ld returned 1 exit status

```

I have an ubuntu hoary 32bit, and i've installed libsdl1.2debian and libsdl1.2-dev. Thx to all :)

---

### Post by charlieg on 2005-07-24
Removed - sorry, I got that wrong (read the brackets wrong).

---

### Post by Hanj on 2005-07-24
I've never used SDL myself, but those error messages sound like you're not linking to SDL correctly. Maybe you should check your linker options?

---

### Post by Vurdak829 on 2005-07-25
Following the instruction of a friend of mine, i've tried to compile the program with the gcc option -lsdl. It didn't work yet
```
example.c:24:2: warning: no newline at end of file
/usr/bin/ld: cannot find -lsdl
collect2: ld returned 1 exit status

```
After that, i've tried to see if libsdl were present on /usr/lib
```
ls /usr/lib/libsd*
ls: /usr/lib/libsd*: No such file or directory

```
I've tried to reinstall libsdl-devel, but the problem is the same...

---

### Post by Vurdak829 on 2005-07-25
[QUOTE=Hanj]I've never used SDL myself, but those error messages sound like you're not linking to SDL correctly. Maybe you should check your linker options?[/QUOTE]

No, i've already tried ;)

---

### Post by Hanj on 2005-07-25
If you haven't already, check [this](http://www.libsdl.org/cgi/docwiki.cgi/FAQ_20Compiling_20on_20Linux) link out. Seems like SDL comes with some bash scripts to help you with linker options, like this:
```
 gcc `sdl-config --cflags` `sdl-config --libs` -osdltest sdltest
```

Maybe someone who has actually used SDL could be of more help if this doesn't work ;)

---

### Post by Vurdak829 on 2005-07-25
It works! Thx hanj :)
But i discovered that it work also with gcc -lSDL option (not -lsdl) :P

---

