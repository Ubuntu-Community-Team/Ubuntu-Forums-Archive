---
title: "printf not doing anything in C++ and SDL"
date: 2011-05-01
forum: Programming Talk
---

### Post by faillord adam on 2011-05-01
I'm trying to make a simple Space Invaders game, but when I try to print instructions to the player, nothing happens.

Here's my code:
```
#ifdef __cplusplus
    #include <cstdlib>
#else
    #include <stdlib.h>
#endif
#ifdef __APPLE__
    #include <SDL/SDL.h>
#else
    #include <SDL/SDL.h>
#endif
#include <iostream>

int main ( int argc, char** argv )
{
    // initialize SDL video
    if ( SDL_Init( SDL_INIT_VIDEO ) < 0 )
    {
        printf( "Unable to init SDL: %s\n", SDL_GetError() );
        return 1;
    }

    // make sure SDL cleans up before exit
    atexit(SDL_Quit);

    // create a new window
    SDL_Surface* screen = SDL_SetVideoMode(640, 480, 16,
                                           SDL_HWSURFACE|SDL_DOUBLEBUF);
    if ( !screen )
    {
        printf("Unable to set 640x480 video: %s\n", SDL_GetError());
        return 1;
    }

    // program main loop
    bool done = false;
    while (!done)
    {
        // message processing loop
        SDL_Event event;
        while (SDL_PollEvent(&event))
        {
            // check for messages
            switch (event.type)
            {
                // exit if the window is closed
            case SDL_QUIT:
                done = true;
                break;

                // check for keypresses
            case SDL_KEYDOWN:
                {
                    // exit if ESCAPE is pressed
                    if (event.key.keysym.sym == SDLK_ESCAPE)
                        done = true;
                    break;
                }

                    {
                        printf("Press ESC to exit/nUse the left and right keys to move/nCLick to fire/n");
                    }
            } // end switch
        } // end of message processing

        // DRAWING STARTS HERE

        // clear screen
        SDL_FillRect(screen, 0, SDL_MapRGB(screen->format, 0, 0, 0));

        // DRAWING ENDS HERE

        // finally, update the screen :)
        SDL_Flip(screen);
    } // end main loop

    // all is well ;)
    printf("Thank you for playing Space Invaders\n");
    return 0;
}

```

What's wrong?

---

### Post by Arndt on 2011-05-01
> **faillord adam said:**
> I'm trying to make a simple Space Invaders game, but when I try to print instructions to the player, nothing happens.

Here's my code:
```
#ifdef __cplusplus
    #include <cstdlib>
#else
    #include <stdlib.h>
#endif
#ifdef __APPLE__
    #include <SDL/SDL.h>
#else
    #include <SDL/SDL.h>
#endif
#include <iostream>

int main ( int argc, char** argv )
{
    // initialize SDL video
    if ( SDL_Init( SDL_INIT_VIDEO ) < 0 )
    {
        printf( "Unable to init SDL: %s\n", SDL_GetError() );
        return 1;
    }

    // make sure SDL cleans up before exit
    atexit(SDL_Quit);

    // create a new window
    SDL_Surface* screen = SDL_SetVideoMode(640, 480, 16,
                                           SDL_HWSURFACE|SDL_DOUBLEBUF);
    if ( !screen )
    {
        printf("Unable to set 640x480 video: %s\n", SDL_GetError());
        return 1;
    }

    // program main loop
    bool done = false;
    while (!done)
    {
        // message processing loop
        SDL_Event event;
        while (SDL_PollEvent(&event))
        {
            // check for messages
            switch (event.type)
            {
                // exit if the window is closed
            case SDL_QUIT:
                done = true;
                break;

                // check for keypresses
            case SDL_KEYDOWN:
                {
                    // exit if ESCAPE is pressed
                    if (event.key.keysym.sym == SDLK_ESCAPE)
                        done = true;
                    break;
                }

                    {
                        printf("Press ESC to exit/nUse the left and right keys to move/nCLick to fire/n");
                    }
            } // end switch
        } // end of message processing

        // DRAWING STARTS HERE

        // clear screen
        SDL_FillRect(screen, 0, SDL_MapRGB(screen->format, 0, 0, 0));

        // DRAWING ENDS HERE

        // finally, update the screen :)
        SDL_Flip(screen);
    } // end main loop

    // all is well ;)
    printf("Thank you for playing Space Invaders\n");
    return 0;
}

```

What's wrong?

Is the printf in question actually reached?

---

### Post by gusnan on 2011-05-01
How are you starting your program? If you are starting it from your desktop by double-clicking the programs icon, you won't see the output of your printf's. On the other hand, if you are starting it from a terminal, or from an IDE, the output should be visible.

(If all worked fine, at least the "Thank you for playing Space Invaders\n" message should be shown.)

---

