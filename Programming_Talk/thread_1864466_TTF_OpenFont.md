---
title: "TTF_OpenFont"
date: 2011-10-19
forum: Programming Talk
---

### Post by 7cardcha on 2011-10-19
I have a problem with SDL. Here is the code
```


#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include "SDL/SDL_ttf.h"
#include <string>
using namespace std;

SDL_Surface* screen = NULL;
SDL_Surface* img = NULL;
TTF_Font* font = NULL;
SDL_Surface* messageup = NULL;
SDL_Surface* messagedown = NULL;
SDL_Surface* messageleft = NULL;
SDL_Surface* messageright = NULL;
SDL_Surface* message = NULL;
SDL_Color textColor = {0,0,0};

SDL_Event event;

SDL_Surface* load_image(string filename)
{
    SDL_Surface* loadedImage = IMG_Load(filename.c_str());
    SDL_Surface* optimizedImage = SDL_DisplayFormat(loadedImage);
    SDL_FreeSurface(loadedImage);
    return optimizedImage;
}

void apply_surface(int x ,int y,SDL_Surface* source,SDL_Surface* dest)
{
    SDL_Rect offset;
    offset.x = x;
    offset.y = y;
    SDL_BlitSurface(source,NULL,dest,&offset);
}

void init(string caption = "",int height = 640,int width = 480,int colorbits = 32)
{
    SDL_Init(SDL_INIT_EVERYTHING);
    screen = SDL_SetVideoMode(height,width,colorbits,SDL_SWSURFACE);
    TTF_Init();
    SDL_WM_SetCaption(caption.c_str(),NULL);
}

int main( int argc, char* args[] )
{
    init("butthole");
    img = load_image("background.png");
    font = TTF_OpenFont("lazy.tff",28);
    if(!font) {
    printf("TTF_OpenFont: %s\n", TTF_GetError());
        return 1;
    }

    messageup = TTF_RenderText_Solid(font,"Up pressed",textColor);
    messagedown = TTF_RenderText_Solid(font,"Down pressed",textColor);
    messageleft = TTF_RenderText_Solid(font,"Left pressed",textColor);
    messageright = TTF_RenderText_Solid(font,"Right pressed",textColor);


    apply_surface(0,0,img,screen);
    SDL_Flip(screen);
    bool quit = true;
    while(quit)
    {
        while(SDL_PollEvent(&event))
        {
            if(event.type == SDL_QUIT)
            {
                quit = false;
            }
            switch(event.key.keysym.sym)
            {
                case SDLK_UP: message = messageup; break;
                case SDLK_DOWN: message = messagedown; break;
                case SDLK_LEFT: message = messageleft; break;
                case SDLK_RIGHT: message = messageright; break;
            }
            apply_surface(320,240,message,screen);
            SDL_Flip(screen);
            SDL_Delay(20);
        }
    }
    SDL_FreeSurface(img);
    SDL_FreeSurface(message);
    SDL_FreeSurface(messagedown);
    SDL_FreeSurface(messageup);
    SDL_FreeSurface(messageleft);
    SDL_FreeSurface(messageright);
    SDL_Quit();
}

```

It compiles fine(using the command: g++  -o a.out main.cpp -lSDL -lSDL_image -lSDL_ttf) 
but gives the error: TTF_OpenFont: Couldn't open lazy.tff

Any idea what is wrong?

lazy.tff is in the same directory

---

### Post by gsmanners on 2011-10-19
> TTF_OpenFont: Couldn't open lazy._tff_

Any idea what is wrong?

lazy.tff is in the same directory

I think I see your problem. You sure that's how that extension is spelled?

---

### Post by 7cardcha on 2011-10-19
> **gsmanners said:**
> I think I see your problem. You sure that's how that extension is spelled?

Oh. My. God. WHY MUST I BE SUCH AN IDIOT. Thanks a lot man.

---

### Post by Alan D on 2011-10-20
> **7cardcha said:**
> Oh. My. God. WHY MUST I BE SUCH AN IDIOT. Thanks a lot man.

No way. You are not an idiot. That is the exact sort of mistake anyone makes.

---

