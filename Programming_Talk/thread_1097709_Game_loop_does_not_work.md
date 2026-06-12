---
title: "Game loop does not work"
date: 2009-03-16
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-03-16
I got this:
```

int main( int argc, char *argv[] )
{
    const int TICKS_PER_SECOND = 25;
    const int SKIP_TICKS = 1000 / TICKS_PER_SECOND;
    const int MAX_FRAMESKIP = 5;
    
    unsigned int next_game_tick = SDL_GetTicks();
    float interpolation;
    int loops;
    
    SDL_Event event;
    SDL_Surface *screen = NULL;
    screen = SDL_SetVideoMode( 640, 480, 32, SDL_HWSURFACE );
    bool running = true;
    
    while ( running )
    {
        while( SDL_PollEvent( &event ) )
        {
            if ( event.type == SDL_QUIT )
                running = false;
        }
        
        
        loops = 0;
        while( SDL_GetTicks() > next_game_tick && loops < MAX_FRAMESKIP )
        {
            printf( "updating\n" );
            // update_game();
            
            next_game_tick += SKIP_TICKS;
            loops ++;
        }
        
        interpolation = float( SDL_GetTicks() + SKIP_TICKS - next_game_tick ) / float( SKIP_TICKS );
        
        // display_game( interpolation );
    }
    
    return 0;
}

```

That's actually same than here: [http://dewitters.koonsolo.com/gameloop.html](http://dewitters.koonsolo.com/gameloop.html) (the last one)

But it doesn't work. It never prints "updating". And interpolation isn't anything between 0 and 1. It was 100898840.0 when I checked it.

Why? What's wrong? I read trough the code, line by line, but I just don't get it. :confused:

---

### Post by dwhitney67 on 2009-03-16
I had to clean up your code to compile; in fact, I'm surprised you were able to compile what you had posted.

Anyhow, I got the result that you were looking for... that is, the "updating".

Here's the code:
```

#include <SDL/SDL.h>
#include <stdbool.h>
#include <stdio.h>

int main(int argc, char** argv)
{
  const int TICKS_PER_SECOND = 25;
  const int SKIP_TICKS = 1000 / TICKS_PER_SECOND;
  const int MAX_FRAMESKIP = 5;

  SDL_Event    event;
  SDL_Surface* screen = SDL_SetVideoMode(640, 480, 32, SDL_HWSURFACE);
  unsigned int next_game_tick = SDL_GetTicks();
  bool         running = true;

  while (running)
  {
    while (SDL_PollEvent(&event))
    {
      if (event.type == SDL_QUIT)
        running = false;
    }

    for (int loops = 0; (SDL_GetTicks() > next_game_tick) && (loops < MAX_FRAMESKIP); ++loops)
    {
      printf("updating\n");

      //update_game();

      next_game_tick += SKIP_TICKS;
    }

    float interpolation = (SDL_GetTicks() + SKIP_TICKS - next_game_tick) / (float)SKIP_TICKS;

    printf("interpolation = %f\n", interpolation);

    //display_game(interpolation);
  }

  return 0;
}

```

P.S.  I used -std=gnu99 as a GCC compiler option.  I assume you are developing in C, since you are using the printf().

---

### Post by crazyfuturamanoob on 2009-03-16
Thanks. :) I don't see anything done much different, why your code works but mine (deWiTTERS') doesn't?

And I use C++, but I use printf because I don't like cout. Why C++ has new printing functions when old ones work good?


Edit: I changed main.cpp in this larger program for testing, because was too lazy to create new makefiles and stuff for new testing program. 

I ran the code I posted in first post with gdb, and next_game_tick gets value 276296907, when SDL_GetTicks() is 36952. Some kind of memory error?

---

