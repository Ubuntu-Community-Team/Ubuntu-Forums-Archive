---
title: "Undefined reference to..."
date: 2009-04-20
forum: Programming Talk
---

### Post by swappo1 on 2009-04-20
I get the following errors when I run make and I don't know what the problem is.
```
scott@scott-laptop:~/SDL_Pong$ make
g++ -o Pongclone main.o global.cpp -lSDL_image -lpthread
main.o: In function `main':
main.cpp:(.text+0x62): undefined reference to `display_init()'
main.cpp:(.text+0x75): undefined reference to `display_load_files()'
main.cpp:(.text+0x8f): undefined reference to `display_update()'
main.cpp:(.text+0x98): undefined reference to `clean_up()'
collect2: ld returned 1 exit status
make: *** [Pongclone] Error 1

```
Here is main.cpp
```
#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include <iostream>
#include "global.h"
#include "display.h"

using namespace std;

SDL_Event event;

int main(int argc, char* args[])
{
	bool quit = false;
	
	//Initialize SDL
	if(display_init() == false)
	{
		cout << "SDL failed to initialize" << endl;
		return 1;
	}

	if(display_load_files() == false)
	{
		cout << "couldn't load the files" << endl;
		return 1;
	}
	
	while(quit == false)
	{
		while(SDL_PollEvent(&event))
		{
			if(event.type == SDL_QUIT || event.key.keysym.sym == SDLK_ESCAPE)
			{
				quit = true;
			}
		}
		display_update();
	}

	clean_up();	//display.cpp

	return 0;
}
```
display.cpp
```
//Pongclone

//Display file

#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include "display.h"

//Set the screen
SDL_Surface *screen = NULL;
//set the background
SDL_Surface *background = NULL;

//initialize screen
bool display_init()
{
	if(SDL_Init(SDL_INIT_VIDEO) == -1)
	{
		return false;
	}
	//set screen
	screen = SDL_SetVideoMode(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE);
	if(screen == NULL)
	{
		return false;
	}
	//add caption to window
	SDL_WM_SetCaption("Pongclone", "Pongclone");
	
	return true;
}
//load the imagage
SDL_Surface *load_image(char *file)		//( string filename )
{
	//The image that's loaded
	SDL_Surface* loadedImage = NULL;

	//The optimized surface that will be used
	SDL_Surface* optimizedImage = NULL;

	//Load the image
	loadedImage = IMG_Load(file)		//( filename.c_str() );

	//If the image loaded
	if( loadedImage != NULL )
	{
		//Create an optimized surface
		optimizedImage = SDL_DisplayFormat( loadedImage );

		//Free the old surface
		SDL_FreeSurface( loadedImage );

		//If the surface was optimized
		if( optimizedImage != NULL )
		{
			//map the colorkey to the transparent background of the sprite
			Uint32 colorkey = SDL_MapRGB(optimizedImage->format, 0xff, 0xff, 0xff); 
            
			//Set all colors of the background to be transparent
			SDL_SetColorKey(optimizedImage, SDL_SRCCOLORKEY, colorkey);
		}
	}

	//Return the optimized surface
	return optimizedImage;
}
//load files to be displayed
bool display_load_files()
{	//background image
	background = load_image("SDL_background.png");
	
	if(background == NULL)
		{
		return false;
		}
	return true;
}
//blit an image on the screen
void display_apply_surface(int x, int y, SDL_Surface* source, SDL_Surface* destination)
{
	SDL_Rect offset;
	
	offset.x = x;
	offset.y = y;
	
	SDL_BlitSurface(source, NULL, destination, &offset);
}
//Free surfaces and quit

//Update the display
void display_update()
{
	display_apply_surface(0, 0, background, screen);
	
	if(SDL_Flip(screen) == -1)
		{
			return 1;
		}
}

void clean_up()
{
	SDL_FreeSurface(background);
	
	SDL_Quit();
}
```
display.h
```
//Pongclone


//display header

#ifndef DISPLAY_H
#define DISPLAY_H

#include <SDL/SDL.h>

//init display
bool display_init();

//load the image
SDL_Surface *load_image(char *);		//( string filename );

//load the files to be displayed
bool display_load_files();

//blit an image on the screen
void display_apply_surface(int x, int y, SDL_Surface* source, SDL_Surface* destination);

//Update the display
void display_update();

//Free surfaces and quit
void clean_up();

#endif
```
Thanks for the patience while I muddle through my first Makefile.

---

### Post by Simian Man on 2009-04-20
You need to compile and link to the display.cpp code - right now you aren't doing this.  Something like this:
```

# makefile (untested)
Pongclone: main.o global.o display.o
    g++ -o Pongclone main.o global.o display.o -lSDL_image -lpthread

main.o: main.cpp
    g++ -c main.cpp

global.o: global.cpp
    g++ -c global.cpp

display.o: display.cpp display.h
    g++ -c display.cpp

```

---

### Post by swappo1 on 2009-04-20
It appears I didn't put display.cpp in Makefile.  That clears the problem up.

---

