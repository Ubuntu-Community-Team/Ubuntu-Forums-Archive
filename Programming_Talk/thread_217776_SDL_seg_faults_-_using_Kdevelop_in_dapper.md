---
title: "SDL seg faults - using Kdevelop in dapper"
date: 2006-07-17
forum: Programming Talk
---

### Post by G Morgan on 2006-07-17
I've been learning SDL from [this tutorial]("http://cone3d.gamedev.net/cgi-bin/index.pl?page=tutorials/gfxsdl/tut2") and I've been having some troubles with seg faults. Heres the code I've been using

```
#include <SDL/SDL.h>
#include <iostream>
#include <cstdlib>

using namespace std;

SDL_Surface *back;
SDL_Surface *image;
SDL_Surface *screen;

int xpos=0,ypos=0;

int InitImages();
void DrawIMG( SDL_Surface *img, int x, int y );
void DrawIMG( SDL_Surface *img, int x, int y, int w, int h, int x2, int y2 );
void DrawBG();
void DrawScene();

int main(){
	Uint8 *keys;
	
	if( SDL_Init( SDL_INIT_VIDEO|SDL_INIT_AUDIO ) < 0 )
	{
		cout << "Unable to init SDL: " << SDL_GetError() << endl;
		return 1;
	}
	atexit(SDL_Quit);
	
	SDL_Surface *screen;
	//screen = SDL_SetVideoMode( 640, 480, 32, SDL_HWSURFACE|SDL_DOUBLEBUF );
	screen = SDL_SetVideoMode( 640, 480, 32, SDL_HWSURFACE|SDL_DOUBLEBUF|SDL_FULLSCREEN );
	//screen = SDL_SetVideoMode( 640, 480, 32, SDL_SWSURFACE );
	
	if ( screen == NULL )
	{
		cout << "Unable to set 640x480 video: " << SDL_GetError() << endl;
		return 1;
	}
	
	InitImages();
	DrawBG();
	
	int done = 0;
	
	while (done == 0 ){
		SDL_Event event;
		while ( SDL_PollEvent(&event) )
		{
			if ( event.type == SDL_QUIT ) { done = 1; }
			if ( event.type == SDL_KEYDOWN )
			{
				if ( event.key.keysym.sym == SDLK_ESCAPE ) { done = 1; }
			}
		}
		keys = SDL_GetKeyState( NULL );
		if ( keys[SDLK_UP] ){ ypos -= 1; }
		if ( keys[SDLK_DOWN] ){ ypos += 1; }
		if ( keys[SDLK_LEFT] ){ xpos -= 1; }
		if ( keys[SDLK_RIGHT] ){ xpos += 1; }
		DrawScene();
	}
	
	return 0;
}

int InitImages(){
	back = SDL_LoadBMP( "bg.bmp" );
	image = SDL_LoadBMP( "image.bmp" );
	return 0;
}

void DrawIMG( SDL_Surface *img, int x, int y ){
	SDL_Rect dest;
	dest.x = x;
	dest.y = y;
	SDL_BlitSurface( img, NULL, screen, &dest );
}

void DrawIMG( SDL_Surface *img, int x, int y, int w, int h, int x2, int y2 ){
	SDL_Rect dest;
	dest.x = x;
	dest.y = y;
	SDL_Rect dest2;
	dest2.x = x2;
	dest2.y = y2;
	dest2.w = w;
	dest2.h = h;
	SDL_BlitSurface( img, &dest2, screen, &dest );
}

void DrawBG(){
	DrawIMG( back, 0, 0 );
}

void DrawScene(){
	DrawIMG( back, xpos-2, ypos-2, 132, 132, xpos-2, ypos-2 );
	DrawIMG( image, xpos, ypos );
	
	SDL_Flip( screen );
}

```

The strange thing about this is that the binary from the site works but even their source code doesn't work properly when compiled in Kdevelop. I keep getting the error
#Fatal signal: Segmentation Fault (SDL Parachute Deployed)


I've tried placing the image files into the project/ directory and project/src/ and project/debug/src/ but to no avail. I've also tried altering the permissions to 777 incase that was a problem but it didn't make a difference.

Any help would be appreciated.

---

### Post by GeoMX on 2006-07-18
You could try testing if your images were loaded correctly

```

SDL_image img = SDL_LoadBMP( "image.bmp" );
if ( !img ) {
  cerr << "Error loading image.bmp: " << SDL_GetError() << endl;
  exit( 1 );
}

```

Also, for testing purposes, you could include some info messages within your code (kind of simple debugging :P) :

```

int InitImages(){
	cout << "Loading images...." << endl;
	back = SDL_LoadBMP( "bg.bmp" );
	image = SDL_LoadBMP( "image.bmp" );
	cout << "Images loaded correctly." << endl;
	return 0;
}

```

This way you'll find easily where your code is crashing. I hate those segment faults errors, but they're very commmon when you try to use something you didn't load correctly, an image, a font, etc.

Also, if your InitImages is returning an int, you could use it as a success/failure return:

```

  if ( !image || !back )
    return ERROR_LOADING_IMAGES;
  else return SUCCESS_LOADING_IMAGES;

```

Regards,
JJ (GeoMX).

---

### Post by G Morgan on 2006-07-18
Ok I modified the InitImages() to the following

```
int InitImages(){
	cout << "loading images" << endl;
	back = SDL_LoadBMP( "bg.bmp" );
	if ( back == NULL ) {
		cout << "Error loading bg.bmp: " << SDL_GetError() << endl;
		exit( 1 );
	}
	image = SDL_LoadBMP( "image.bmp" );
	if ( image == NULL ) {
		cout << "Error loading image.bmp: " << SDL_GetError() << endl;
		exit( 1 );
	}
	cout << "images loaded" << endl;
	return 0;
}
```

The output in the terminal reads like this

```
loading images
images loaded
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
```

I'm assuming then that the images were loaded fine and something else is causing the problem.

---

### Post by wmcbrine on 2006-07-20
OK... you declared screen as both a global, and a local variable in main(). When you call SDL_SetVideoMode(), you assign the result to the local. Then, in other functions, you attempt to use the (uninitialized) value of the global.

Take the screen declaration out of main().

---

### Post by G Morgan on 2006-07-21
Cheers for that, teach me not to cut and paste from an older project without checking its all correct. The part that threw me was the example source has the same flaw so I assumed something else was wrong. Anyway its working now thanks again.

---

