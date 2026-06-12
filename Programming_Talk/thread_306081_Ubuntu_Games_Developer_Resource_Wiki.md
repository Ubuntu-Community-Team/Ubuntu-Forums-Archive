---
title: "Ubuntu Games Developer Resource Wiki"
date: 2006-11-24
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-11-24
Hi

You may have noticed a large amount of HOWTO relating to SDL and games programming on this part of the forum, well, guess what! we've made a Wiki to store all these lovely articles.

We will continue to post on the forum about any questions and we will announce every new HOWTO as they are released.

If you have any ideas for HOWTOs or you have a HOWTO of your own that you would like to contribute, let us know and we will be happy to include anything you give.

The URL for our new Wiki is: [http://ubuntu-gamedev.pbwiki.com/](http://ubuntu-gamedev.pbwiki.com/)

Mike

---

### Post by Choad on 2006-11-24
following your first tutorial, libsdl OSS wants to get rid of libsdl ALSA

is there a reason why i want OSS over ALSA

will removing ALSA break things?

---

### Post by Choad on 2006-11-24
ok the second tutorial, in the wiki it says SDL_Flip(); but it needs to be SDL_Flip(screen);

also, i made this

```
#include "SDL/SDL.h"

int main(int argc, char* argv[])
{
	// start sdl
	SDL_Init(SDL_INIT_EVERYTHING);
	
	// load an image
	
	SDL_Surface* loaded_image = NULL;
	loaded_image = SDL_LoadBMP("MyImage.bmp");
	
	// convert it to the right format
	
	SDL_Surface* compatible_image = NULL;
	compatible_image = SDL_DisplayFormat(loaded_image);
	SDL_FreeSurface(loaded_image);
	
	// set up the screen
	
	const int SCREEN_WIDTH = 800;
	const int SCREEN_HEIGHT = 600;
	const int SCREEN_BPP = 32;
	
	SDL_Surface* screen = NULL;
	
	screen = SDL_SetVideoMode(	SCREEN_WIDTH, 
					SCREEN_HEIGHT, 
					SCREEN_BPP, 
					SDL_SWSURFACE);
	
	// put image on screen
	
	SDL_Rect position;
	position.x = 0;
	position.y = 0;
	
	SDL_BlitSurface(	compatible_image,
				NULL,
				screen,
				&position);
	
	SDL_Flip(screen);
	
	//Wait 2 seconds
	SDL_Delay( 2000 );
	

	// Destroy remaining surfaces
	SDL_FreeSurface( compatible_image );
	
	
	// quit sdl
	SDL_Quit();
	
	return 0;
}

```

and it compiles but it just displays a black window. my image is NOT displayed. why is this? the image is in the same directory as the binary

---

### Post by Mickeysofine1972 on 2006-11-24
> **Choad said:**
> following your first tutorial, libsdl OSS wants to get rid of libsdl ALSA

is there a reason why i want OSS over ALSA

will removing ALSA break things?

No reason i can think of, you might have problems i fthe system you want to run the program on need OSS instead of ALSA. I'm not too sure theres much likelihood of that though unless someone else knows of something that might make a difference.

Go with OSS I would say, but only because I read somewhere that its a better sound system.

Mike

---

### Post by Mickeysofine1972 on 2006-11-24
> **Choad said:**
> ok the second tutorial, in the wiki it says SDL_Flip(); but it needs to be SDL_Flip(screen);

also, i made this

```
#include "SDL/SDL.h"

int main(int argc, char* argv[])
{
	// start sdl
	SDL_Init(SDL_INIT_EVERYTHING);
	
	// load an image
	
	SDL_Surface* loaded_image = NULL;
	loaded_image = SDL_LoadBMP("MyImage.bmp");
	
	// convert it to the right format
	
	SDL_Surface* compatible_image = NULL;
	compatible_image = SDL_DisplayFormat(loaded_image);
	SDL_FreeSurface(loaded_image);
	
	// set up the screen
	
	const int SCREEN_WIDTH = 800;
	const int SCREEN_HEIGHT = 600;
	const int SCREEN_BPP = 32;
	
	SDL_Surface* screen = NULL;
	
	screen = SDL_SetVideoMode(	SCREEN_WIDTH, 
					SCREEN_HEIGHT, 
					SCREEN_BPP, 
					SDL_SWSURFACE);
	
	// put image on screen
	
	SDL_Rect position;
	position.x = 0;
	position.y = 0;
	
	SDL_BlitSurface(	compatible_image,
				NULL,
				screen,
				&position);
	
	SDL_Flip(screen);
	
	//Wait 2 seconds
	SDL_Delay( 2000 );
	

	// Destroy remaining surfaces
	SDL_FreeSurface( compatible_image );
	
	
	// quit sdl
	SDL_Quit();
	
	return 0;
}

```

and it compiles but it just displays a black window. my image is NOT displayed. why is this? the image is in the same directory as the binary

Do you have a bmp file in the same folder called 'MyImage.bmp'?

If you don't then you could make one with GIMP or some other image software and place it in that folder. It is a windows bmp btw.

Mike

---

### Post by Choad on 2006-11-24
yes i do. :)

