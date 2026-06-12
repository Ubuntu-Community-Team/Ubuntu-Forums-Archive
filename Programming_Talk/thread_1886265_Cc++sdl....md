---
title: "C\c++\sdl...?"
date: 2011-11-24
forum: Programming Talk
---

### Post by Spirrwell on 2011-11-24
I'm REALLY unsure on how to classify my question here. I created an SDL program that gets pixels from an input image file and writes it to an "img.pxls" as I guess "raw" data... Since I'm a bit unsure on how else to describe it, here's the code:

```
#include <iostream>
#include <fstream>
#include "SDL.h"
#include "SDL_image.h"

using namespace std;
SDL_Surface *IMG;

Uint32 getpixel(SDL_Surface *surface, int x, int y)
{

    int bpp = surface->format->BytesPerPixel;
    /* Here p is the address to the pixel we want to retrieve */
    Uint8 *p = (Uint8 *)surface->pixels + y * surface->pitch + x * bpp;

    switch(bpp) {
    case 1:
        return *p;
        break;

    case 2:
        return *(Uint16 *)p;
        break;

    case 3:
        if(SDL_BYTEORDER == SDL_BIG_ENDIAN)
            return p[0] << 16 | p[1] << 8 | p[2];
        else
            return p[0] | p[1] << 8 | p[2] << 16;
        break;

    case 4:
        return *(Uint32 *)p;
        break;

    default:
        return 0;       /* shouldn't happen, but avoids warnings */
    }
}


void WriteSurface(SDL_Surface *Surface)
{
	ofstream img;
	img.open ("img.pxls");
	
    for(Sint32 y = 0; y < Surface->h; y++)
	{
        for(Sint32 x = 0; x < Surface->w; x++)
		{
			img << getpixel(Surface, x, y);
			img << "\n";
		}
	}
	img.close();
 
}

int main( int argc, char* args[] )
{
	system("COLOR 02");
	string FILENAMES;
    //Start SDL
    SDL_Init( SDL_INIT_EVERYTHING );
    printf("Please enter the location of the image you would like to extract pixels from:\n");
	
	scanf("%s", FILENAMES.c_str());
	IMG = IMG_Load(FILENAMES.c_str());
	if (IMG != NULL)
	{
		WriteSurface(IMG);
	}

	if (IMG == NULL)
		printf("\nImage does not exist!\n\n");

	if (IMG != NULL)
		printf("\nSuccessfully extracted pixels!\n\n");

	system("PAUSE");
	
    //Quit SDL
	SDL_FreeSurface(IMG);
    SDL_Quit();
    

    return 0;    
}
```

I used a simple 640 x 480 image for input and when it "extracts" the pixels, I get my img.pxls file. It contains a bunch of numbers. What I want to do is directly access the screen or video memory with a program and write these pixels to the screen for as long as the program is executed. If someone can point me in the right direction it'd be appreciated If you're wondering why in the hell would I want to do that, I'm bored. Ultimately I want to to see if this could help me in creation of an operating system by compiling a program into a .bin file that reads these pixels and prints them to screen. I'm learning Assembly and stuff, so it's just something that has caught my interest.

---

### Post by dagoth_pie on 2011-11-27
Unfortunately I can't give specific advice, I don't know the specifics of how SDL works. The approach I'd go for though, would be to get access to the backbuffer, then itorate through and write pixel by pixel from the image onto the surface. There's probably a function in SDL to do it, but I'm assuming you're wanting to reinvent the wheel here.

EDIT: I just went through and read the code you posted, I know, I probably should have done that first. Once you figure out how to get access to the backbuffer, you'll just have to write to the backbuffer surface rather then a file, and lock that into a while loop, checking once everytime through the loop to for an exit command from SDL, and reacting to the condition by exiting.

---

### Post by fct on 2011-11-30
Hello.

What you want is basically to write, pixel by pixel, to the screen.

For that you need, first, to write to an SDL_Surface with a putpixel() method, an example of which you can see here:

[http://www.libsdl.org/docs/html/guidevideo.html](http://www.libsdl.org/docs/html/guidevideo.html)

Then you want to blit that surface to the screen. In SDL, that means you blit to the screen surface, which you can get with SDL_GetVideoSurface(). Then use the SDL_BlitSurface() method.

The SDL Guides are where you should look for other examples:
[http://www.libsdl.org/docs/html/](http://www.libsdl.org/docs/html/)

---

### Post by Simian Man on 2011-11-30
> **Spirrwell said:**
> What I want to do is directly access the screen or video memory with a program and write these pixels to the screen for as long as the program is executed.

SDL won't let you do that because no modern operating system will let you do that.  If you want to run DOS or something equivalent, you can do this, but I really don't see the point.

---

### Post by MG&amp;TL on 2011-11-30
As always, if you're making an OS, look at linux from Scratch and MikeOS.

---

### Post by Petrolea on 2011-12-01
I remember from the times when I used to mess around with SDL that I had an array where I stored pixels and then wrote that array of pixels (which was height*width of screen wide) on the screen.

Not sure how I did this, but I'm pretty sure that's the way I did it and I remember it worked.

---

### Post by Simian Man on 2011-12-02
> **Petrolea said:**
> I remember from the times when I used to mess around with SDL that I had an array where I stored pixels and then wrote that array of pixels (which was height*width of screen wide) on the screen.

Yes, SDL lets you draw pixels to the screen, but through calls to SDL, which then turn into calls to the OS.  You can't write *directly* to video memory which is what the OP wanted.

---

### Post by Petrolea on 2011-12-02
> **Simian Man said:**
> Yes, SDL lets you draw pixels to the screen, but through calls to SDL, which then turn into calls to the OS.  You can't write *directly* to video memory which is what the OP wanted.

I tried to describe writing to screen. But of course you can't write to it directly.

With SDL you can go pretty low with writing to screen. You put pixels on some kind of virtual surface and then show it on the screen. With doing this you're not really accessing the screen itself (as hardware), but I don't think that's what OP wanted to do. 

But anyway, using that should be enough to fulfil the job of showing just a picture on the screen.

---

