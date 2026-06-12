---
title: "C++ - Segmentation Fault help"
date: 2009-02-21
forum: Programming Talk
---

### Post by jacensolo on 2009-02-21
I'm trying to make a physics demonstration "game". I was pretty sure my code wouldn't work because of some silly logic error I got wrong, but I get a segmentation fault on run. This is my first real (besides console I/O and such) C++ program so I don't know what to look for. It is organized but will look jumbled  in many files so bear with me.

I'm using SDL btw.

main file:
[php]#ifdef HAVE_CONFIG_H
#include <config.h>
#endif

#include <iostream>
#include <stdlib.h>
#include "Engine.h"

int main(int argc, char *argv[])
{
	Engine physics = Engine();
	Surface* screen = new Surface(800,400,16);
	Surface* bgimage = new Surface("bg.bmp");
	Surface square("square.bmp", screen->surface, 0, 0);
	Object* ball = new Object("square.bmp", 10.0);
	while (true)
	{

		screen->Draw_Background(bgimage->surface);
		//square.Move(5,2, screen->surface);
		ball->MoveObject(ball->ApplyForce(40.0, 90.0), bgimage->surface);
		//SDL_DELAY(10);
	}
	
}[/php]
[php]#ifndef ENGINE_H
#define ENGINE_H

#include "SDL.h"
#include "Object.h"
#include "Surface.h"


class Engine
{
public:
	//Initiliaze the game - Mouse, keyboard, etc
	Engine();
public:
	SDL_Surface* MakeScreen(int width, int height, bool fullscreen);
	SDL_Surface* MakeScreen(int width, int height);
	void events();
	void update();
};
#endif[/php]
[php]#include "Engine.h"

//class Engine {};

Engine::Engine()
{
	SDL_Init(SDL_INIT_VIDEO);
}
SDL_Surface* Engine::MakeScreen(int width, int height, bool fullscreen)
{
	if (fullscreen == true)
	{
		return SDL_SetVideoMode(width, height, 16, SDL_DOUBLEBUF | SDL_FULLSCREEN);
	}
	else
	{
		return SDL_SetVideoMode(width, height, 16, SDL_DOUBLEBUF);
	}
}

SDL_Surface* Engine::MakeScreen(int width, int height)
{
	return SDL_SetVideoMode(width, height, 16, SDL_DOUBLEBUF | SDL_ANYFORMAT);
}[/php]
[php]#ifndef OBJECT_H
#define OBJECT_H

#include "Surface.h"
#include <math.h>
class Object : public Surface
{
	/*The resolution of the program is 800x600 and the field is 400x300 - Each pixel is 2 meters*/
	float* g; //The ammount of acceleration of gravity
	float mass; //the mass of the object in kg
	float weight; //in newtons
	SDL_Rect* velocity;
	bool grounded; //is it on the ground?
	//SDL_Rect* acceleration; //acceleration
	
	
public:
	
	Object(const char* file, float mass); //calls the Surface constructor and calculates the weight
	SDL_Rect* ApplyForce(float newtons, float angle); //Returns the offset
	void MoveObject(SDL_Rect* accel, SDL_Surface* screen); //check to see if the object can move then move it
	
	
	
	/*------------------------------------------------------------------------*/
	float Cosine(float value); //convert into degrees
	float Sin(float value); // convert into degrees
	float Tan(float value); //convert into degrees
	
	
};

#endif[/php]
[php]#ifndef SURFACE_H
#define SURFACE_H
#include "SDL.h"
class Surface
{
public:
#
	SDL_Surface *surface; /* The surface on which we will load the image/screen */
#
	SDL_Rect offset; /* The target area to load an image */
	const char *path; /* The path of the image */
	