---

### Post by seethru on 2006-11-24
> **Choad said:**
> yes i do. :)
Put some error checking in and have it output the error message you're getting to the terminal. It'll give you some insight into where you're going wrong. Plus, it's just good code to put in redundant checks.

---

### Post by Mickeysofine1972 on 2006-11-24
The only thing that I can see that strikes me as different from our example is that you convert the image BEFORE you set the video surface.

Try doing it after you set the screen up and see what happens.

Mike

---

### Post by Choad on 2006-11-24
> **seethru said:**
> Put some error checking in and have it output the error message you're getting to the terminal. It'll give you some insight into where you're going wrong. Plus, it's just good code to put in redundant checks.
yeah i would have, but i was following the tutorial

dont you think the tutorial should be updated?

i dont actually know how to put error checking in. is it just checking the return value of each function for a positive or negative number?

---

### Post by Choad on 2006-11-24
> **Mickeysofine1972 said:**
> The only thing that I can see that strikes me as different from our example is that you convert the image BEFORE you set the video surface.

Try doing it after you set the screen up and see what happens.

Mike
that did it :)

---

### Post by seethru on 2006-11-24
For future reference, here's an example of a check when loading an image.
```

SDL_Surface *image = IMG_Load(filename);
	if (!image)
	{
		printf("IMG_Load: %s\n", IMG_GetError());
		return 1;
	}

```

---

### Post by VDM on 2006-11-24
> **Choad said:**
> ok the second tutorial, in the wiki it says SDL_Flip(); but it needs to be SDL_Flip(screen);

also, i made this

```
#include "SDL/SDL.h"

int main(int argc, char* argv[])
{
	// start sdl
	SDL_Init(SDL_INIT_EVERYTHING);
	
	// load an image
	
	SDL_Surface* loaded_image = NULL;
	loaded_image = SDL_LoadBMP("MyImage.bmp");
	
	// convert it to the right format
	
	SDL_Surface* compatible_image = NULL;
	compatible_image = SDL_DisplayFormat(loaded_image);
	SDL_FreeSurface(loaded_image);
	
	// set up the screen
	
	const int SCREEN_WIDTH = 800;
	const int SCREEN_HEIGHT = 600;
	const int SCREEN_BPP = 32;
	
	SDL_Surface* screen = NULL;
	
	screen = SDL_SetVideoMode(	SCREEN_WIDTH, 
					SCREEN_HEIGHT, 
					SCREEN_BPP, 
					SDL_SWSURFACE);
	
	// put image on screen
	
	SDL_Rect position;
	position.x = 0;
	position.y = 0;
	
	SDL_BlitSurface(	compatible_image,
				NULL,
				screen,
				&position);
	
	SDL_Flip(screen);
	
	//Wait 2 seconds
	SDL_Delay( 2000 );
	

	// Destroy remaining surfaces
	SDL_FreeSurface( compatible_image );
	
	
	// quit sdl
	SDL_Quit();
	
	return 0;
}

```

and it compiles but it just displays a black window. my image is NOT displayed. why is this? the image is in the same directory as the binary



Not sure if that is the issue, but you could try to change

const int SCREEN_BPP = 32;

to:

const int SCREEN_BPP = 0;

0 basically means to use the current display depth.

---

