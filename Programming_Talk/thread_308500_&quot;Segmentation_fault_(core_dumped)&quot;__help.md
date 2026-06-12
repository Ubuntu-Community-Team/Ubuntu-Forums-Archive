---
title: "&quot;Segmentation fault (core dumped)&quot;  help with c++ thing"
date: 2006-11-28
forum: Programming Talk
---

### Post by Choad on 2006-11-28
```

#include <stdio.h>

#include <stdlib.h>

#include "SDL/SDL.h"
#include "SDL/SDL_image.h"	
#include <string>

  ////////////////
  // Prototypes //
  ////////////////
  
void DrawScene(void);
bool Init(void);
SDL_Surface * LoadImage( std::string filename );


  /////////////
  // Globals //
  /////////////

SDL_Surface * screen;

SDL_Surface * sprBackground;
SDL_Surface * sprPlayer;
SDL_Surface * sprBlock;

SDL_Rect rectBackground;
SDL_Rect rectPlayer;
SDL_Rect rectPlayerSource;
SDL_Rect rectBlock;

const int SCREEN_WIDTH = 640;
const int SCREEN_HEIGHT = 480;
const int SCREEN_BPP = 32;

bool levelLayout[19][14];


  ///////////////
  // Functions //
  ///////////////
  
void DrawScene(void)
{
	SDL_BlitSurface(sprBackground, 
			NULL, 
			screen, 
			&rectBackground);
	
	SDL_BlitSurface(sprPlayer, 
			&rectPlayerSource, 
			screen, 
			&rectPlayer); 
	
	SDL_Flip(screen);
}

bool Init(void)
{
	  // set up the level
	for (int i = 0; i < 20; i++)
	{
		for (int o = 0; o < 15; o++)
		{
			if ((i == 0) || (i == 19) || (o == 0) || (o == 14))
			{
				levelLayout[i][o] = true;
			}
			else
			{
				levelLayout[i][o] = false;
			}
		}
	}
	
	  // load sprites
	sprBackground = LoadImage("background.png");
	sprPlayer = LoadImage("player.png");
	sprBlock = LoadImage("block.png");
	
	rectBackground.x = 0;
	rectBackground.y = 0;
	rectPlayer.x = 64;
	rectPlayer.y = 64;
	rectPlayerSource.x = 0;
	rectPlayerSource.y = 0;
	rectPlayerSource.w = 32;
	rectPlayerSource.h = 32;
	
	  //Initialize SDL video subsystems
    	if( SDL_Init( SDL_INIT_VIDEO ) == -1 )    
    	{
		return false;    
	}
	
	  // create screen
	screen = SDL_SetVideoMode( 	SCREEN_WIDTH, 
					SCREEN_HEIGHT, 
					SCREEN_BPP, 
					SDL_SWSURFACE ); 
	  //Register SDL_Quit() with atexit

	atexit(SDL_Quit);
}

SDL_Surface *LoadImage( std::string filename )
{
	SDL_Surface* loaded_image = NULL;
	SDL_Surface* compatible_image = NULL;
	
	if(filename.c_str() == NULL) 
	{ 
		return NULL;
	}

	  // load the image
	loaded_image = IMG_Load(filename.c_str());
	
	if( loaded_image == NULL )
	{
		  // if not exit the function
		return NULL;
	}	

	  // convert image to screen format
	compatible_image = SDL_DisplayFormat( loaded_image );

	if( compatible_image != NULL ) 
	{
		  // set transparrent colour
		Uint32 colorkey = SDL_MapRGB( 	compatible_image->format, 
						255, 
						0, 
						255); // choose pink

		SDL_SetColorKey(compatible_image, 
				SDL_RLEACCEL | SDL_SRCCOLORKEY, 
				colorkey);
	}

	  // Destroy the old copy
	SDL_FreeSurface( loaded_image );

	  // return a pointer to the newly created display compatible image
	return compatible_image;
}

  //////////
  // Main //
  //////////
  

int main(int argc, char *argv[])

{

	Init();
	

	int done = 0;

	Uint8 *keys;

	SDL_Event event; //Used to point to SDL_Event

	SDL_Rect dest;



	/** Create a while loop that exits when the variable done = 1.

		This example keeps running until Esc key is pressed. */

	while (done == 0) 
		{

		  //Using polling to read input

		while (SDL_PollEvent(&event)) 
		{

			if (event.type == SDL_KEYDOWN) 
			{

				if (event.key.keysym.sym == SDLK_ESCAPE)
				{

					done = 1;
				}

			}//end if

		}//end while
		DrawScene();

	}//end while



	return 0;

}


```


