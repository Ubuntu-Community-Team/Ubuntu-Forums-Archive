---
title: "SDL Problem"
date: 2010-01-26
forum: Programming Talk
---

### Post by wwsoft on 2010-01-26
Hello , Im new to SDL. Im trying to write a simple game engine to make game devlopment easier for me. But Im running into some problems ...

```
 
#include <SDL.h>
#include "SDL_image.h"
#include "SDL_ttf.h"
#include "SDL_mixer.h"

#include <cstdio>
#include <iostream>
#include "engin.h"
#include "objects.h"

int main ( int argc, char** argv )
{
    // initialize SDL video
    if ( SDL_Init( SDL_INIT_EVERYTHING) < 0 )
    {
        printf( "Unable to init SDL: %s\n", SDL_GetError() );
        return 1;
    }

    if(Mix_Init()==-1) // error
    {
        //printf("Mix_Init: %s\n", Mix_GetError());
        return 1;
    }

    if(IMG_Init()==-1)//error
    {
        //printf("IMG_Init: %s\n", IMG_GetError());
        return 1;
    }

    if(TTF_Init()==-1)// works fine
    {
        printf("TTF_Init: %s\n", TTF_GetError());
        return 1;
    }
...

|24|error: ‘Mix_Init’ was not declared in this scope|
|30|error: ‘IMG_Init’ was not declared in this scope|


```Im linking all of the sdl librarys but for some reason none of the functions are being defined ... Can someone shed some light onto my problem ?

sidenote: SDL_ttf works fine

---

### Post by dwhitney67 on 2010-01-26
Two things are missing from your post...

1)  How are you compiling/linking your application;

2)  What are the exact errors.  (EDIT:  I see the errors within your code listing).

EDIT #2:
I just noticed that on my Ubuntu 9.10 system, the SDL 1.2.8 version of SDL_mixer does not define Mix_Init() or Mix_Quit().  However with SDL 1.2.10, it does.  Here's the SDL_mixer.h header file with version 1.2.10:
[http://svn.euclids-dream.com/repos/games/blessed_relief/trunk/include/win-vc8/SDL/SDL_mixer.h](http://svn.euclids-dream.com/repos/games/blessed_relief/trunk/include/win-vc8/SDL/SDL_mixer.h)

---

### Post by heamaster on 2010-01-26
Often when my functions are not found it is becuase I'm only compiling for example like this:
[PHP]gcc main.c[/PHP]
Not like this:
[PHP]gcc *.c[/PHP]

---

### Post by dwhitney67 on 2010-01-26
> **heamaster said:**
> Often when my functions are not found it is becuase I'm only compiling for example like this:
[PHP]gcc main.c[/PHP]
Not like this:
[PHP]gcc *.c[/PHP]

This only helps in resolving linking issues; not compiling issues.

---

### Post by wwsoft on 2010-01-27
```

Mix_Init(MIX_INIT_OGG|MIX_INIT_MOD)
...

/usr/include/SDL/SDL_image.h|70|error: too few arguments to function ‘int IMG_Init(int)’|
```

---

