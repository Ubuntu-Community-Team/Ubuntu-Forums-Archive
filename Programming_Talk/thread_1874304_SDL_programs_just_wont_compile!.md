---
title: "SDL programs just wont compile!"
date: 2011-11-02
forum: Programming Talk
---

### Post by compiz addict on 2011-11-02
Here's what I got from the terminal upon running ./compile
```

/tmp/ccoqWjtQ.o: In function `Slock(SDL_Surface*)':
test.cpp:(.text+0x25): undefined reference to `SDL_LockSurface'
/tmp/ccoqWjtQ.o: In function `Sulock(SDL_Surface*)':
test.cpp:(.text+0x56): undefined reference to `SDL_UnlockSurface'
/tmp/ccoqWjtQ.o: In function `DrawPixel(SDL_Surface*, int, int, unsigned char, unsigned char, unsigned char)':
test.cpp:(.text+0x97): undefined reference to `SDL_MapRGB'
/tmp/ccoqWjtQ.o: In function `DrawScene(SDL_Surface*)':
test.cpp:(.text+0x282): undefined reference to `SDL_Flip'
/tmp/ccoqWjtQ.o: In function `graphics()':
test.cpp:(.text+0x29a): undefined reference to `SDL_Init'
test.cpp:(.text+0x2a6): undefined reference to `SDL_GetError'
test.cpp:(.text+0x2c9): undefined reference to `SDL_Quit'
test.cpp:(.text+0x2f2): undefined reference to `SDL_SetVideoMode'
test.cpp:(.text+0x300): undefined reference to `SDL_GetError'
test.cpp:(.text+0x359): undefined referenc

```

Here's ./compile
```

gcc -o test `sdl-config --libs` `sdl-config --cflags` -lSDL_mixer -lpthread *.cpp

```

Here's test.cpp (variable declarations are just for later use)
```

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <math.h>
#include "SDL_mixer.h"
#include "SDL.h"
#include "graphics.h"
#define FIGURES 240
#define POINTS 10

int xpos[FIGURES][POINTS];
int ypos[FIGURES][POINTS];

int main(int argc, char *argv[])
{
  graphics();
  return 0;
}

```

and here's graphics.h
```

void Slock(SDL_Surface *screen)
{
  if ( SDL_MUSTLOCK(screen) )
  {
    if ( SDL_LockSurface(screen) < 0 )
    {
      return;
    }
  }
}

void Sulock(SDL_Surface *screen)
{
  if ( SDL_MUSTLOCK(screen) )
  {
    SDL_UnlockSurface(screen);
  }
}

void DrawPixel(SDL_Surface *screen, int x, int y,
                                    Uint8 R, Uint8 G, Uint8 B)
{
  Uint32 color = SDL_MapRGB(screen->format, R, G, B);
  switch (screen->format->BytesPerPixel)
  {
    case 1: // Assuming 8-bpp
      {
        Uint8 *bufp;
        bufp = (Uint8 *)screen->pixels + y*screen->pitch + x;
        *bufp = color;
      }
      break;
    case 2: // Probably 15-bpp or 16-bpp
      {
        Uint16 *bufp;
        bufp = (Uint16 *)screen->pixels + y*screen->pitch/2 + x;
        *bufp = color;
      }
      break;
    case 3: // Slow 24-bpp mode, usually not used
      {
        Uint8 *bufp;
        bufp = (Uint8 *)screen->pixels + y*screen->pitch + x * 3;
        if(SDL_BYTEORDER == SDL_LIL_ENDIAN)
        {
          bufp[0] = color;
          bufp[1] = color >> 8;
          bufp[2] = color >> 16;
        } else {
          bufp[2] = color;
          bufp[1] = color >> 8;
          bufp[0] = color >> 16;
        }
      }
      break;
    case 4: // Probably 32-bpp
      {
        Uint32 *bufp;
        bufp = (Uint32 *)screen->pixels + y*screen->pitch/4 + x;
        *bufp = color;
      }
      break;
  }
}

void DrawScene(SDL_Surface *screen)
{
  Slock(screen);
  for(int x=0;x<640;x++)
  {
    for(int y=0;y<480;y++)
    {
      DrawPixel(screen, x,y,y/2,y/2,x/3);
    }
  }
  Sulock(screen);
  SDL_Flip(screen);
}

int graphics()
{

  if ( SDL_Init(SDL_INIT_AUDIO|SDL_INIT_VIDEO) < 0 )
  {
    printf("Unable to init SDL: %s\n", SDL_GetError());
    exit(1);
  }
  atexit(SDL_Quit);

  SDL_Surface *screen;
  screen=SDL_SetVideoMode(640,480,32,SDL_HWSURFACE|SDL_DOUBLEBUF);
  if ( screen == NULL )
  {
    printf("Unable to set 640x480 video: %s\n", SDL_GetError());
    exit(1);
  }
  int done=0;

  while(done == 0)
  {
    SDL_Event event;

    while ( SDL_PollEvent(&event) )
    {
      if ( event.type == SDL_QUIT )  {  done = 1;  }

      if ( event.type == SDL_KEYDOWN )
      {
        if ( event.key.keysym.sym == SDLK_ESCAPE ) { done = 1; }
      }
    }

    DrawScene(screen);
  }

  return 0;
}

```

