---
title: "Annoying SDL Problem"
date: 2009-07-28
forum: Programming Talk
---

### Post by dellwood on 2009-07-28
Hi, 

One of my SDL functions in "Engine.cpp" is spitting out an error that I can't seem to pinpoint.  Here's the code.

Engine.h

```
#ifndef ENGINE_H
#define ENGINE_H

#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include "SDL/SDL_ttf.h"
#include <iostream>
#include <string>
#include <vector>
#include <map>

using namespace std;

class Init {
        private:
                int win_width, win_height, win_bpp; //used for setting up the window
                string win_caption; //the text that goes in the window caption
                int win_time; //the time the window stays open ( for dev purposes only )
                string file, handle; //the filename and image handle strings
                SDL_Surface *nativeImage; // used for loading image
                SDL_Surface *optimizedImage; // used for optimizing the image
                string filename; // filename for loadImage
                int xCoord, yCoord; // placeSurface offsets
                SDL_Surface *source;
                SDL_Surface *destination; //for surface blitting

        public:
                SDL_Surface *screen; // needs to be used outside of function
                Init();
                ~Init();
                void Load( int win_width, int win_height, int win_bpp, string win_caption, int win_time );
                SDL_Surface *loadImage( string filename );
                void placeSurface( int xCoord, int yCoord, SDL_Surface *source, SDL_Surface* destination );
                void Quit();
};



#endif // ENGINE_H 

```

Engine.cpp

#include "Engine.h"

```
/* Constructor */
Init::Init() {
	int win_width = 640;
	int win_height = 480;
	int win_bpp = 32;
	string win_caption = "Default Caption";
	int win_time = 3;
	SDL_Surface *screen = NULL;
	string filename = " ";
	string handle = " ";
	SDL_Surface *nativeImage = NULL;
	SDL_Surface *optimizedImage = NULL;
	int xCoord = 0;
	int yCoord = 0;
	SDL_Surface *source = NULL;
	SDL_Surface *destination = NULL;
}

/* Destructor */
Init::~Init() {
 }

/* Class Functions */

void Init::Load( int win_width, int win_height, int win_bpp, string win_caption, int win_time ) {

	/* Initialize Subsystems */
	if( SDL_Init( SDL_INIT_EVERYTHING < 0 ) ) {
		cerr << "Failed to Initialize subsystems: ", SDL_GetError();
	}

	/* Set up screen */
	screen = SDL_SetVideoMode( win_width, win_height, win_bpp, SDL_SWSURFACE );

	/* Make sure screen initialized */
	if( screen == NULL ) {
		cerr << "Failed to load screen: ", SDL_GetError();
	}

	/* Set Caption */
	SDL_WM_SetCaption( win_caption.c_str(), NULL );
	

	/* Convert win_time from seconds to milliseconds */
	win_time *= 1000;
	
	/* Wait win_time seconds */
	SDL_Delay( win_time );	

}

SDL_Surface *loadImage( string filename ) {
	
		/* Load the image */

		SDL_Surface *nativeImage = IMG_Load( filename.c_str() );

		if( nativeImage != NULL ) {
			/* Optimize the image */
			SDL_Surface *optimizedImage = SDL_DisplayFormat( nativeImage );
		}	
		else {
			cerr << "Error loading image: " << SDL_GetError() << endl;
		}

		return optimizedImage;
}

void placeSuface( int xCoord, int yCoord, SDL_Surface *source, SDL_Surface *destination ) {
	
	/* Create a rectangle */
	SDL_Rect surface;
	
	/* Set the */
	surface.x = xCoord;
	surface.y = yCoord;
	
	/* Blit the surface to the screen */
	SDL_BlitSurface( source, NULL, destination, &surface);
}
		
void Init::Quit() {
	/* Quit the program (more to be added here later */
	SDL_Quit();
}
```

```
#include <iostream>
#include "Engine.h"

int main( int argc, char** args ) {

        SDL_Surface * image;

        /* Create class objects */
        Init main_init;

        /* Load the object functions */
        main_init.Load( 640, 480, 32, "A Test Program", 3 );

        image = main_init.loadImage( "image.png" );

        main_init.placeSurface( 0, 0, image, main_init.screen );

        main_init.Quit();

        return 0;
}
```

And last but not least, the error:

