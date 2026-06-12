---
title: "HOWTO: Displaying a picture on the screen"
date: 2006-11-22
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-11-22
This is the second in a series of HOWTO's on how to develop games on the Ubuntu/Linux platform using Simple DirectMedia Layer (SDL).

This session covers the following topics:


1) Using Surfaces
2) Initialzing the Display/Screen
3) Putting images on screen


1) Using Surfaces
SDL along with other API's like Directx deals with images whether on-screen or in memory as a flat 2d image. In SDL this is referred to as a 'Surface'. Please note that even the screen is classed as a surface. To load an display a picture from a file you must first create a surface and load the image onto the surface.

```

SDL_Surface* loaded_image = NULL;
loaded_image = SDL_LoadBMP("MyImage.bmp");

```

This code above creates a 'pointer' to the surface that SDL_LoadBMP creates when it loads the MyImage.bmp file.

```

WARNING: SDL_LoadBMP() loads you picture into memory in the same format as it is stored! That means a 24bpp picture is loaded and stored taht way!

```

That might not mean very much to you right now but if I was to tell you that if you screen bpp is 32bpp then you can see that they are not the same. On top of that, >everytime< you put that picture onto your screen SDL has to convert the picture from 24bpp to 32bpp. Imagine trying to do that 32+ times per second. You can imagine that it wastes alot of time doing that.

One solution is to convert the image as soon as it is loaded and from that point onwards it wont need to be converted again.

```

SDL_Surface* compatible_image = NULL;
compatible_image = SDL_DisplayFormat( loaded_image );
SDL_FreeSurface( loaded_image );

```

SDL_DisplayFormat() converts the loaded_image surface any returns another surface that is the same bpp as the current display bpp.

SDL_FreeSurface() destroys the incompatible image surface so that we can free up the memory it uses.

SDL_Surfaces can be hardware, (video card memory referred to as SDL_HWSURFACE), or software, (system memory referred to as SDL_SWSURFACE). This is important as later we a will create a surface for the screen but create it as a SDL_SWSURFACE to ensure compatibility with you graphics hardware. Some of you out there might not be able to run the programs otherwise!

2) Initialzing the Display/Screen
Firstly, we can't view anything unless we tell SDL to create a place to display the picture. To do this we need to decide what dimensions the area will be. The reasons for this is that you may not be running in full-screen modes; you may be running in windowed modes. This means you can have a variable width and height for you display.

```

const int SCREEN_WIDTH = 800;	// screen dimesions
const int SCREEN_HEIGHT = 600;
const int SCREEN_BPP = 32;	// screen color depth

SDL_Surface* screen = NULL; // pointer to screen surface

screen = SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE ); // create screen 800x600x32bpp in software rendering mode.

```

3) Putting images on screen
SDL treats surfaces as rectangles when it handles placing them on screen. Because of this, we must declare a SDL_Rect and set some of its information up before we can place the image on-screen.

```

SDL_Rect position;
position.x = 0; // were just putting the picture in the top left corner
position.y = 0; // at position 0,0 

```

And finally we place the image in the screens buffer surface and display it.

```

SDL_BlitSurface( compatible_image, NULL, screen, &position ); // put the image on the screen surface

SDL_Flip(); // send the screen surface to be displayed

```

Notice the NULL in the arguments for SDL_BlitSurface; thats only used if you only want to display part of the picture. You can specify which part by setting up another SDL_Rect and putting it where the NULL is. This can be used when displaying frames for animation, which is the subject of anothe HOWTO that will come soon.

Well! there it is! First you learned how SDL treats images and the screen as 'Surfaces' to be draw upon, then you learned how to load a picture and finally how to display it.

Check out the c++ program attached for a demo that you can compile by typing the following command:
```

g++ `sdl-config --cflags --libs` -o mypic mypic.cpp
./mypic

```

I and a few others have reported that the above method of compiling generates errors! if that doesn't work for your system type:

```

g++ -o mypic mypic.cpp -lSDL
./mypic

```

We're currently looking into the peculiarity and we will keep you in formed. For the time being all other HOWTOs will compile using the second form of commands.

You can create a picture for yourself to use with the program example as long as you save it as a window$ BMP called MyImage.bmp.

Please feel free to comment or contribute!

Mike

