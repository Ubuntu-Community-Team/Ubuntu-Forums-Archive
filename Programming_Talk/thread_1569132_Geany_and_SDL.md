---
title: "Geany and SDL"
date: 2010-09-06
forum: Programming Talk
---

### Post by Iubdou on 2010-09-06
I'm using a development environment called Geany that handles multiple languages and since I'm taking a variety of programming courses it seemed appropriate to go for this one, but I can't for the life of me get SDL to play nice with it. I've tried various fixes ranging from reinstalling packages to trying to link it by hand but nothing is working so here's the original error output and the code that generated it. Maybe someone can shed some light on this for me.

//Include SDL functions and datatypes
#include "SDL/SDL.h" 
int main( int argc, char* args[] ) {
    //The images
    SDL_Surface* hello = NULL;
    SDL_Surface* screen = NULL; 
    //Start SDL
    SDL_Init( SDL_INIT_EVERYTHING );
    //Set up screen
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

gcc -Wall -o "BasicSDL" "BasicSDL.c" (in directory: *omitted: irrelevant to error*)
/tmp/ccV8txp6.o: In function `main':
BasicSDL.c:(.text+0x25): undefined reference to `SDL_Init'
BasicSDL.c:(.text+0x3e): undefined reference to `SDL_SetVideoMode'
BasicSDL.c:(.text+0x51): undefined reference to `SDL_RWFromFile'
BasicSDL.c:(.text+0x5e): undefined reference to `SDL_LoadBMP_RW'
BasicSDL.c:(.text+0x7c): undefined reference to `SDL_UpperBlit'
BasicSDL.c:(.text+0x88): undefined reference to `SDL_Flip'
BasicSDL.c:(.text+0x92): undefined reference to `SDL_Delay'
BasicSDL.c:(.text+0x9e): undefined reference to `SDL_FreeSurface'
BasicSDL.c:(.text+0xa3): undefined reference to `SDL_Quit'
collect2: ld returned 1 exit status
Compilation failed.

---

### Post by dv3500ea on 2010-09-06
You need to link your program to SDL using the -lSDL flag.

You need to go to _Build -> Set Includes and Arguments_ in geany and add the -lSDL flag (see attachment).

---

### Post by slavik on 2010-09-06
and please use code tags for the code. :)

---

### Post by Iubdou on 2010-09-06
Well, it compiles fine now, but it doesn't build properly. Yay.

Build outputs the following errors.

g++ -Wall -o "lesson01" "lesson01.cpp" -ISDL (in directory: A place)
/tmp/ccjJz8o4.o: In function `main':
lesson01.cpp:(.text+0x25): undefined reference to `SDL_Init'
lesson01.cpp:(.text+0x3e): undefined reference to `SDL_SetVideoMode'
lesson01.cpp:(.text+0x51): undefined reference to `SDL_RWFromFile'
lesson01.cpp:(.text+0x5e): undefined reference to `SDL_LoadBMP_RW'
lesson01.cpp:(.text+0x7c): undefined reference to `SDL_UpperBlit'
lesson01.cpp:(.text+0x88): undefined reference to `SDL_Flip'
lesson01.cpp:(.text+0x92): undefined reference to `SDL_Delay'
lesson01.cpp:(.text+0x9e): undefined reference to `SDL_FreeSurface'
lesson01.cpp:(.text+0xa3): undefined reference to `SDL_Quit'
collect2: ld returned 1 exit status
Compilation failed.

---

### Post by Iubdou on 2010-09-06
Also, in future I will. Sorry about that, I hardly ever use web forums and despite browsing this one for tips and solutions I haven't gotten the hang of the syntax just yet.

---

### Post by slavik on 2010-09-06
add -lsdl in the build args.

---

### Post by dv3500ea on 2010-09-07
> **Iubdou said:**
> 
g++ -Wall -o "lesson01" "lesson01.cpp" -ISDL


Use -**l**SDL not -**I**SDL.

It is an l, which stands for 'link'.

---

### Post by slavik on 2010-09-07
> **dv3500ea said:**
> Use -**l**SDL not -**I**SDL.

It is an l, which stands for 'link'.
l = lowercase el ;)

---

### Post by Iubdou on 2010-09-07
And with that it works perfectly. Thank you all very much, now I know there are people I can turn to if I ever have such difficulties again. You'd all get free cookies if I knew where to send them to.

---

