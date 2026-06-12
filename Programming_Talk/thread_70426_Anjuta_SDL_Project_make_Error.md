---
title: "Anjuta SDL Project make Error"
date: 2005-09-29
forum: Programming Talk
---

### Post by remin8 on 2005-09-29
I really know nothing about makefiles but i think that is where my problem might be. I have all the proper packages for dev under SDL/OpenGL/Anjuta. So far I have the following steps to create a SDL app with Anjuta:

Create new generic terminal project (c++)

Go to Settings -> Compiler and linker settings -> Options and add **[COLOR="Blue"]'sdl-config --cflags'[/COLOR]** to CFLAGS and **[COLOR="Blue"]'sdl-config --libs' -lGL -lGLU -lSDL_image -lSDL_mixer[/COLOR]** to LDFLAGS

I configure the project according to Anjuta's wishes

I add **#include "SDL.h"** to the main.cc file and save it

At this point is where my problem is. When I go to build the project it gives me the warning **[COLOR="Red"]g++: cannot specify -o with -c or -S and multiple compilations[/COLOR]**!!!

Does anyone know what I am doing wrong here? I am about to go back to CLI I am so fustrated.

---

### Post by JmSchanck on 2005-09-30
"sdl-config --cflags" just expands to -I/usr/include/SDL -D_REENTRANT, try just doing 
```

-I/usr/include/SDL

```
under CFLAGS.
If I set up a project exactly how you describe I get the same error but by dropping the -D_REENTRANT it works.

---

### Post by remin8 on 2005-10-01
I try putting -I/usr/include/SDL under my CFLAGS block in Compiler and Linker Settings but when I do it can't find SDL.h when I compile. I try different combinations and still no success... what is going on!? It shouldn't be this hard!

---

### Post by JmSchanck on 2005-10-01
I don't know if you've tried doing it this way already but here's another way that I know works:

In Anjuta go to settings > compiler and linker settings

Click the Include paths tab at the top and type in /usr/include/SDL (assuming this is where your SDL include files are)

Click the Libraries tab and enter the libraries you want to use ex:
SDL
SDL_image
SDL_ttf
(entered 1 at a time and make sure the boxes are checked.)

Under additional options under the options tab leave everything blank.

---

### Post by remin8 on 2005-10-01
SUCCESS! Thanks JmSchanck!!! I was tried added that dir under Settings -> Source Path with no success. It always seems like I get hung up on the easy stuff! 

In case anyone is refrenceing this thread. All you have to do is add /usr/include/SDL/ in your include paths!

---

### Post by remin8 on 2005-10-01
AHHH! New problem... now even though I get no errors about SDL.h (and all the permissions on all the SDL include files are correct) I now can't get to the actual SDL functions... it gives me an error that SDL_Init and others are undefinded refrences. Anybody know what is going on? I am going to write a tutorial as soon as I find out waht has been going wrong, because nothing out there really exists for Anjuta and SDL.

---

### Post by remin8 on 2005-10-02
Help! I can compile fine via CLI but Anjuta doesn't work....

---

### Post by remin8 on 2005-10-02
Ok, I think I got it. Maybe it might be of some help to some people out there....


[SIZE="7"]Ubuntu, Anjuta, & SDL Tutorial[/SIZE]
20051001 @ 1741 BY JAY TOMTEN | REMIN8.COM
[SIZE="5"]Install Packages[/SIZE]
First you need to install all the packages you will need for SDL development and Anjuta. The following worked for me on Ubuntu 5.04 and 5.10,  more SDL development libraries are available if you look but these 3 can get most stuff done:

anjuta (including dependencies)
libtool
libsdl1.2-dev (including dependencies)


[SIZE="5"]
Create Project[/SIZE]
Start Anjuta and select the Application Wizard.

Select Generic/Terminal project

Enter a name for your project like testSDL and select whether you want to use C or C++:

If you have all the correct packages installed for Anjuta the project will configure with no problems. The next step is to go to Settings -> Compiler and linker settings -> Include Paths. Type in /usr/include/SDL/ and click add to allow the SDL header files to be accessible to your project:

Now go to the  Settings -> Compiler and linker settings -> Libraries tab and add SDL, SDL_image, and SDL_mixer to get you started. You will have to type them in manually and click add for each library you wish to use:

Close the Compiler and linker options window and click OK to rebuild all files in the project durring the next build. Now select main.cc under source -src to edit your main c++ file:

Now replace the code in the main.cc file with the code below:

