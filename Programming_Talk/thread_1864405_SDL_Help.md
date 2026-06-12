---
title: "SDL Help"
date: 2011-10-18
forum: Programming Talk
---

### Post by 7cardcha on 2011-10-18
I am having some SDL Segfault woes. I have wrote and compiled some SDL programs sucsessfully, Here is my code.

```


#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include "SDL/SDL_ttf.h"
#include <string>
using namespace std;

SDL_Event event;
TTF_Font* font = NULL;
SDL_Color textColor = {255,255,255};

SDL_Surface* background = NULL;
SDL_Surface* message = NULL;
SDL_Surface* screen = NULL;

const int width = 640;
const int height = 480;
const int colorbit = 32;

SDL_Surface *load_image(string filename)
{
    SDL_Surface* loadedImage = NULL;
    SDL_Surface* optimizedImage = NULL;
    loadedImage = IMG_Load(filename.c_str());

    if(loadedImage != NULL)
    {
        optimizedImage = SDL_DisplayFormat(loadedImage);
        SDL_FreeSurface(loadedImage);
    }
    Uint32 colorkey = SDL_MapRGB(optimizedImage->format,0,0,0);
    colorkey = SDL_MapRGB(optimizedImage->format,0,0xFF,0xFF);
    SDL_SetColorKey(optimizedImage,SDL_SRCCOLORKEY,colorkey);
    return optimizedImage;
}

void apply_surface(int coordx, int coordy,SDL_Surface* source,SDL_Surface* dest,SDL_Rect* clip = NULL)
{

    SDL_Rect offset;
    offset.x = coordx;
    offset.y = coordy;
    SDL_BlitSurface( source, clip, dest, &offset);
}
bool init(string caption = "",int width = 640,int height = 480)
{
    if(SDL_Init(SDL_INIT_EVERYTHING)== -1)
    {
        return false;
    }
    screen = SDL_SetVideoMode(width,height,colorbit,SDL_SWSURFACE);
    if(TTF_Init() == -1)
    {
        return false;
    }
    if(screen == NULL)
    {
        return false;
    }
    SDL_WM_SetCaption(caption.c_str(),NULL);
    return true;
}

int main( int argc, char* args[] )
{
    if(init("Hit x dumbshit")==false)
    {
        return 1;
    }

    background = load_image("background.png");
    font = TTF_OpenFont("lazy.ttf",28);
    message = TTF_RenderText_Solid(font,"I am a big buttshit",textColor);
    apply_surface(0,0,background,screen);
    apply_surface(0,150,message,screen);

    SDL_Flip(screen);
    bool run = true;

    while(run == true)
    {
        while(SDL_PollEvent(&event))
        {
            if(event.type == SDL_QUIT)
            {
                run = false;
            }
        }
    }
    SDL_FreeSurface(background);
    SDL_FreeSurface(message);
    TTF_CloseFont(font);
    SDL_Quit();
}


```


This compiles properly but Segfaults. I really REALLY Hate to ask for help with such messy code and so little background but I really tried to fix it. I don't throw every error I have onto a forum. Please help.

---

### Post by 7cardcha on 2011-10-18
Oh yeah and I fired up the core dump in gdb. It tells me that problem is load_image() I have used that function before many times without issue.

---

### Post by 7cardcha on 2011-10-18
NVM I fixed it

---