	Surface (int screen_w, int screen_h, int screen_d);
	Surface(const char* path); /* Constructor to load an image (but not apply it!) */
	Surface (const char* Path, SDL_Surface *dest); /* Load an image path, and blit it immediately */
	Surface (const char* Path, SDL_Surface *dest, int x, int y);  /* Load an image and blit it immediately, but also accept the x and y coordinates of where to position it */
	void Apply_Surface (SDL_Surface *dest); /* Applies this->surface to another (programmer defined) */
	void Draw_Background (SDL_Surface* bgimage); /* Draw the background. Only works for a background surface */
	void Load_Optimal (); /* Loads an optimal image to this->surface */
	void SetPos (int x, int y); /* Set the position of the offset (SDL_Rect) */
	void Move (int x, int y, SDL_Surface *dest); /* Move the image */
	
	
};

#endif[/php]
[php]

# include "Surface.h" /* Default SDL header */

Surface::Surface(int screen_w, int screen_h, int screen_d)
{
	SDL_Init (SDL_INIT_EVERYTHING); /* Change SDL_SWSURFACE to SDL_FULLSCREEN to make it fullscreen */
	
	this->surface = SDL_SetVideoMode (screen_w, screen_h, screen_d, SDL_SWSURFACE);
}


Surface::Surface(const char* Path)
{
	
	this->path = Path; /* Assign the file path to Path */
	
	this->Load_Optimal (); /* Load the image, optimal of course! */
}

Surface::Surface(const char* Path, SDL_Surface* dest)
{
	this->path = Path; /* Assign this->path to equal Path (should be self-explanatory, really) */
	
	this->Load_Optimal (); /* Load an optimised image */
	
	this->SetPos (0,0); /* Set the image to be loaded in 0,0 on the screen by default */
	
	this->Apply_Surface (dest); /* Blit and flip the surfaces to make them appear on-screen */
}

Surface::Surface (const char *Path, SDL_Surface *dest, int x, int y)
{
	this->path = Path; /* Self explantory stuff */
	
	this->Load_Optimal (); /* Load an optimised image */
	
	this->SetPos (x,y); /* Set the coordinates to the programmer-defined coordinates */
	
	this->Apply_Surface (dest); /* Blit and flip the surfaces to make them appear on-screen */
}

void Surface::Apply_Surface (SDL_Surface* dest)
{
	SDL_BlitSurface (this->surface, NULL, dest, &this->offset); /* Blit the surfaces */
	
	SDL_Flip (dest); /* Flip the screen (AKA double buffering) */
	
}

void Surface::Draw_Background (SDL_Surface* bgimage)
{
	SDL_Rect temp;
	temp.x = 0;
	temp.y = 0;
	SDL_BlitSurface (bgimage, NULL, this->surface, &temp);
	SDL_Flip(this->surface);
}



void Surface::Load_Optimal () /* Loads an optimal image to this->surface */

{
	
	SDL_Surface *loaded  = NULL; /* The surface to load the basic image */
	
	this->surface = NULL; /* The optimised surface */
	
	loaded = SDL_LoadBMP(this->path); /* Load the basic image */
	
	if (loaded != NULL) /* This is why NULL is important, now we can check if it was loaded successfully */
		
	{
		
		this->surface = SDL_DisplayFormat (loaded); /* Load an optimised version of the basic surface */
		
		SDL_FreeSurface (loaded); /* Delete the basic one, it's no longer needed */
		
	}
	
}

void Surface::SetPos (int x, int y) /* Set the position of the offset (SDL_Rect) */

{
	
	this->offset.x = x; /* Sets the x coordinate of this->offset to equal x (programmer defined) */
	
	this->offset.y = y; /* Sets the y coordinate of this->offset to equal y (programmer defined) */
	
}


void Surface::Move (int x, int y, SDL_Surface* dest) /* Move the image */

{ /* Again, this has to accept the screen as a parameter, due to the call to Apply_Surface () */
	
	this->offset.x += x; /* Add x to the offset */
	
	this->offset.y += y; /* Add y to the offset */
	
	Apply_Surface (dest); /* Update the screen */
	
}[/php]
[php]#include "Object.h"
#include "Surface.h"
#define GROUND 590
Object::Object(const char* file, float mass) : Surface(file)
{
	this->mass = mass;
	this->velocity = 0;
}