```

// mypic.cpp

// include SDL libraries
#include "SDL.h" 
#include <string.h>

int main( int argc, char* argv[])
{
	SDL_Surface* loaded_image = NULL;	// create surface pointers
	SDL_Surface* compatible_image = NULL;
	SDL_Surface* screen = NULL;

	SDL_Rect position;

	const int SCREEN_WIDTH = 800;		// set screen dimensions
	const int SCREEN_HEIGHT = 600;
	const int SCREEN_BPP = 32;

	position.x = 0; 			// initialize position rectangle
	position.y = 0;
	atexit(SDL_Quit);
	// create screen 800x600x32bpp in software rendering mode.
	screen = SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE ); 

	if ( screen == NULL ) {
            fprintf(stderr, "Unable to set 800x600 video: %s\n", SDL_GetError());
        exit(1);
        }

	// load the picture (a windows bmp) which you can create yourself using GIMP
	loaded_image = SDL_LoadBMP("MyImage.bmp"); 
	
	// re-format the image to 32bpp
	compatible_image = SDL_DisplayFormat( loaded_image );
	// destroy the old picture
	SDL_FreeSurface( loaded_image );

	// put the image on the screen surface
	SDL_BlitSurface( compatible_image, NULL, screen, &position ); 

	SDL_Flip( screen ); // send the screen surface to be displayed

	//Wait 2 seconds
	SDL_Delay( 2000 );
	

	// Destroy remaining surfaces
	SDL_FreeSurface( compatible_image );
	// Close down SDL
	
}


```

---

### Post by hod139 on 2006-11-22
Same comments from your first post:
when using SDL you should be including it as:
     ```

     [LEFT]#include "SDL.h"[/LEFT]
 

```**not**
     ```

     [LEFT]#include "SDL/SDL.h"[/LEFT]
 

```and then when building, you should be typing
     ```

     [LEFT]g++ `sdl-config --cflags --libs` -o mypic mypic.cpp[/LEFT]


```This will allow your examples to be portable across multiple platforms.

 You should be using 
     ```

     [LEFT]atexit(SDL_Quit)[/LEFT]
 

```so SDL_Quit is called, even if you application unexpectedly quits.

You should also be checking the return calls of the SDL functions to see if they actually succeeded. For example
```
screen = SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE ); // create screen 800x600x32bpp in software rendering mode.;
    if ( screen == NULL ) {
        fprintf(stderr, "[COLOR=#000000]Unable to set 800x600 video: %s\n[/COLOR]", SDL_GetError());
        exit(1);
    }
```

---

### Post by Mickeysofine1972 on 2006-11-22
Adjustments made

Mike

---

### Post by Mickeysofine1972 on 2006-11-22
I'd just like to say that I am really pleased with response from you guys

Keep up the good work! and keep contributing!

We could have a game in the offing!

Mike

BTW is 'Complementarity' a real word mr hod139? and how would one cook with it?

---

### Post by hod139 on 2006-11-22
> **Mickeysofine1972 said:**
> 
BTW is 'Complementarity' a real word mr hod139? 

Yeah, it is real.  The linear complementarity problem (LCP) is a mathematical formulation that is very useful in formulating contact dynamics.  If you really want to hear more details about the math you can pm me, but it is fairly advanced: an LCP comes from the KKT conditions of a quadratic program.  At the highest level, LCPs allow us to more formally model systems that exhibit "unilateral" or one sided constraints. e.g. the non-penetration constraint.  

> and how would one cook with it?
I forgot I even had by website on my profile, so I was a little confused with what you were saying at first.  [Cooking with complementarity]("http://www.cs.rpi.edu/research/pdf/06-08.pdf") is a technical report I wrote to help elucidate the use of complementarity in contact dynamics through use of examples (the recipes so to speak).  So cooking is my lame attempt at humor. Feel free to pm me about any of this, but I doubt many people here want to see a general discussion on the topic.

Lastly, the [open dynamics engine]("http://ode.org/") project is an open source game engine which uses complementarity in almost the same fashion illustrated in my tech report.  I say almost, because they make some assumptions (intentional hacks) about friction to speed up solution time.  While I am not associated with the project, I am very familiar with the time-stepping scheme they are using (they are using a scheme developed by Dave Stewart and Jeff Trinkle, and Jeff is my adviser), so if you have any questions about this, again just pm me.

---

### Post by Mickeysofine1972 on 2006-11-23
Indeed I will for a later HOWTO ;-)

Mike

---

