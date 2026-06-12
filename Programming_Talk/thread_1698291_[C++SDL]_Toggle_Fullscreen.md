---
title: "[C++/SDL] Toggle Fullscreen"
date: 2011-03-02
forum: Programming Talk
---

### Post by dodle on 2011-03-02
I figured out what I think to be a cross-platform way to toggle fullscreen in an SDL window and created a header file for it, but I am a novice programmer. Would someone mind checking my code for errors?

SDLToggleFS.h:
[php]// Cross-platform Toggle FullScreen for an SDL Window

#ifndef _SDL_TOGGLE_FS
    #define _SDL_TOGGLE_FS

#define SDL_WIN_SETTINGS surface->w, surface->h, surface->format->BitsPerPixel

// Check if SDL is already loaded
#ifndef _SDL_H
    #include <SDL/SDL.h>
#endif

int IsFullScreen(SDL_Surface *surface)
{
    if (surface->flags & SDL_FULLSCREEN) return 1; // return true if surface is fullscreen
    return 0; // Return false if surface is windowed
}

int SDL_ToggleFS(SDL_Surface *surface)
{
    Uint32 flags = surface->flags; // Get the video surface flags
    
    if (IsFullScreen(surface))
    {
        // Swith to WINDOWED mode
        if ((surface = SDL_SetVideoMode(SDL_WIN_SETTINGS, flags -= SDL_FULLSCREEN)) == NULL) return 0;
        return 1;
    }
    
    // Swith to FULLSCREEN mode
    if ((surface = SDL_SetVideoMode(SDL_WIN_SETTINGS, flags|SDL_FULLSCREEN)) == NULL) return 0;
    return 1;
}

#endif[/php]

So far it works on both Ubuntu and Win32.

**Note:** This is for SDL 1.2, version 1.3 has a functions called SDL_SetWindowFullscreen.

---

### Post by dodle on 2011-03-03
*bump* I am just really worried there might be errors in this code because I am not experienced. I don't want to cause in problems on my computer.

**Edit:** It would also be nice if someone could confirm for me whether or not it works on Mac OS

---

### Post by dodle on 2011-04-28
I'm reviving this thread because my code is not working now. I have simplified SDLToggleFS.h (I didn't realize how simple toggling fs was).

[php]// Cross-platform Toggle FullScreen for an SDL Window

#ifndef _SDL_TOGGLE_FS
    #define _SDL_TOGGLE_FS

#include <SDL/SDL.h>

static int SDL_ToggleFS(SDL_Surface *surface)
{
    Uint32 flags = surface->flags; // Get the video surface flags
    
    if (flags & SDL_FULLSCREEN) flags &= ~SDL_FULLSCREEN;
    else flags = flags|SDL_FULLSCREEN;
    
    if ((surface = SDL_SetVideoMode(surface->w, surface->h, surface->format->BitsPerPixel, flags)) == NULL) return 0;
    return 1;
}

#endif[/php]

If I make a call to SDL_ToggleFS(SDL_Surface*) it will toggle into fullscreen but not out of it. It works fine if I put the code into my main .cpp file:

[php]#include <SDL/SDL.h>

int main(int argc, char** argv)
{
    if (SDL_Init(SDL_INIT_VIDEO) < 0) return 1;
    
    SDL_Surface *surface;
    SDL_Event event;
    SDLKey key;
    int running = 1;
    Uint32 flags;
    
    if ((surface = SDL_SetVideoMode(800, 500, 24, SDL_HWSURFACE|SDL_DOUBLEBUF)) == 0) return 1;
    
    while (running)
    {
        while (SDL_PollEvent(&event))
        {
            flags = surface->flags;
            key = event.key.keysym.sym;
            
            if ((event.type == SDL_QUIT) || (key == SDLK_ESCAPE)) running = 0;
            
            if (event.type == SDL_KEYDOWN)
            {
                if (key == SDLK_RETURN)
                {
                    if (flags & SDL_FULLSCREEN)
                    {
                        if ((surface = SDL_SetVideoMode(800, 500, 24, flags &= ~SDL_FULLSCREEN)) == 0) return 1;
                    }
                    else if ((surface = SDL_SetVideoMode(800, 500, 24, flags|SDL_FULLSCREEN)) == 0) return 1;
                }
            }
        }
    }
    
    SDL_Quit();
    
    return 0;
}[/php]

Would somebody help me figure out what is going on?

**------ Edit ------**

NVM, got it figured out: [http://forums.libsdl.org/viewtopic.php?t=7033&highlight=toggle+fullscreen](http://forums.libsdl.org/viewtopic.php?t=7033&highlight=toggle+fullscreen)

[php]// Cross-platform Toggle FullScreen for an SDL Window

#ifndef _SDL_TOGGLE_FS
    #define _SDL_TOGGLE_FS

#include <SDL/SDL.h>

static SDL_Surface* SDL_ToggleFS(SDL_Surface *surface)
{
    Uint32 flags = surface->flags; // Get the video surface flags
    flags ^= SDL_FULLSCREEN;
    
    return SDL_SetVideoMode(surface->w, surface->h, surface->format->BitsPerPixel, flags);
}

#endif[/php]

---