SDL_Rect* Object::ApplyForce(float newtons, float angle)
{
	SDL_Rect* acceleration;
	SDL_Rect* tempnewtons;
	
	
	
	tempnewtons->x = (int)(newtons * Cosine(angle)); // Cosine=A/H = H*Cosine=A
	tempnewtons->y = (int)(newtons * Sin(angle)); //Sin=O/H = H*Sin=O
	
	//store the acceleration componenets
	acceleration->x = (int)(this->mass/tempnewtons->x);
	acceleration->y = (int)(this->mass/tempnewtons->y);
	
	return acceleration;
}

void Object::MoveObject(SDL_Rect* accel, SDL_Surface* screen)
{
	//check to see if it is at ground
	if (this->offset.y >= GROUND) 
	{
		
		this->velocity->y = (int)GROUND;
		this->velocity->x += (int)accel->x;
	}
	
	else
	{
		this->velocity->y += (int)(31.6122f);
		this->velocity->x += (int)(800.0/velocity->x);
	}
	this->Move(velocity->x, velocity->y, screen);
	
}[/php]

I know Engine need not be. I had it working differently, with everything inside engine, then decided to change it. I also know there is probably some unnecessary code and/or conversions in there. My excuse is it is 3 in the morning.

---

### Post by dwhitney67 on 2009-02-21
Please recompile/relink your code, then run it using 'gdb'.  It will tell you where the program is seg-faulting.  It would be an immense help if you posted this information.

---

### Post by jacensolo on 2009-02-21
I'm unsure how to do this in Kdevelop. I've googled and couldn't find anything.

---

### Post by dwhitney67 on 2009-02-21
Use the command line by opening a gnome-terminal.  Think of this terminal like a DOS command terminal that is available in Windoze.

You open the terminal, change to the folder where your program resides (using the 'cd' command), compile your application using 'g++', then run using 'gdb'.

Here's an example, which undoubtedly the folder name and the program name differ from yours:
```

cd folder
g++ myprog.cpp -o myprog
gdb myprog

```
Btw, if you cannot debug via Kdevelop (and this is surprising), then you really should dump that IDE and learn to use a terminal, and perhaps vim, for your development needs.  Once you've mastered the use of the terminal, editor, etc then maybe it is safe to return to the IDE.  At least by then you will have a better understanding of the Linux development environment.

---

### Post by jacensolo on 2009-02-21
> **dwhitney67 said:**
> Use the command line by opening a gnome-terminal.  Think of this terminal like a DOS command terminal that is available in Windoze.

You open the terminal, change to the folder where your program resides (using the 'cd' command), compile your application using 'g++', then run using 'gdb'.

Here's an example, which undoubtedly the folder name and the program name differ from yours:
```

cd folder
g++ myprog.cpp -o myprog
gdb myprog

```
Btw, if you cannot debug via Kdevelop (and this is surprising), then you really should dump that IDE and learn to use a terminal, and perhaps vim, for your development needs.  Once you've mastered the use of the terminal, editor, etc then maybe it is safe to return to the IDE.  At least by then you will have a better understanding of the Linux development environment.

I tried that earlier today and I got a cursor next to gdb. I'll try it again after I get back.

BTW, I'm not new to Linux or programming in general. I only have one windows pc and that is for guests. I am, however, new to C++ pointers. I think I somehow am trying to use a NULL pointer.

The only reason I'm using Kdevelop is for auto make. The code completion is a huge plus too :D

---

### Post by Zugzwang on 2009-02-22
In Kdevelop it is even easier to do debugging. Just select "Start" from the debugging menu. It should then run your program (without any parameters on the command line - if you want these, you can set them up in the project preferences). When your program seg-faults, it will even let you inspect the contents of the local variables at the time of seg-faulting.

---

