---
title: "HOWTO: Checking for Input in SDL"
date: 2006-11-24
forum: Programming Talk
---

### Post by seethru on 2006-11-24
This is the fifth HOWTO in a series of HOWTOs about game development using Simple DirectMedia Layer.

This HOWTO covers the following subjects:

1) Taking input from a keyboard
2) Input from a mouse, specifically it's location on the screen.

Inputs in SDL are checked for by testing in a loop if anything has happen to the computers inputs. This is called 'Polling' for input. All we have to do to 'Poll' for information is execute one function that SDL has built in to get the needed guidance from a user.

Lets start out by laying out all the includes, and initializing SDL so that we can see the change a key press makes.

```

#include <stdio.h>
#include <stdlib.h>
#include "SDL.h"

int main(int argc, char *argv[])
{
	int done = 0;
	SDL_Surface *screen;
	Uint8 *keys;
	SDL_Event event; //Used as dot pointer to SDL_Event
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

```

Ok, so now that we have SDL setup, with the variables we'll need for this tutorial, lets continue on.

1) Taking input from a keyboard is relatively easy in SDL, and uses two fairly simple things: an SDL_Event data structure, and an SDL_PollEvent function to fill in the data structure with key presses and mouse movement information.
```

	/* Create a while loop that exits when the variable done = 1.
		This example keeps running until Esc key is pressed. */
	while (done == 0) {
		//Using polling to read input
		while (SDL_PollEvent(&event)) {
			if (event.type == SDL_KEYDOWN) {
				if (event.key.keysym.sym == SDLK_ESCAPE)
					done = 1;
				if (event.key.keysym.sym == SDLK_r) {
					SDL_FillRect(screen, NULL, SDL_MapRGB(screen->format,255,0,0)); // This line changes the color to red.
					printf("r key pressed\n");
				}
				if (event.key.keysym.sym == SDLK_g) {
					SDL_FillRect(screen, NULL, SDL_MapRGB(screen->format,0,255,0)); // This line changes the color to green.
					printf("g key pressed\n");
				}
				if (event.key.keysym.sym == SDLK_b) {
					SDL_FillRect(screen, NULL, SDL_MapRGB(screen->format,0,0,255)); // This line changes the color to blue.
					printf("b key pressed\n");
				}
			}//end if

```
Ok, this chunk of code is what polls for the specific key presses. In this example, we've made r,g, and b change the color of the screen using SDL_FillRect and SDL_MapRGB. As you can see, there is a while loop that runs to check for any form of input. In this case, if a key is down, it throws it into the if statements which then check to see if it's one of the three keys.




2.) Mouse input, specifically mouse location and movement.
```

			if (event.type == SDL_MOUSEMOTION) {
				printf("%d %d %d %d\n",event.motion.x,event.motion.y,event.motion.xrel,event.motion.yrel);
			}

```
So these three lines of code go INSIDE the polling while loop. Basically what this does is outputs the current x and y location of the mouse pointer to the terminal window.

In both cases, you'll notice the dot pointer to SDL_Event. For the keyboard it's event.key, and for the mouse it's event.motion.

Lets close our loops in the code now and finish the main() function.

```

		}//end while
		SDL_Flip(screen);
	}//end while


	return 0;
}

```

You can compile this example by running
```

gcc `sdl-config --cflags --libs` -o input input.c
./input

```

Inside the package I've included a very helpful PDF which lists the different keys on a keyboard, and buttons on a mouse.

Enjoy :)

---

### Post by Gustav on 2006-11-24
I think this is the fifth HOWTO (the fourth being about sprites)

---

### Post by Mickeysofine1972 on 2006-11-24
oops your right lol

Mike

---

### Post by edo333 on 2006-11-24
> **seethru said:**
> 

Inside the package I've included a very helpful PDF which lists the different keys on a keyboard, and buttons on a mouse.

Enjoy :)

I'm afraid I did not see the mouse events listed in the PDF am I missing something.  
Thanks for all the keyboard events by teh way it's nice to have them all listed in one place.

---

### Post by seethru on 2006-11-24
> **edo333 said:**
> I'm afraid I did not see the mouse events listed in the PDF am I missing something.  
Thanks for all the keyboard events by teh way it's nice to have them all listed in one place.
You're very right, I'll make up a list of them later and post them, sorry about that lol.

---

### Post by Mickeysofine1972 on 2006-11-24
The event.motion is where that gets handled as well as event.type

All you need to check is the .x .y .xrel .yrel for mouse movement

Mouse buttons are checked by looking for event.type = SDL_MOUSEBUTTONDOWN

if it is pressed you can do the following:
```

if( SDL_GetMouseState(NULL, NULL) & SDL_BUTTON(1) ) {
     // do something because mouse button 1 is pressed
}

```

That will tell your if the button you want is pressed.

Mike

---

### Post by Choad on 2006-11-24
concidering games are very object based programs, wouldnt it make sense to write these tutorials in c++ rather than c?

im only new to both these languages so i could be wrong but the printf function is a c thing isnt it? whereas cout is the c++ way of doing it

could be wrong tho lol

---

### Post by seethru on 2006-11-24
> **Choad said:**
> concidering games are very object based programs, wouldnt it make sense to write these tutorials in c++ rather than c?

im only new to both these languages so i could be wrong but the printf function is a c thing isnt it? whereas cout is the c++ way of doing it

could be wrong tho lol
It would, I personally don't have the knowledge to write these in c++. Currently in school for game development, and only know c w/ sdl ;). I'm currently programming a game using c and sdl, so it isn't that big of a difference.

---

### Post by Mickeysofine1972 on 2006-11-24
> **Choad said:**
> concidering games are very object based programs, wouldnt it make sense to write these tutorials in c++ rather than c?

im only new to both these languages so i could be wrong but the printf function is a c thing isnt it? whereas cout is the c++ way of doing it

could be wrong tho lol

Good point actually!

Fortunately I know both so I will try to generate this in C and/or C++ as I agree that it will probably work better if we stick to one language.

Saying that though, I have a preference for C++ in this regard as I do think it will make life easier in the long run.

I will be happy in the meantime to supply C++ versions of any C based HOWTOs

The beauty of C++ is that you also can refer to old C based methods too!, (like printf).

Who knows this might even turn into Python at one stage!

Thanks for the feedback it helps us loads to refine our methods etc.



Mike

---

### Post by edo333 on 2006-11-25
I'm not much of a programmer, and I'm fairly new to the whole ubuntu/linux world, but I really enjoy how I can customize everything.  What I would like to do is write, or download an applet that will run in the background on startup and launch a predetermined application on middle mouse click.  
Specifically I want it to launch 3d desktop.  
I'm not sure how much work is involved in programming this, but it seems to me it would be pretty easy.  
Can someone write an applet for this?
Or give me a good start to writing my own.  
Thanks

---

### Post by Mickeysofine1972 on 2006-11-25
My best advice is to start a new thread for this as other programmers who may not look at this thread because their not interested in games programming might not see.

I cant really get involved in that sort of project myself but others might just do for you if you get their attention with a new thread.

Mike

---

