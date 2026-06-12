---
title: "[C++] &quot;Expected Unqualified-id...&quot;"
date: 2011-02-28
forum: Programming Talk
---

### Post by dodle on 2011-02-28
I'm having trouble compiling some code. I think I've solved this problem before but can't remember how.

test.cpp:
[php]#include <SDL/SDL.h>

SDL_Surface *window;
SDL_Event event;

// Main Window attributes
int const MW_WIDTH = 640;
int const MW_HEIGHT = 480;
int const MW_BPP = 32;

int Init();
{
    // Initialize SDL
    if (SDL_Init(SDL_INIT_EVERYTHING) == NULL) return 1;
    return 0;
}

int Cleanup();
{
    // Free up memory and close
    SDL_FreeSurface(window);
    SDL_Quit();
    return 0;
}

int main(int argc, char* argv[])
{
    if (Init()) return 1;

    SDL_Surface *window;

    window = SDL_SetVideoMode(MW_WIDTH, MW_HEIGHT, MW_BPP, SDL_HWSURFACE|SDL_DOUBLEBUF);

    bool running = true;

    while (running)
    {
        while (SDL_PollEvent(&event))
        {
            if (event.type = SDL_QUIT) running = false;
        }
    }

    Cleanup();
    return 0;
}[/php]

compiler output:
```
$ g++ test.cpp -o test -lSDL
test.cpp:12: error: expected unqualified-id before ‘{’ token
test.cpp:19: error: expected unqualified-id before ‘{’ token
make: *** [test] Error 1
```

The problems occur in the functions [color=red]Init()[/color] and [color=red]Cleanup()[/color].

---

### Post by Arndt on 2011-02-28
> **dodle said:**
> I'm having trouble compiling some code. I think I've solved this problem before but can't remember how.

test.cpp:
[php]#include <SDL/SDL.h>

SDL_Surface *window;
SDL_Event event;

// Main Window attributes
int const MW_WIDTH = 640;
int const MW_HEIGHT = 480;
int const MW_BPP = 32;

int Init();
{
    // Initialize SDL
    if (SDL_Init(SDL_INIT_EVERYTHING) == NULL) return 1;
    return 0;
}

int Cleanup();
{
    // Free up memory and close
    SDL_FreeSurface(window);
    SDL_Quit();
    return 0;
}

int main(int argc, char* argv[])
{
    if (Init()) return 1;

    SDL_Surface *window;

    window = SDL_SetVideoMode(MW_WIDTH, MW_HEIGHT, MW_BPP, SDL_HWSURFACE|SDL_DOUBLEBUF);

    bool running = true;

    while (running)
    {
        while (SDL_PollEvent(&event))
        {
            if (event.type = SDL_QUIT) running = false;
        }
    }

    Cleanup();
    return 0;
}[/php]

compiler output:
```
$ g++ test.cpp -o test -lSDL
test.cpp:12: error: expected unqualified-id before ‘{’ token
test.cpp:19: error: expected unqualified-id before ‘{’ token
make: *** [test] Error 1
```

The problems occur in the functions [color=red]Init()[/color] and [color=red]Cleanup()[/color].

The error message is certainly not helpful, but when you write

```
int Init();
{
```

it should be

```
int Init()
{ 

```

---

### Post by dodle on 2011-02-28
Geez, I'm sorry, I should have seen that. Thanks for pointing out my foolishness... :)

---

