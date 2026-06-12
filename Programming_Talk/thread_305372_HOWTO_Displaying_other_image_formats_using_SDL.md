---
title: "HOWTO: Displaying other image formats using SDL"
date: 2006-11-23
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-11-23
This is the thrird in a series of HOWTOs covering games development using Simple DirectMedia Layer (SDL)

This HOWTO covers the following topics:

1) Installing extra support for loading other image formats
2) How to load different file formats.

1) Installing extra support for loading other image formats

Firstly, we need to make sure that you have the SDL_Image1.2 library installed, as we cant compile the different functionality into your programs without it.

Open up you favourite package manager and search for 'sdl'. This should give you a list of libraries that are currently installed. The ones where interested in are 'libsdl-image1.2' and 'libsdl-image1.2-dev'. 

If you have these already installed then your good to go, or else select them and install them now.

2) How to load different file formats.

Loading other image formats is as simple as changing a couple of lines of code so here goes.

```

#include "SDL_image.h"

```

Then we change the function name used to load the image from 'SDL_LoadBMP' to 'IMG_Load'. 

Before we do that though its worth moving some of the code from the last HOWTO around so that we have a proper function to call to take care of loading the image onto a surface and converting it to the same Display format as we are working with.

So here is our new function to do that including some error checking tests:
```

SDL_Surface *Load_image( std::string filename )
{
	SDL_Surface* loaded_image = NULL;
	SDL_Surface* compatible_image = NULL;

	if(filename == NULL) { // check to see if a filename was provided
		// if not exit the function
		return NULL;
	}

	// load the image using our new IMG_Load function from sdl-Image1.2
	loaded_image = IMG_Load( filename.c_str() );

	if( loaded_image == NULL ){ // check to see if it loaded properly
		// if not exit the function
		return NULL;
	}	

	// the image loaded fine so we can now convert it to the current display depth
	compatible_image = SDL_DisplayFormat( loaded_image );

	// Destroy the old copy
	SDL_FreeSurface( loaded_image );

	// return a pointer to the newly created display compatible image
	return compatible_image;
}

```

NOTE: You will notice in previous HOWTOs that there was no attempt to do error checking. Now that we are making the code segments more complex it will benefit us to start this valuable practice. Later on when things seem to go wrong for no reason, you will be glad that you took the time to create a way to know why your code isn't behaving the way you planned. :-D


Now that we have created our new funtion to go the job of loading images we can know shorten our main() function as you can see in the full program listing below:
```

// anypic.cpp
// some find that thier programs wont compile unless you add 'SDL/SDL.h' instead of just 'SDL.h'
// If you are like me then do the 'SDL/SDL.h' thing instead

#include "SDL/SDL.h"
#include "SDL/SDL_image.h"	
#include <string>	

SDL_Surface *Load_image( std::string filename )
{
	SDL_Surface* loaded_image = NULL;
	SDL_Surface* compatible_image = NULL;

	if(filename.c_str() == NULL) { // check to see if a filename was provided
		// if not exit the function
		return NULL;
	}

	// load the image using our new IMG_Load function from sdl-Image1.2
	loaded_image = IMG_Load( filename.c_str() );

	if( loaded_image == NULL ){ // check to see if it loaded properly
		// if not exit the function
		return NULL;
	}	

	// the image loaded fine so we can now convert it to the current display depth
	compatible_image = SDL_DisplayFormat( loaded_image );

	// Destroy the old copy
	SDL_FreeSurface( loaded_image );

	// return a pointer to the newly created display compatible image
	return compatible_image;
}

int main( int argc, char* argv[] )
{
	SDL_Surface* image = NULL;	
	SDL_Surface* screen = NULL;

	SDL_Rect position;

	const int SCREEN_WIDTH = 800;		// set screen dimensions
	const int SCREEN_HEIGHT = 600;
	const int SCREEN_BPP = 32;

	position.x = 0; 			// initialize position rectangle
	position.y = 0;
	
	// make sure SDL shuts down in the event of a crash
	atexit( SDL_Quit );

	// create screen 800x600x32bpp in software rendering mode.
	screen = SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE ); 
	
	// load the picture (a windows bmp) which you can create yourself using GIMP
	image = Load_image( argv[1] ); // argv[1] is the command line argument for the filename
	
	if( image == NULL ){
		printf("unable to load %s\n", argv[1]);
	}
	
	// put the image on the screen surface
	SDL_BlitSurface( image, NULL, screen, &position ); 

	SDL_Flip( screen ); // send the screen surface to be displayed

	//Wait 2 seconds
	SDL_Delay( 2000 );	

	// Destroy image surface
	SDL_FreeSurface( image );
	return 0;
}

```

to compile and run:
```

g++ -o anypic anypic.cpp -lSDL -lSDL_image
./anypic <the name and path of any picture file you like>

```

So there you have it! how to make a re-usable function to load any of the popular graphics formats you like!

Please feel free to contribute with comments and/or howtos of your own!

Mike

---

### Post by Gustav on 2006-11-23
Great howtos!

You misspelled the first SDL_Surface (it sais SDL_Sureface) :)

---

### Post by Mickeysofine1972 on 2006-11-23
Thanks and ,,,, er thanks!

I didn't notice!

Funny it works when I compile it though :-D 

Corrected mistakes!

Mike

PS - I'd like to welcome seethru  to the SDL Programming for Ubuntu HOWTO Writers Team! and I'd like to say we are looking forward to seeing what mysteries of SDL and games development you can help us explode! 

PPS - If you would like to contribute in our project please contact us - we would love to have your contribution

---

### Post by Houman on 2006-11-23
Hi there;

I think there is an extra 
```

printf("unable to load %s", argv[1]);

```
around the beginning of the main function;

thanks for the HowTo by the way, I think theyre great, I read all of them :)

regards

Houman

---

### Post by Mickeysofine1972 on 2006-11-23
Thanks for the help! I get so excited toward the end of a new HOWTO that I sometime miss these things!

I'm glad were helping out, this originally sprang from a thread about whether Linux gaming is improving. We agreed that if there was a good resource of info on games development that this might improve things for those who have limited experience or resources for games development.

Our aim is really to start with SDL as the means to deliver sound and graphics, but ultimately these howtos will start and cover other more general games programming subject like path finding and basic AI.

So keep on reading and we will make ubuntuforums.org a center for learning all things linux!

Mike

---