I don't see why this wouldn't work. I even tried copying some online tutorials, and THEY wouldn't compile! I have libsdl1.2-dev and libsdl-mixer1.2-dev both installed. I have no idea what to do!! :confused::confused::confused: Most of the code is copied and pasted from a tutorial as well, further supporting that it should work!

---

### Post by crdlb on 2011-11-03
Why is your file named ".cpp"? If you are compiling C with gcc, it should be ".c"

When doing a one-line compile and link, gcc can be very funny about the order of the arguments. Try:```
gcc test.c -std=c99 `sdl-config --cflags` `sdl-config --libs` -o test
```
The "-std=c99" is necessary because your graphics.h uses a C99 feature ("for(int x=0;...").

P.S. Why is that header file filled with code? That code belongs in a .c file. A header file should contain function prototypes for functions that need to be called from another file. All of the other functions should be "static".

P.P.S. in C, "int graphics()" should be "int graphics(void)".

---

### Post by compiz addict on 2011-11-04
Ok, that works and teaches me a bit. The SDL tutorial I was using said to make a .cpp file, I found that kind of strange as well. Also, if I want to write this in CPP, how differently would I have to code it and what would I pass to g++ to make it use SDL?

---

### Post by pbrane on 2011-11-04
Put all the code in a .cpp file.

```

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <math.h>
#include <SDL_mixer.h>
#include <SDL.h>


#define FIGURES 240
#define POINTS 10

int xpos[FIGURES][POINTS];
int ypos[FIGURES][POINTS];


void Slock(SDL_Surface *screen)
{
  if ( SDL_MUSTLOCK(screen) )
  {
    if ( SDL_LockSurface(screen) < 0 )
    {
      return;
    }
  }
}

void Sulock(SDL_Surface *screen)
{
  if ( SDL_MUSTLOCK(screen) )
  {
    SDL_UnlockSurface(screen);
  }
}

void DrawPixel(SDL_Surface *screen, int x, int y, Uint8 R, Uint8 G, Uint8 B)
{
  Uint32 color = SDL_MapRGB(screen->format, R, G, B);
  switch (screen->format->BytesPerPixel)
  {
    case 1: // Assuming 8-bpp
      {
        Uint8 *bufp;
        bufp = (Uint8 *)screen->pixels + y*screen->pitch + x;
        *bufp = color;
      }
      break;
    case 2: // Probably 15-bpp or 16-bpp
      {
        Uint16 *bufp;
        bufp = (Uint16 *)screen->pixels + y*screen->pitch/2 + x;
        *bufp = color;
      }
      break;
    case 3: // Slow 24-bpp mode, usually not used
      {
        Uint8 *bufp;
        bufp = (Uint8 *)screen->pixels + y*screen->pitch + x * 3;
        if(SDL_BYTEORDER == SDL_LIL_ENDIAN)
        {
          bufp[0] = color;
          bufp[1] = color >> 8;
          bufp[2] = color >> 16;
        } else {
          bufp[2] = color;
          bufp[1] = color >> 8;
          bufp[0] = color >> 16;
        }
      }
      break;
    case 4: // Probably 32-bpp
      {
        Uint32 *bufp;
        bufp = (Uint32 *)screen->pixels + y*screen->pitch/4 + x;
        *bufp = color;
      }
      break;
  }
}

void DrawScene(SDL_Surface *screen)
{
  Slock(screen);
  for(int x=0;x<640;x++)
  {
    for(int y=0;y<480;y++)
    {
      DrawPixel(screen, x,y,y/2,y/2,x/3);
    }
  }
  Sulock(screen);
  SDL_Flip(screen);
}

int graphics()
{

  if ( SDL_Init(SDL_INIT_AUDIO|SDL_INIT_VIDEO) < 0 )
  {
    printf("Unable to init SDL: %s\n", SDL_GetError());
    exit(1);
  }
  atexit(SDL_Quit);

  SDL_Surface *screen;
  screen=SDL_SetVideoMode(640,480,32,SDL_HWSURFACE|SDL_DOUBLEBUF);
  if ( screen == NULL )
  {
    printf("Unable to set 640x480 video: %s\n", SDL_GetError());
    exit(1);
  }
  int done=0;

  while(done == 0)
  {
    SDL_Event event;

    while ( SDL_PollEvent(&event) )
    {
      if ( event.type == SDL_QUIT )  {  done = 1;  }

      if ( event.type == SDL_KEYDOWN )
      {
        if ( event.key.keysym.sym == SDLK_ESCAPE ) { done = 1; }
      }
    }

    DrawScene(screen);
  }

  return 0;
}

int main(int argc, char *argv[])
{
  graphics();
  return 0;
}


```

Compile like this.
```

g++ -Wall graphix.cpp $(sdl-config --cflags --libs) -o graphix

```

---

### Post by compiz addict on 2011-11-05
Awesome! thanks! Not finding any need for using C++ yet though, as everything I'm doing seems to work well in C. I recently came up with an awesome 2D game idea and wanted to start coding it right away (my usual approach to things like this), so that's my explanation for any noobish questions.

---

