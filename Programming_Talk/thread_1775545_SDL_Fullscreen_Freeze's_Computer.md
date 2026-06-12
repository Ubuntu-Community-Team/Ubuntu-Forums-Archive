---
title: "SDL Fullscreen Freeze's Computer"
date: 2011-06-04
forum: Programming Talk
---

### Post by pheserus on 2011-06-04
I've been trying to make SDL use fullscreen on Xubuntu and it more often then not will 
go into fullscreen but not render anything, as if it did nothing but change the screen
resolution. And when the application closes, it leaves the computer in a frozen state.
I can see all my windows and desktop and everything, but I can not interact. It doesn't 
always do this. After rebooting, I can launch the application and it will work perfectly.
But I can never get it to do so more than once until I reboot. Strangely, it works flawlessly
 on Ubuntu in virtualbox, every time.

I've been testing it with this simple & small application.
```
#include <SDL/SDL.h>

int main(int argc, char* args[])
{
    SDL_Init(SDL_INIT_EVERYTHING);
    
    SDL_Surface *screen = SDL_SetVideoMode(800, 600, 32, SDL_SWSURFACE | SDL_FULLSCREEN);
    
    SDL_Rect square = { 350,250,100,100 };
    
    SDL_Rect background = { 0,0,800,600 };
    
    SDL_FillRect(screen, &background, SDL_MapRGB(screen->format, 255, 255, 255));
    
    SDL_FillRect(screen, &square, SDL_MapRGB(screen->format, 255, 0, 0));
    
    SDL_Flip(screen);
    
    SDL_Delay(10000);
    
    SDL_FreeSurface(screen);
    
    SDL_Quit();
    
    return 0;
}
```Am I doing something wrong? What could possibly be the problem?
Hardware? Video Settings? My Monitor?

---

### Post by Petrolea on 2011-06-06
I can't try atm, but try adding SDL_DOUBLEBUF to video mode (should still work without though). Also try 16 bits color mode.

---

### Post by Zugzwang on 2011-06-06
You might have probek gfx card drivers or so. Try to disable the desktop effects in the "Appearance" settings of Ubuntu.

---