```
g++ -o Main main.cpp Engine.cpp -lSDL -lSDL_image                                                                                        ~/Programs/C++/syi-engine
Engine.cpp: In function &#8216;SDL_Surface* loadImage(std::string)&#8217;:
Engine.cpp:68: error: &#8216;optimizedImage&#8217; was not declared in this scope
```

It seems to think I haven't declared "optimized image," even though I did in the header as well as in the constructor...right ? :D  I have been mulling this over for 30 + minutes without success:-k.

Thanks :).

-Josh

---

### Post by wmcbrine on 2009-07-28
Hint: Note the word "scope".

---

### Post by JordyD on 2009-07-28
> **wmcbrine said:**
> Hint: Note the word "scope".

And not of [this]("http://en.wikipedia.org/wiki/Telescopic_sight") variety, but rather [this]("http://en.wikipedia.org/wiki/Scope_(programming)") one.

---

### Post by dellwood on 2009-07-28
After looking here ( [http://cplusplus.syntaxerrors.info/index.php?title=%E2%80%98bar%E2%80%99_was_not_declared_in_this_scope](http://cplusplus.syntaxerrors.info/index.php?title=%E2%80%98bar%E2%80%99_was_not_declared_in_this_scope) ) as well as your wiki link I did add Init:: between SDL_Surface and *loadImage, but that still gave the same error ( after forcing me to fix a few others ).  Was that the 'scope' problem you were talking about, or is it something else?

Thanks.

-Josh

---

### Post by JordyD on 2009-07-28
> **dellwood said:**
> After looking here ( [http://cplusplus.syntaxerrors.info/index.php?title=%E2%80%98bar%E2%80%99_was_not_declared_in_this_scope](http://cplusplus.syntaxerrors.info/index.php?title=%E2%80%98bar%E2%80%99_was_not_declared_in_this_scope) ) as well as your wiki link I did add Init:: between SDL_Surface and *loadImage, but that still gave the same error ( after forcing me to fix a few others ).  Was that the 'scope' problem you were talking about, or is it something else?

Thanks.

-Josh

That's not the scope I was talking about.

If you declare a variable inside of a certain scope, when it exits that scope, your variable is gone.

(Some) things that increase scope:
functions,
loops,
if statements,
classes

Now take a look at the variable that the compiler says is non-existent:
```
SDL_Surface *loadImage( string filename ) {
	
		/* Load the image */

		SDL_Surface *nativeImage = IMG_Load( filename.c_str() );

		if( nativeImage != NULL ) {
			/* Optimize the image */
			SDL_Surface *optimizedImage = SDL_DisplayFormat( nativeImage );
		}	
		else {
			cerr << "Error loading image: " << SDL_GetError() << endl;
		}

		return optimizedImage;
}
```

So, the loadImage function is in its scope. Think of a filesystem, like this: /loadImage
We load an image into nativeImage. Scope is still /loadImage
We go into an if statement, scope is now /loadImage/if
We declare optimizedImage and define it.
We exit the if statement, and now scope is /loadImage again.
We try to return optimizedImage, but it does not exist, since it was declared out of scope (/loadImage/if specifically). If we declared it in /loadImage, then we could still use it, and it would be initialized to SDL_DisplayFormat(nativeImage).

---

### Post by monraaf on 2009-07-28
This makes me sad :( It seems that people don't even take the time anymore to learn the language basics.

---

### Post by dellwood on 2009-07-29
I am still learning the basics.  I told myself that when I got to point x in my programming book , I would look back and try to devise an exercise that incorporates everything I had learned up to that point, which included functions, classes, and simple API's ( I know SDL may not have been the best choice, but I used a very small portion of it ).  Since I spent a most of today writing/debugging/re-writing this code, and I had it down to one error, I said what the heck, I'll stick it up on the forums and see if I can actually get this to work. 

So hopefully your not sad anymore :).

-Josh

---

### Post by monraaf on 2009-07-29
Ah okay, so this is part of your learning process. Personally I think it's better to stick to plain old 'boring' console programs learning the basics of the language first before diving into external libraries.

---

### Post by wmcbrine on 2009-07-29
> **dellwood said:**
> I know SDL may not have been the best choiceYour problem has nothing to do with SDL.

---

### Post by dwhitney67 on 2009-07-29
There are also problems with the implementation of the methods loadImage() and placeSuface() [sic] in the Engine.cpp file.  Once again, the problems are related to "scope".

---