### Post by Choad on 2006-11-24
> **seethru said:**
> For future reference, here's an example of a check when loading an image.
```

SDL_Surface *image = IMG_Load(filename);
	if (!image)
	{
		printf("IMG_Load: %s\n", IMG_GetError());
		return 1;
	}

```
ok whats the difference between 

SDL_Surface *image

and 

SDL_Surface* image

????

---

### Post by Mickeysofine1972 on 2006-11-24
None thats just a different way of typing it.
Thats not the problem, I will compile your code in the morning and let you know what happens.

BTW I'm on GMT so it might be a while

MIke

---

### Post by Mickeysofine1972 on 2006-11-24
NOTE to Self:

NEVER: set image formats before you initialize the screen! LOL

Thanks for helping up to realize that though, that will really help us if that happens again! 

Mike

---

### Post by Choad on 2006-11-24
> **Mickeysofine1972 said:**
> None thats just a different way of typing it.
Thats not the problem, I will compile your code in the morning and let you know what happens.

BTW I'm on GMT so it might be a while

MIke
im on GMT too, from south west england

i got the sample code from the 2nd or 3rd tutorial, cant remember which, and it compiled fine. cant even be bothered to do any more. i managed to render a bitmap in c++ which is further than i ever got before in this language, so im happy :D

---

### Post by Mickeysofine1972 on 2006-11-25
You think thats good you should see whats coming next :-D 

Next up is animation ! the code is done I just have to write a howto to explain how it works

Mike

---

### Post by Choad on 2006-11-25
edit: never mind i was being an idiot lol

---

### Post by Choad on 2006-11-25
ok explain why this isnt working.... i added to the input tutorial, i wanted to make a bat follow the mouse X coordinate

```

#include <stdio.h>
#include <stdlib.h>
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

int main(int argc, char *argv[])
{
	int done = 0;
	SDL_Surface *screen;
	Uint8 *keys;
	SDL_Event event; //Used to point to SDL_Event
	SDL_Rect dest;

	//Initialize SDL
	if (SDL_Init(SDL_INIT_VIDEO) == 1) {
		printf("Error initializing: %s\n", SDL_GetError());
		return 1;
	}
	//Register SDL_Quit() with atexit
	atexit(SDL_Quit);



	//Set the video mode
	screen = SDL_SetVideoMode(640,480,32,SDL_DOUBLEBUF);
	if (screen == NULL) {
		printf("Cannot set video mode: %s\n", SDL_GetError());
		return 1;
	}
	
	[B]SDL_Rect position;
	SDL_Surface* image = NULL;
	position.x = 10;
	position.y = 50;
	
	image = Load_image("bat.jpg")
	
	if( image == NULL ){
		printf("unable to load %s\n", argv[1]);
	}[/B]

	/** Create a while loop that exits when the variable done = 1.
		This example keeps running until Esc key is pressed. */
	while (done == 0) {
		SDL_Delay(10);
		//Using polling to read input
		while (SDL_PollEvent(&event)) {
			if (event.type == SDL_KEYDOWN) {
				if (event.key.keysym.sym == SDLK_ESCAPE)
					done = 1;
				if (event.key.keysym.sym == SDLK_r) {
					SDL_FillRect(screen, NULL, SDL_MapRGB(screen->format,255,0,0));
					printf("r key pressed\n");
				}
				if (event.key.keysym.sym == SDLK_g) {
					SDL_FillRect(screen, NULL, SDL_MapRGB(screen->format,0,255,0));
					printf("g key pressed\n");
				}
				if (event.key.keysym.sym == SDLK_b) {
					SDL_FillRect(screen, NULL, SDL_MapRGB(screen->format,0,0,255));
					printf("b key pressed\n");
				}
			}//end if
			if (event.type == SDL_MOUSEMOTION) {
				printf("%d %d %d %d\n",event.motion.x,event.motion.y,event.motion.xrel,event.motion.yrel);
				**position.x = event.motion.x;**
			}
		}//end while
		**SDL_BlitSurface(image, NULL, screen, &position);**
		SDL_Flip(screen);
	}//end while


	return 0;
}

```

it compiles just fine, but the bat is nowhere to be seen. i am compiling it with g++ not gcc, if that makes a difference

---

### Post by Mickeysofine1972 on 2006-11-25
> **Choad said:**
> ok explain why this isnt working.... i added to the input tutorial, i wanted to make a bat follow the mouse X coordinate

