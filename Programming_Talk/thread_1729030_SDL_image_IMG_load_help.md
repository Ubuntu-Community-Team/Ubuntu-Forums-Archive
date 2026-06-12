---
title: "SDL_image IMG_load help"
date: 2011-04-14
forum: Programming Talk
---

### Post by natpat on 2011-04-14
**EDIT: Found the problem - I had a missing package, namely libpng3.**

Hey,

I've been dabbling in a bit of C++ and SDL. However, whenever I call IMG_load from the SDL_image library on a .png image, it always returns null - but with a .bmp it's fine.

I've been searching, and all I've found is the windows solution to make sure you have the .dll s in the same folder, but I know that's not it.

Anyone know what the reason could be?

Thanks

```
#include <iostream>

#include "CApp.h"
bool CApp::OnInit() {
    if(SDL_Init(SDL_INIT_EVERYTHING) < 0) {
        return false;
    }

    if((Surf_Display = SDL_SetVideoMode(WIDTH, HEIGHT, 32, SDL_HWSURFACE | SDL_DOUBLEBUF)) == NULL) {
        return false;
    }

    if((Surf_Grid = CSurface::OnLoad("./gfx/grid.png")) == NULL) {
        return false;
    }

    

    return true;
}

```

and in CSurface
```
#include "CSurface.h"
#include <iostream>
CSurface::CSurface() {
}

SDL_Surface* CSurface::OnLoad(char* File) {
    SDL_Surface* Surf_Temp = NULL;
    SDL_Surface* Surf_Return = NULL;
    if((Surf_Temp = IMG_Load(File)) == NULL) {
        std::cout << "Failed to load image";
        return NULL;
    }
    Surf_Return = SDL_DisplayFormatAlpha(Surf_Temp);

    SDL_UnlockSurface(Surf_Temp);
    SDL_FreeSurface(Surf_Temp);

    return Surf_Return;
}


bool CSurface::OnDraw(SDL_Surface* Surf_Dest, SDL_Surface* Surf_Src, int X, int Y) {
    if(Surf_Dest == NULL || Surf_Src == NULL) {
        return false;
    }

    SDL_Rect DestR;

    DestR.x = X;
    DestR.y = Y;

    SDL_BlitSurface(Surf_Src, NULL, Surf_Dest, &DestR);

    return true;
}

bool CSurface::OnDraw(SDL_Surface* Surf_Dest, SDL_Surface* Surf_Src, int X, int Y, int X2, int Y2, int W, int H) {
    if(Surf_Dest == NULL || Surf_Src == NULL) {
        return false;
    }
    SDL_Rect DestR;

    DestR.x = X;
    DestR.y = Y;

    SDL_Rect SrcR;

    SrcR.x = X2;
    SrcR.y = Y2;
    SrcR.w = W;
    SrcR.h = H;

    SDL_BlitSurface(Surf_Src, &SrcR, Surf_Dest, &DestR);

    return true;
}


```

---

