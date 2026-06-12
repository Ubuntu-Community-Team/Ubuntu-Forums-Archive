---
title: "Segmentation Fault while running basic sdl program"
date: 2012-12-29
forum: Programming Talk
---

### Post by smithy545 on 2012-12-29
I was attempting to learn to program with sdl in c++ using lazy foo tutorials([http://lazyfoo.net/](http://lazyfoo.net/)) when I got a segfault error on my first program. Im working on a basic program that blits a bmp to the screen but it breaks when loading the image and/or when blitting it to the screen. Im running this on ubuntu server 12.04 32 bit. 
  
```

/*This source code copyrighted by Lazy Foo' Productions (2004-2012)
and may not be redistributed without written permission.*/

//Include SDL functions and datatypes
#include "SDL/SDL.h"

int main( int argc, char* args[] )
{
    //The images
    SDL_Surface* hello = NULL;
    SDL_Surface* screen = NULL;

    //Start SDL
    SDL_Init( SDL_INIT_EVERYTHING );

    //Set up screen. Problem Here.
    screen = SDL_SetVideoMode( 640, 480, 32, SDL_SWSURFACE );

    //Load image
    hello = SDL_LoadBMP( "hello.bmp" );

    //Apply image to screen
    SDL_BlitSurface( hello, NULL, screen, NULL );

    //Update Screen
    SDL_Flip( screen );

    //Pause
    SDL_Delay( 2000 );

    //Free the loaded image
    SDL_FreeSurface( hello );

    //Quit SDL
    SDL_Quit();

    return 0;
}

```

---

### Post by gnush on 2012-12-29
Either post your code in code-tags or use pastebin. I, probably including other members, dislike downloading stuff. It makes things much more tedious. Another reason posting the code directly in the thread is good is because you get an overview of the program, and can determine whether or not you're capable of helping.

---

### Post by smithy545 on 2012-12-29
Ya sorry. I put the code in my post.

---

### Post by Bachstelze on 2012-12-29
Works fine here, so you will need to provide more details. Have you tried it with other image files and/or on other systems?

---

### Post by smithy545 on 2012-12-29
Okay I've narrowed down the problem. I changed the bits per pixel, width and height of the window to 0 in SDL_SetVideoMode and it ran fine so I know it's a problem with that function.
If SDL_SetVideoMode is like this:
```
screen = SDL_SetVideoMode( 0, 0, 0, SDL_SWSURFACE );
```
It works, but if otherwise it gives a Segmentation Fault error.

---

### Post by smithy545 on 2013-01-05
I fixed my problem. I was in root while trying this and I logged into another account and it worked. Although it did appear in ASCII art format it still worked.

---

### Post by pbrane on 2013-01-05
> **smithy545 said:**
> Okay I've narrowed down the problem. I changed the bits per pixel, width and height of the window to 0 in SDL_SetVideoMode and it ran fine so I know it's a problem with that function.
If SDL_SetVideoMode is like this:
```
screen = SDL_SetVideoMode( 0, 0, 0, SDL_SWSURFACE );
```
It works, but if otherwise it gives a Segmentation Fault error.

you should be able to do something like this
```

screen = SDL_SetVideoMode(800, 600, 32, SDL_HWSURFACE | SDL_DOUBLEBUF);

```

also check for screen being null,
```

if (screen == null) {
  // say it's borked and exit
}

```

---