```

#include <stdio.h>
#include <stdlib.h>
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

int main(int argc, char *argv[])
{
	int done = 0;
	SDL_Surface *screen;
	Uint8 *keys;
	SDL_Event event; //Used to point to SDL_Event
	SDL_Rect dest;

	//Initialize SDL
	if (SDL_Init(SDL_INIT_VIDEO) == 1) {
		printf("Error initializing: %s\n", SDL_GetError());
		return 1;
	}
	//Register SDL_Quit() with atexit
	atexit(SDL_Quit);



	//Set the video mode
	screen = SDL_SetVideoMode(640,480,32,SDL_DOUBLEBUF);
	if (screen == NULL) {
		printf("Cannot set video mode: %s\n", SDL_GetError());
		return 1;
	}
	
	[B]SDL_Rect position;
	SDL_Surface* image = NULL;
	position.x = 10;
	position.y = 50;
	
	image = Load_image("bat.jpg")
	
	if( image == NULL ){
		printf("unable to load %s\n", argv[1]);
	}[/B]

	/** Create a while loop that exits when the variable done = 1.
		This example keeps running until Esc key is pressed. */
	while (done == 0) {
		SDL_Delay(10);
		//Using polling to read input
		while (SDL_PollEvent(&event)) {
			if (event.type == SDL_KEYDOWN) {
				if (event.key.keysym.sym == SDLK_ESCAPE)
					done = 1;
				if (event.key.keysym.sym == SDLK_r) {
					SDL_FillRect(screen, NULL, SDL_MapRGB(screen->format,255,0,0));
					printf("r key pressed\n");
				}
				if (event.key.keysym.sym == SDLK_g) {
					SDL_FillRect(screen, NULL, SDL_MapRGB(screen->format,0,255,0));
					printf("g key pressed\n");
				}
				if (event.key.keysym.sym == SDLK_b) {
					SDL_FillRect(screen, NULL, SDL_MapRGB(screen->format,0,0,255));
					printf("b key pressed\n");
				}
			}//end if
			if (event.type == SDL_MOUSEMOTION) {
				printf("%d %d %d %d\n",event.motion.x,event.motion.y,event.motion.xrel,event.motion.yrel);
				**position.x = event.motion.x;**
			}
		}//end while
		**SDL_BlitSurface(image, NULL, screen, &position);**
		SDL_Flip(screen);
	}//end while


	return 0;
}

```

it compiles just fine, but the bat is nowhere to be seen. i am compiling it with g++ not gcc, if that makes a difference

You need a ';' at the end of this line: 

```

image = Load_image("bat.jpg")

```

Mike

---

### Post by Choad on 2006-11-25
LOL

i was compiling the wrong file

i am a dumbass

edit: works now! doesnt re-draw the whole scene so you end up with a million copies of the bat but hey, who cares! thats easily sorted

---

### Post by Choad on 2006-11-25
ok i have 2 ideas for future tutorials

1 - alpha masking

2 - how to control the framerate so it will run at 60 fps instead of as fast as the processor can handle!

---

### Post by Mickeysofine1972 on 2006-11-25
I'm curious? why do you want to limit the frame rate?

Mike

---

### Post by Choad on 2006-11-25
so it doesnt max out the cpu for a start

if you have a pong game that uses 100% of the cpu, something is wrong

---

### Post by Mickeysofine1972 on 2006-11-25
Well you could use a timer to make the game run at a certain pace.

Thats going to be in another HOWTO soon to come so we can take care of that later :-D

Mike

---

