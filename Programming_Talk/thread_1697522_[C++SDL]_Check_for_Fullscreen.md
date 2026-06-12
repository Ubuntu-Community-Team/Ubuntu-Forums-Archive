---
title: "[C++/SDL] Check for Fullscreen"
date: 2011-02-28
forum: Programming Talk
---

### Post by dodle on 2011-02-28
Is there a way to check if an SDL window is in fullscreen? Right now I am just setting a boolean variable when I put it in fullscreen.

[php]#define WN 640, 480, 32, SDL_HWSURFACE|SDL_DOUBLEBUF
#define FS 640, 480, 32, SDL_HWSURFACE|SDL_DOUBLEBUF|SDL_FULLSCREEN

SDL_Surface *MWindow;

bool fullscreen = false;

if (fullscreen)
{
    fullscreen = false;
    MWindow = SDL_SetVideoMode(WN);
}
else
{
    fullscreen = true;
    MWindow = SDL_SetVideoMode(FS);
}[/php]

**Edit:** SDL has the function [color=red]SDL_WM_ToggleFullscreen[/color]. But it only works for X11, I am looking for something that is cross-platform.

---

### Post by foxmuldr on 2011-03-01
> **dodle said:**
> Is there a way to check if an SDL window is in fullscreen?

Just a couple thoughts...

Is there a way to query the dimensions of the root window and the current window and see if they're the same? And possibly a way to find out if the client area of the window is the same size as the physical window area, indicating there is no border?

- Rick C. Hodgin

---

### Post by dodle on 2011-03-01
I can get the size of the window using m and w:

[php]#define WN 640, 480, 32, SDL_HWSURFACE|SDL_DOUBLEBUF
#define FS 640, 480, 32, SDL_HWSURFACE|SDL_DOUBLEBUF|SDL_FULLSCREEN

SDL_Surface *MWindow;
int width;
int height;

bool fullscreen = false;

if (fullscreen)
{
    fullscreen = false;
    MWindow = SDL_SetVideoMode(WN);
}
else
{
    fullscreen = true;
    MWindow = SDL_SetVideoMode(FS);
}

width = MWindow->w;
height = MWindow->h;[/php]

But I have no clue how to get size of the (screen/client area?), I assume that is platform specific.

---

### Post by dodle on 2011-03-02
SOLVED! I was able to check for fullscreen with:

[php](SDL_Surface->flags & SDL_FULLSCREEN);[/php]

Example code:
[php]#include <iostream>
#include <SDL/SDL.h>
using namespace std;

int IsFullScreen(SDL_Surface *surface)
{
    // Return true if fullscreen
    if (surface->flags & SDL_FULLSCREEN) return 1;
    
    // Return false if windowed
    return 0;
}

int main()
{
    SDL_Surface *mwindow;
    
    // Start SDL
    if (SDL_Init(SDL_INIT_EVERYTHING) < 0) return 1;
    
    // Create a video surface
    if ((mwindow = SDL_SetVideoMode(800, 600, 32, SDL_HWSURFACE|SDL_DOUBLEBUF|SDL_FULLSCREEN)) == NULL) return 1;
    
    // Check if the surface is in fullscreen
    if (IsFullScreen(mwindow)) cout << "Fullscreen\n";
    else cout << "Windowed\n";
    
    // Cleanup
    SDL_FreeSurface(mwindow);
    SDL_Quit();
    
    return 0;
}[/php]

---

