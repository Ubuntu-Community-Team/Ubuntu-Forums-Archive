---
title: "Easy to use library for 2D drawing?"
date: 2008-02-04
forum: Programming Talk
---

### Post by yesint on 2008-02-04
Dear All,
I'm looking for some easy to use library to write rather simple 2D game. It should not be super-fast or hardware accelerated, but I want it to be more or less simple to learn and to understand. The side-purpose of this project is to gain some experience in Linux programming and C/C++, which I never used for serious things (I'm a fortran expert). I looked at openGL but it is really very scary - I don't want to spend months learning how to draw a pixel on the bitmap.
What I need:
* (reasonably) fast access to individual pixels
* drawing lines and basic shapes
* loading pictures
* easy access to keyboard events

Any suggestions are appreciated!

---

### Post by Wybiral on 2008-02-04
Check out SDL, then check out SDL_gfx (it's a side-library that makes it easier to draw simple shapes and such). You can also use OpenGL with SDL when you're up to it.

---

### Post by hod139 on 2008-02-04
I have no personal experience with it, but I've heard good things about libcairo: [http://www.cairographics.org/](http://www.cairographics.org/)

---

### Post by mike_g on 2008-02-04
Yes, SDL sounds perfect for what you want. It handles graphics, sound, and input. Setting it up on Ubuntu is also very easy; just type:
```
sudo apt-get install libsdl1.2-dev
```
And it will set the development libraries for you.

Once it installed you can test it with this prog if you like:
```
#include "SDL/SDL.h"
#include <math.h>

#define GRAPHICS_WIDTH 256
#define GRAPHICS_HEIGHT 256
#define BITDEPTH 32
#define DEG_TO_RAD 0.0174532925
#define FRAME_LIMIT 1000 / 20 		//Limit the animation to 20 frames per second

SDL_Surface *screen = NULL;  
SDL_Event event;

void WritePixel(int x, int y, Uint32 col)
{
    Uint32 *pix;  
    pix=screen->pixels+(x+y*GRAPHICS_WIDTH)*4;
    *pix=col; 
}  

int main()
{
       // Setup stuff
	if(SDL_Init(SDL_INIT_VIDEO) !=0) 
		return 1;
   	screen = SDL_SetVideoMode(GRAPHICS_WIDTH, GRAPHICS_HEIGHT, BITDEPTH, 0);
	if(screen == NULL) 
		return 1;
	
	int x;
	int quit = 0;
	int anim = 0;	
	unsigned timer;

	//This is the main loop that runs until the program ends
	while(!quit)
	{
		//Get the start time at the begining of each loop
		timer = SDL_GetTicks();	

               //Clear teh screen
		SDL_FillRect(screen, NULL, 0);	
	
                // Draw something here
		for(x=0; x<GRAPHICS_WIDTH; x++)
			WritePixel(x, 128+cos(x*DEG_TO_RAD+anim)*100, 0xFFFFFFFF);

                // Flip the stuff drawn into view
		if(SDL_Flip(screen)==-1) 
			return 1;
		
		//This code checks for a keypress, which signals to end the program
		while(SDL_PollEvent(&event))
                     if(event.type==SDL_KEYDOWN)
                         quit=1;
		
		//Increment  animation
		if(++anim > 359) anim = 0; 	

		//This delays the program so that it does not run too fast
		timer = SDL_GetTicks()-timer;
		if(timer < FRAME_LIMIT) SDL_Delay(FRAME_LIMIT-timer);
	}

	SDL_Quit();
	return 0;
}
```
That will basically set up the screen and draw some stuff. To compile it you will have to link SDL:
```
gcc -Wall filename -lSDL
```
You can also find some good SDl tutorials Here:
[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)
and here:
[http://student.kuleuven.be/~m0216922/CG/index.html](http://student.kuleuven.be/~m0216922/CG/index.html)

---

### Post by cb951303 on 2008-02-04
with those requirements i wouldn't go with SDL because the core library doesnt have drawing line and shape functions. also accessing to individual pixels is almost never fast :)
I would recommend you allegro ([www.allegro.cc](www.allegro.cc))
also notice that these libraries doesn't have hardware acceleration. if you need it you must learn opengl now or then.  my personal choice would be to go with "opengl + glfw". you can do countless things with this combination ;)

cheers

---

### Post by yesint on 2008-02-05
Thank you guys! I'll check these libraries.

---

### Post by bfhicks on 2008-02-05
IMO, opengl is super easy to get set up. Install GLUT, then install glutmaster: [http://www.stetten.com/george/glutmaster/glutmaster.html]("http://www.stetten.com/george/glutmaster/glutmaster.html")

glutMaster is an excellent C++ wrapper to allow you to program in C++ instead of C. Using the demoWindow class located on the glutmaster page, it is ready to compile & run. It is then very simple to modify this demoWindow class to do more complex things, and eventually write your own class.

I was new to opengl/glut and graphics programming and it took me no longer than a few hours with it to see something fairly impressive.

There are also tons of tutorials on the web (doing a basic google search provided tons of results) that can help you along the way. 

Only one method needs to be touched and that's the "CallBackDisplayFunc()".  There is a lot of other things happening in that class, but paying attention to this one method helps you focus on what you actually want to do.

I saw that you mentioned wanting to stay away from opengl but it's not as scary as it may seem at first.

---