### Post by dwhitney67 on 2009-03-16
Ok, your original code, with the exception of one line that I changed (not including header files).  I'll let you hunt for it.
```

#include <SDL/SDL.h>
#include <cstdio>

int main( int argc, char *argv[] )
{
    const int TICKS_PER_SECOND = 25;
    const int SKIP_TICKS = 1000 / TICKS_PER_SECOND;
    const int MAX_FRAMESKIP = 5;

    float interpolation;
    int loops;

    SDL_Event event;
    SDL_Surface *screen = NULL;
    screen = SDL_SetVideoMode( 640, 480, 32, SDL_HWSURFACE );
    bool running = true;
    unsigned int next_game_tick = SDL_GetTicks();

    while ( running )
    {
        while( SDL_PollEvent( &event ) )
        {
            if ( event.type == SDL_QUIT )
                running = false;
        }


        loops = 0;
        while( SDL_GetTicks() > next_game_tick && loops < MAX_FRAMESKIP )
        {
            printf( "updating\n" );
            // update_game();

            next_game_tick += SKIP_TICKS;
            loops ++;
        }

        interpolation = float( SDL_GetTicks() + SKIP_TICKS - next_game_tick ) / float( SKIP_TICKS );

        // display_game( interpolation );
    }

    return 0;
}

```

---

### Post by crazyfuturamanoob on 2009-03-17
```

....

void gameObject::run( int argc, char *argv[] )
{
    const int TICKS_PER_SECOND = 25;
    const int SKIP_TICKS = 1000 / TICKS_PER_SECOND;
    const int MAX_FRAMESKIP = 5;
    
    bool running = true;
    unsigned int next_game_tick = SDL_GetTicks();
    SDL_Event event;
    
    // get a window, initalize SDL and opengl and setup a 2d view
    if( init_sdl_gl( screen, SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP ) != 1 )
        return;
    
    SDL_ShowCursor( SDL_DISABLE );
    
    printf( "next_game_tick is %u\nSDL_GetTicks() returned %u\n", next_game_tick, SDL_GetTicks() );
    
    while( running )
    {
        .......

```
See code above. It will not update, just redraw everything, and prints this at beginning:
> 
next_game_tick is 347984751
SDL_GetTicks() returned 209

Does not make sense. But if I swap two lines so it looks like this:
```

void gameObject::run( int argc, char *argv[] )
{
    const int TICKS_PER_SECOND = 25;
    const int SKIP_TICKS = 1000 / TICKS_PER_SECOND;
    const int MAX_FRAMESKIP = 5;
    
    bool running = true;
**    // moved next_game_tick declaration from here**
    SDL_Event event;
    
    // get a window, initalize SDL and opengl and setup a 2d view
    if( init_sdl_gl( screen, SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP ) != 1 )
        return;
    
**    unsigned int next_game_tick = SDL_GetTicks();**

    SDL_ShowCursor( SDL_DISABLE );

```
It starts working, and both SDL_GetTicks() and next_game_tick are equal (140).

Creepy. How can I find this bug?

---

### Post by dwhitney67 on 2009-03-17
That's what I discovered yesterday, thru trial n' error.

It's helpful to read the man-page for SDL_GetTicks():
```

SDL_GetTicks(3)                         SDL API Reference                         SDL_GetTicks(3)

NAME
       SDL_GetTicks- Get the number of milliseconds since the SDL library initialization.

SYNOPSIS
       #include "SDL.h"

       Uint32 SDL_GetTicks(void)

DESCRIPTION
       Get  the number of milliseconds since the SDL library initialization. Note that this value
       wraps if the program runs for more than ~49 days.

SEE ALSO
       SDL_Delay

SDL                                   Tue 11 Sep 2001, 23:01                      SDL_GetTicks(3)

```
The word "since" of the first sentence of the DESCRIPTION is the key.  There probably should be a note to indicate that if an attempt is made to call SDL_GetTicks() prior to initialization, the return value is undefined.

---

### Post by crazyfuturamanoob on 2009-03-17
Wow! Never thought of that. I was looking for some errors with string handling from other source files. Thanks :D

---

