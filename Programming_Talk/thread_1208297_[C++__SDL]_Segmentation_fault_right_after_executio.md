---
title: "[C++ / SDL] Segmentation fault right after execution !"
date: 2009-07-09
forum: Programming Talk
---

### Post by credobyte on 2009-07-09
Do you see any mistakes/bugs ? I run it, window appears and closes with "Segmentation fault" .. why ? :-k

```
#include "SDL.h"

int main ( int argc, char *argv[] )
{
  SDL_Init(SDL_INIT_VIDEO);
  SDL_WM_SetCaption("SDL Test", "SDL Test");
  SDL_Surface* screen = SDL_SetVideoMode(640, 480, 0, 0);
  SDL_Surface* temp = SDL_LoadBMP("sdl_logo.bmp");
  SDL_Surface* bg = SDL_DisplayFormat(temp);
  SDL_FreeSurface(temp);

  SDL_Event event;
  int gameover = 0;

  while (!gameover)
  {
    if (SDL_PollEvent(&event)) {
      switch (event.type) {
        case SDL_QUIT:
          gameover = 1;
          break;

        case SDL_KEYDOWN:
          switch (event.key.keysym.sym) {
            case SDLK_ESCAPE:
            case SDLK_q:
              gameover = 1;
              break;
          }
          break;
      }
    }

    SDL_BlitSurface(bg, NULL, screen, NULL);
    SDL_UpdateRect(screen, 0, 0, 0, 0);
  }

  SDL_FreeSurface(bg);
  SDL_Quit();

  return 0;
}

```[COLOR=Red]**Update:** Problem solved ( logo was missing ).[/COLOR]

---

### Post by boblemur on 2009-07-09
remember to mark as solved

---

### Post by rockachu2 on 2011-07-29
Happened to me too. Remember image capitalization counts.

---

### Post by Wim Sturkenboom on 2011-07-30
Thread is 2 years old :D

---