### Post by hod139 on 2006-11-25
Framerate control is very very easy if you use the SDL_gfx library (it's in the repositories).  Then in your code you add
```

#include "SDL_framerate.h"

FPSmanager fps_manager;
SDL_initFramerate( &fps_manager );
// you want the top framerate to be 60 for example
SDL_setFramerate( &fps_manager, 60 );
while (looping)
{
 // process your graphics, etc here

 SDL_framerateDelay( &fps_manager);
}


```Then when building, you have to do:
```

gcc `sdl-config --cflags --libs` -lSDL_gfx -o foo foo.c  

``` Note, I had to add -lSDL_gfx

I'll try to be as active as I can.

---

### Post by Choad on 2006-11-25
bargain!

i am almost begining to understand all this pointer buisness too. tho it seems like a whole lot of hassle!

---

### Post by Mickeysofine1972 on 2006-11-25
As Einstein said "everything can be made simpler but not simple" or something like that! :-D

The truth is that can always make thing simple unless you want to give up control.

Its a shame but thats true for most things.

Pointers give you the ability to access memory directly, but that comes at the cost of having to know how that works. This is a s simple as it can be but not really 'simple'.

Mike

PS - that almost sounds like I know what I'm talking about LOL

---

### Post by Mickeysofine1972 on 2006-11-26
Update: weekends are a bit of an inconvenience when it comes to developing a series of HOWTOs for SDL.

The reason is that I have 'responsibilities' yes you've guessed it I'm ad husband and farther and I must on occasion step into the realms of what women call 'real life', ( i just know the politically correct ploice will get me for saying that but its true.

Well, rest assured that when the weekend is over I will return to plowing though the articles about SDL.

We have had a great response and we have also formed a of me, Seethru and VDM we are all working in a collaborative way to generate some REALLY top notch games programming articles.

If you would like to contribute you are very welcome as feel that the more support from the Ubuntu/Linux community the better.

So if your using ubuntu or just linux or you use windows but can compile SDL we can use anything you would like to contribute HOW EVER SMALL.

Don't be afraid we will only praise you for you help.

New HOWTO due in the next week include timers, tiled/platform background rendering and much much more!

Mike

---

### Post by Sslaxx on 2006-11-27
Cheers for this! At the mo it's mostly HowTos, I see. Any plans for FAQs, or other articles? I'd be happy to contribute what I can.

---

### Post by Mickeysofine1972 on 2006-11-27
We weren't planning a FAQ as such just a series of howto or tutorials that describe the whole game making process.

I know we're focusing on programming but I hope to get artist involved from other parts of the forums so there will be articles on there for them too.

This is a games developing resources so there should be something for everyone who wants to get involved in developing for the Ubuntu/Linux platform :-D

BTW we'd love to have you contribute anything you can ;-) and of course you can expect to get full credit in our articles.

Mike

---

### Post by Choad on 2006-11-28
i have attached a little thing i made. could be the beginnings of a maze game. i would write up a tutorial for it but its not finished and i dont have an account with that wiki

it nicely combines alot of the previous tutorials

-input
-sprites
-image loading

and also does some new stuff

-a simple level design
-collision
-changing sprite to face the direction you are traveling

right now, i have designed the (really boring) level in code. i was hoping someone could modify it to load "level.txt" where a simple map of 0's and 1's could define the level. i dont know any file i/o in c++

anyway.... here it is

oh my coding style is pretty different from the stuff before. i use much less comments and different nesting style. 

i also missed out alot of error checking.... coz i forgot basically

compile with 

$ g++ `sdl-config --cflags --libs` -o maze maze.cpp -lSDL -lSDL_image

:)

---

### Post by Mickeysofine1972 on 2006-11-28
WOW Thats excellent!

Thats definitely going to included as a collision detection howto!

Your code may not be the same as mine or VDM & seethru but you still right clearly and it make good sense so you get my thumbs up:D 

Mike

---

### Post by Mickeysofine1972 on 2006-11-28
Hi Choad

If you would like access to the wiki please add me to you msn my id is : [email]hibbert_michael@hotmail.com[/email] or email me a an email you can easily be contacted on as I have to have an email address to invite you to edit the wiki.

The rules are simple, you can make as many wiki pages as you like but you cannot edit the main page without my permission.

other than that go for it!

Mike

---

### Post by Choad on 2006-11-29
lol i went crazy and now its turning in to a "rocks n gems" type game

but i am going about it all wrong. i dont really know object programming yet so everything is done procedural, and to be honest it sucks. but hey it works... kinda. half the stuff isnt implemented yet, but i have had enough for thisevening so i thought i'd share my work

compile with same command

---

### Post by Mickeysofine1972 on 2006-11-29
Excellent ! nice touch with the gravity as well!

Mike

BTW where are you getting your tiles and sprites? I'm using the GPL spritelib librabry

---

### Post by Choad on 2006-11-29
making them

got the grass from grsites.com, everything else was hnd made in gimp

---

### Post by Mickeysofine1972 on 2006-11-29
good stuff ;-)

Mike

---