well, its a fair chunk of code... it compiles just fine but i cant run it. i am a bit annoyed because i kept on compiling it to see if it was working and it was, but i wasnt actually running the binary, so i cant figure out what bit of code caused the error

i am compiling it with this command

$ g++ `sdl-config --cflags --libs` -o mything mything.cpp -lSDL -lSDL_image

you need a player.png, background.png and block.png 

any help appreciated :)

---

### Post by Houman on 2006-11-28
hi there;

you must not call SDL_DisplayFormat before doing SDL_SetVideoMode , how would  SDL know what format to convert your image to if you havnt set a video mode?

Also its simple to debug binaries, just compile them with the -g command, then you can run them with gdb and then you can find out where the crash happens (just google for gdb tutorial).

regards

Houman

---

### Post by Choad on 2006-11-28
> **Houman said:**
> hi there;

you must not call SDL_DisplayFormat before doing SDL_SetVideoMode , how would  SDL know what format to convert your image to if you havnt set a video mode?

Also its simple to debug binaries, just compile them with the -g command, then you can run them with gdb and then you can find out where the crash happens (just google for gdb tutorial).

regards

Houman
wohooo!

u r a legend!

---

### Post by Somtin on 2008-11-29
Hi, sorry for the bump.

When I try to compile my code, I get a seg fault, and when running it with gdb, it says that it is at the line where I use SDL_DisplayFormat(temp).

However, I have used SDL_SetVideoMode before I did this... Any clues?

```

// in function Init()
// create the screen surface

screen = SDL_SetVideoMode(width, height, bpp, flags);

.. some stuff here ..

LoadResources();


-- snip --

// in function LoadResources()
SDL_Surface* temp = SDL_LoadBMP("intro.bmp");
if (temp != NULL) {
	media->introbg = SDL_DisplayFormat(temp);
}

SDL_FreeSurface(temp);

```

media is a struct, containing a list of SDL_Surface*

---

### Post by dwhitney67 on 2008-11-29
You are accessing the member 'introbg' of media using a pointer (->).  Have you allocated memory for the media object?

Another easy way to debug code is to either using print statements (cout or printf) or to use assert().

[php]
#include <cassert>

...

SDL_Surface* temp = SDL_LoadBMP("intro.bmp");
if (temp != NULL) {
  assert(media != 0);
  media->introbg = SDL_DisplayFormat(temp);
}
[/php]

---

### Post by Somtin on 2008-12-01
media is a struct* and introbg is SDL_Surface*

I havn't allocated any memory.. how would I do that, where and how much? Better to not use a pointer there?

---

### Post by dwhitney67 on 2008-12-01
Please show the definition of the struct(ure) for 'media'; also show me where 'media' is declared.

---

### Post by nvteighen on 2008-12-01
IIRC, in C++ you'd use 'new' for that. Or you could #include <cstdlib> and use C's malloc()... (I know C, not C++ so I may be wrong).

---

### Post by Somtin on 2008-12-02
the media struct is in an include file, included from the file that the error is in. eg. the error is in file.cpp and at the beginning of the file it has an include file.h, where the struct actually is.

The struct is as follows:
struct s_resources {
        // intro
        SDL_Surface* introbg;
        SDL_Surface* introfader;
};

And the declaration of the struct is inside the same class as what the error is in.

s_resources* media;

---

### Post by dwhitney67 on 2008-12-02
> **Somtin said:**
> the media struct is in an include file, included from the file that the error is in. eg. the error is in file.cpp and at the beginning of the file it has an include file.h, where the struct actually is.

The struct is as follows:
struct s_resources {
        // intro
        SDL_Surface* introbg;
        SDL_Surface* introfader;
};

And the declaration of the struct is inside the same class as what the error is in.

s_resources* media;

You need to allocate memory for media, although if you define it without the pointer symbol (*), then it would not be necessary, because then it would be created on the stack.

If you intend to keep media defined as a pointer, the way you allocate memory for it is as follows (in the class constructor):
[php]
ClassName::ClassName(...)
  : media(new s_resources)
{
}
[/php]
or alternatively as:
[php]
ClassName::ClassName(...)
{
  media = new s_resources;
}
[/php]

Don't forget to deallocate the pointer when your class is destroyed.  You will need to call delete.

If you fail to understand these concepts, I suggest you review your C++ book wrt to memory allocation and deletion.

---

### Post by Somtin on 2008-12-04
Ok, I think I'll remove the pointer as I don't think its necessary as I am not doing any writing to it outside of the class.

---

