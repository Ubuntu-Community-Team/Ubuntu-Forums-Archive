---
title: "c++ sdl basic program problem"
date: 2011-09-02
forum: Programming Talk
---

### Post by Schweinessener on 2011-09-02
i installed Code::blocks from the software center and made an SDL project in code::blocks. the basic program thats written there when you first create the project works perfectly (it displays the code blocks logo in the window and everything) and thus sdl works. after i put this simple code in however:
#include "SDL/SDL.h"

int main(int argc, char* args[])
{
    SDL_Surface* hello = NULL;
    SDL_Surface* screen = NULL;

    SDL_Init(SDL_INIT_EVERYTHING);

    screen = SDL_SetVideoMode(640, 480, 32, SDL_SWSURFACE);
    hello = SDL_LoadBMP("/home/ted/Pictures/Code Project Images/SDL_example/hello.bmp");

    SDL_BlitSurface( hello, NULL, screen, NULL );

    SDL_Flip(screen);

    SDL_Delay(2000);

    SDL_FreeSurface(hello);

    SDL_Quit();

    return 0;
}
a blank, black window appears and no image appears. i have made 'hello.bmp' in gimp and ive saved it where the path i provided specifies. why does this happen, and how can i fix this? (following lazy foos tuts btw.)

---

### Post by Smart Viking on 2011-09-03
That works for me. Something wrong with the image maybe?

```
libsdl = 1.2.14-6.1
gcc version 4.4.5 (Debian 4.4.5-8)
```

Compiled with
```
c++ -lSDLmain -lSDL omg.cpp -o omg
```Used #include <SDL/SDL.h>, instead of #include "SDL/SDL.h"

---

### Post by Schweinessener on 2011-09-03
switching it from the "SDL/SDL.h" to <SDL/SDL.h> actually worked, haha, thanks

---

