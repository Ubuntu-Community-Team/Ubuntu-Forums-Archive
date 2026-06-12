---
title: "setting up SDL"
date: 2009-02-26
forum: Programming Talk
---

### Post by swappo1 on 2009-02-26
Hello,
I am trying to setup SDL to use the ebook Programming Linux Games.  All the tutorials seem to use C++ and I only know C which is what Programming Linux Games uses.  I downloaded and installed SDL from the lazyfoo website.
```
apt-get install libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev
```
I tried initializing SDL with the following program from Programming Linux Games.
```
/* Example of initializing SDL. */
#include <SDL/SDL.h>
#include <stdio.h>
#include <stdlib.h>
int main()
{
    SDL_Surface *screen;
    /* Initialize SDL’s video system and check for errors */
    if (SDL_Init(SDL_INIT_VIDEO) != 0) {
        printf("Unable to initialize SDL: %s\n", SDL_GetError());
        return 1;
    }
    /* Make sure SDL_Quit gets called when the program exits! */
    atexit(SDL_Quit);
    /* Attempt to set a 640x480 hicolor video mode */
    screen = SDL_SetVideoMode(640, 480, 16, SDL_FULLSCREEN);
    if (screen == NULL) {
        printf("Unable to set video mode: %s\n", SDL_GetError());
        return 1;
    }
    /* If we got this far, everything worked */
    printf("Success!\n");
    return 0;
}

```
When I run the program I get the following output.
```
scott@scott-laptop:~$ gcc -o initializing-sdl initializing-sdl.c
/tmp/ccSpmQW7.o: In function `main':
initializing-sdl.c:(.text+0xe): undefined reference to `SDL_Init'
initializing-sdl.c:(.text+0x17): undefined reference to `SDL_GetError'
initializing-sdl.c:(.text+0x37): undefined reference to `SDL_Quit'
initializing-sdl.c:(.text+0x55): undefined reference to `SDL_SetVideoMode'
initializing-sdl.c:(.text+0x65): undefined reference to `SDL_GetError'
collect2: ld returned 1 exit status

```
Any ideas what the problem is?  Thanks.

---

### Post by Simian Man on 2009-02-26
You need to link to the SDL libs with -lSDL.

When using the other libs you will need to link to them to so '-lSDL_image -lSDL_ttf, -lSDL_mixer' and so on.

---

### Post by dwhitney67 on 2009-02-26
Try compiling using the package config info for SDL:
```

gcc `pkg-config SDL --cflags` -o initializing-sdl initializing-sdl.c `pkg-config SDL --libs`

```


P.S.  Forgive me if there is a typo (or two).

---

### Post by swappo1 on 2009-02-26
Ok, -lSDL worked.  I didn't read far enough ahead where it tells me how to build an SDL application.  It gave me the following to use.
```
`sdl-config --cflags --libs`
```
Which worked as well.  -lSDL is shorter though.

Thanks

---

### Post by Simian Man on 2009-02-26
> **swappo1 said:**
> Ok, -lSDL worked.  I didn't read far enough ahead where it tells me how to build an SDL application.  It gave me the following to use.
```
`sdl-config --cflags --libs`
```
Which worked as well.  -lSDL is shorter though.

Thanks

The sdl-config command is better for makefiles though since it will link correctly on different platforms where the compiler linking commands are different.  SDL aims to be extremely cross-platform so sdl-config is still a good idea.

---

