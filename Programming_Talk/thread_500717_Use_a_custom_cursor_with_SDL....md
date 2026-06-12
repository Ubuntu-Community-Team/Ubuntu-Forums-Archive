---
title: "Use a custom cursor with SDL..."
date: 2007-07-14
forum: Programming Talk
---

### Post by Sockerdrickan on 2007-07-14
Hi how can I use a custom cursor in SDL, moveable with MouseX and MouseY? :popcorn:

---

### Post by Wybiral on 2007-07-14
[http://docs.mandragor.org/files/Common_libs_documentation/SDL/SDL_Documentation_project_en/sdlcreatecursor.html](http://docs.mandragor.org/files/Common_libs_documentation/SDL/SDL_Documentation_project_en/sdlcreatecursor.html)

If you're looking for more then that, then you can use MouseX,MouseY and make your own by rendering a surface at that x,y.

---

### Post by Sockerdrickan on 2007-07-14
Congrats to your 1000 post

I get errors could you please send code where I can load the cursor from a PNG or BMP
And the MouseX MouseY draw code? :) Im noob at the moment

---

### Post by Wybiral on 2007-07-14
lol, thanks.

OK, here's a program that loads a BMP and manually renders it as the cursor...

```

#include <SDL/SDL.h>

int mousex, mousey;

SDL_Surface* init_sdl(int width, int height)
{
    SDL_Init(SDL_INIT_VIDEO);
    return SDL_SetVideoMode(width, height, 0, SDL_HWSURFACE | SDL_DOUBLEBUF);
}

void exit_sdl(SDL_Surface* surface)
{
    SDL_FreeSurface(surface);
    SDL_Quit();
}

// Chopped down even function
int events()
{
    SDL_Event event;
    while(SDL_PollEvent(&event))
    {
        switch(event.type)
        {
            case SDL_MOUSEMOTION:
                mousex = event.motion.x;

                mousey = event.motion.y;
            break;


            case SDL_QUIT: return 0;
        }
    }
    return 1;
}

int main()
{
    SDL_Surface *surf = init_sdl(640, 480);
    SDL_Surface *curs = SDL_LoadBMP("temp.bmp");
    // Hide real cursor
    SDL_ShowCursor(0);
    // Set cursor width,height to that of loaded bmp
    SDL_Rect dst;
    dst.w = curs->w;
    dst.h = curs->h;
    while(events())
    {
        // Clear surface
        SDL_FillRect(surf, NULL, SDL_MapRGB(surf->format, 0, 0, 0));
        // Set destination x,y
        dst.x = mousex;
        dst.y = mousey;
        // Blit onto main surface
        SDL_BlitSurface(curs, NULL, surf, &dst);
        // Swap main surface buffers
        SDL_Flip(surf);
    }

    exit_sdl(surf);
}

```

Just change the "test.bmp" to your actual BMP image. That method works, and allows for multicolored images pretty well, but it is a little more work then the standard way that SDL wants you to use (from the link I posted). Most of that is chopped down for the bare minimum needed for that demo to work, but it should give you an idea of how you can use SDL's BMP loader to blit a BMP to the screen.

Remember to blit it AFTER you render your other graphics so that it stays on top.

Also, if you use SDL_Image in combination with that, you can use all kinds of image formats for the cursor (thus allowing for cursors with transparency).

Hope that helps.

---

### Post by Sockerdrickan on 2007-07-15
Wow thaaaanks :D

Gonna make it work with SDL_image now :) Will write here how it goes later!

---

### Post by Sockerdrickan on 2007-07-15
Works ;) ;)

---

### Post by vedelumino on 2012-06-02
Hi, that works! :D Thankyou!
but, how if it has background? when i try, the surface repeating "apply surface". it looks like using brush on GIMP.
any help to solve this problem? thankyou very much :)

---