```
// testSDL

// includes
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <SDL.h>

////////////////////////////////////////////////////////////////
// setPixel()
////////////////////////////////////////////////////////////////
void setPixel(SDL_Surface *screen, int x, int y, Uint8 r, Uint8 g, Uint8 b) {
	Uint8 *ubuff8;
	Uint16 *ubuff16;
	Uint32 *ubuff32;
	Uint32 color;
	char c1, c2, c3;
  
	// Lock the screen, if needed 
	if(SDL_MUSTLOCK(screen) < 0 && SDL_LockSurface(screen) < 0) return;
  
	// set color 
  	color = SDL_MapRGB( screen->format, r, g, b );
	
	// How we draw the pixel depends on the bitdepth 
	switch(screen->format->BytesPerPixel) {
	case 1: 
		ubuff8 = (Uint8*) screen->pixels;
		ubuff8 += (y * screen->pitch) + x; 
		*ubuff8 = (Uint8) color;
		break;
	case 2:
		ubuff8 = (Uint8*) screen->pixels;
		ubuff8 += (y * screen->pitch) + (x*2);
		ubuff16 = (Uint16*) ubuff8;
		*ubuff16 = (Uint16) color; 
		break;  
	case 3:
		ubuff8 = (Uint8*) screen->pixels;
		ubuff8 += (y * screen->pitch) + (x*3);
		if(SDL_BYTEORDER == SDL_LIL_ENDIAN) {
			c1 = (color & 0xFF0000) >> 16;
			c2 = (color & 0x00FF00) >> 8;
			c3 = (color & 0x0000FF);
		} else {
			c3 = (color & 0xFF0000) >> 16;
			c2 = (color & 0x00FF00) >> 8;
			c1 = (color & 0x0000FF);	
		}
		ubuff8[0] = c3;
		ubuff8[1] = c2;
		ubuff8[2] = c1;
		break;
	case 4:
		ubuff8 = (Uint8*) screen->pixels;
		ubuff8 += (y*screen->pitch) + (x*4);
		ubuff32 = (Uint32*)ubuff8;
		*ubuff32 = color;
		break;
	default:
      fprintf(stderr, "Error: Unknown bitdepth!\n");
    }
  
	// Unlock the screen if needed 
	if(SDL_MUSTLOCK(screen)) SDL_UnlockSurface(screen);
}

////////////////////////////////////////////////////////////////
// drawPicture()
////////////////////////////////////////////////////////////////
void DrawPicture(SDL_Surface* screen) {
	// int r = 255, g = 0, b = 255;
	int x, y;
	for(x = 0; x < screen->w; x++ ) {
		for( y = 0; y < screen->h; y++ ) {
			setPixel(screen, x, y, x, y, 0);
		}
	}
	SDL_Flip(screen);
}

////////////////////////////////////////////////////////////////
// main()
////////////////////////////////////////////////////////////////
int main(int argc, char* argv[]) {
	// Declare Variables 
	SDL_Surface *screen;
	SDL_Event event;
	int exitkey = 0;
	
	// Initialize SDL, exit if there is an error. 
	if( SDL_Init(SDL_INIT_VIDEO) < 0 ) {
		fprintf(stderr, "Could not initialize SDL: %s\n", 
		SDL_GetError());
		return -1;
	}
  
	// When the program is through executing, call SDL_Quit 
	atexit(SDL_Quit);
  
	// Grab a surface on the screen
	screen = SDL_SetVideoMode(1280, 1024, 32, SDL_SWSURFACE|SDL_ANYFORMAT);
	if( !screen ) {
		fprintf(stderr, "Couldn't create a surface: %s\n",
		SDL_GetError());
		return -1;
	}
  
	// Print Some info
	printf("Created SDL Surface: %x\n", screen);
	printf("\t BPP \t\t : %d\n", screen->format->BytesPerPixel );
	printf("\t XRes \t\t :%d\n", screen->w );
	printf("\t YRes \t\t :%d\n", screen->h );
  
	// input watcher
	while(!exitkey) {
		DrawPicture(screen);
		while(SDL_PollEvent(&event)) {
			switch( event.type ) {
			case SDL_QUIT:
				exitkey = 1;
				printf("Got quit event!\n");
				break;
			case SDL_KEYDOWN:
				printf("Key hit - exiting!\n");
				exitkey = 1;
				break;
			}
		}
	}
	return 0;
}
```

Now you should be all set. Select Build All from the Build menu and watch your project come to life. Execute the program to see what you made.

I hope this tutorial helps some people out there. Visit remin8.com/jay and let me know what you think.

---

### Post by Lord Illidan on 2006-02-15
Great, this should be made a real howto..

---

