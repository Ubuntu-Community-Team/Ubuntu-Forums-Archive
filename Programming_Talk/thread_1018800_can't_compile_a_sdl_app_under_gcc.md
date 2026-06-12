---
title: "can't compile a sdl app under gcc"
date: 2008-12-22
forum: Programming Talk
---

### Post by ben@layer on 2008-12-22
when I ever try to compile a sdl program under sdl I get this 
```

moe@moe-laptop:~$ gcc sdl.c
sdl.c:7: error: expected identifier or ‘(’ before ‘if’
sdl.c:12: warning: data definition has no type or storage class
sdl.c:12: warning: parameter names (without types) in function declaration
sdl.c:17: warning: data definition has no type or storage class
sdl.c:17: error: conflicting types for ‘screen’
sdl.c:3: error: previous declaration of ‘screen’ was here
sdl.c:17: error: ‘scale’ undeclared here (not in a function)
sdl.c:17: error: ‘x’ undeclared here (not in a function)
sdl.c:17: error: ‘y’ undeclared here (not in a function)
sdl.c:17: warning: initialization makes integer from pointer without a cast
sdl.c:17: error: initializer element is not constant
sdl.c:18: error: expected identifier or ‘(’ before ‘if’
sdl.c:29: error: expected identifier or ‘(’ before ‘while’
sdl.c:39: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘:’ token
moe@moe-laptop:~$ 
```

heres the sorce file

---

### Post by mike_g on 2008-12-22
You forgot to put your prog in the main() function. IE:
```
#include "SDL/SDL.h"
#include <stdio.h>
SDL_Surface* screen;
SDL_Surface* image;
SDL_Rect src , dest;

[COLOR="Red"]int main()
{[/COLOR]
   if(SDL_Init(SDL_INIT_VIDEO) != 0)
   {
       printf("Unable to init SDL: %s\n" , SDL_GetError());
      return(1);
   }
   atexit(SDL_Quit);

//x and y are the dimensions of our map, and we render each map-square as an image of 4x4 white pixels - (scale == 4)
//we want a 16 bit color model, so we don't have to mess with a palette
//the last parameter 0 gives us a rendering surface in a window
   screen = SDL_SetVideoMode(scale * x , scale * y , 16 , 0);
   if(screen == NULL)
   {
   printf("Unable to set video mode: %s\n" , SDL_GetError());
      return(1);
   }

//do something here
//...and here

//now wait for the user to close the window
   SDL_Event event;
   while(SDL_WaitEvent(&event) != 0)
   {
      switch(event.type)
      {
      case (SDL_QUIT):
         SDL_FreeSurface(image);
         goto jump;
      }
//we handle only the one event
   }
   jump: SDL_Quit();
[COLOR="Red"]}[/COLOR]
```
Also, you might want to look at getting rid of the goto; gotos are generally avoided wherever possible. Not sure if your prog works yet; I havent tested it, but you definitely need to have a main function ;)

---

