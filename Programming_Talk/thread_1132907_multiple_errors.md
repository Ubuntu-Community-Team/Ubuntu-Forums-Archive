---
title: "multiple errors"
date: 2009-04-22
forum: Programming Talk
---

### Post by swappo1 on 2009-04-22
Hello,

I am in the process of converting my unfinished pong program from a single file into multiple files using a Makefile.  I get the following errors and can't figure out where they are coming from.
```
scott@scott-laptop:~/SDL_Pong$ make
g++ -O2 -Wall -Werror -ansi   -c -o main.o main.cpp
g++ -O2 -Wall -Werror -ansi   -c -o global.o global.cpp
g++ -O2 -Wall -Werror -ansi   -c -o display.o display.cpp
g++ -O2 -Wall -Werror -ansi   -c -o ball.o ball.cpp
ball.cpp: In member function ‘void Ball::show()’:
ball.cpp:67: error: ‘screen’ was not declared in this scope
ball.cpp:67: error: ‘display_apply_surface’ was not declared in this scope
ball.cpp: In member function ‘void Ball::show_background()’:
ball.cpp:73: error: ‘background’ was not declared in this scope
ball.cpp:73: error: ‘screen’ was not declared in this scope
ball.cpp:73: error: ‘display_apply_surface’ was not declared in this scope
make: *** [ball.o] Error 1

```
Here is ball.cpp
```
//Pongclone

//ball class

#include <SDL/SDL.h>
#include "ball.h"
#include "global.h"
#include "display.h"
#include "stdlib.h"

//Constructor - initialize variables
Ball::Ball()
{
	//Initialize the offsets

    ball.x = (SCREEN_WIDTH - BALL_WIDTH) / 2;

    ball.y = (SCREEN_HEIGHT - BALL_HEIGHT) / 2;
    //initialize the dimensions
    ball.w = BALL_WIDTH;
    ball.h = BALL_HEIGHT;



    //Initialize the velocity

    xVel = 0;

    yVel = 0;
    
    need_reset = true;
}

void Ball::update()
{	
	
	if(need_reset)
	{
		x = (SCREEN_WIDTH - BALL_WIDTH) / 2;
		y = (SCREEN_HEIGHT - BALL_HEIGHT) / 2;
		
		switch(rand() % 4)
		{
			
			case 0: xVel = 10; yVel = 10; break;
			case 1: xVel = -10; yVel = 10; break;
			case 2: xVel = 10; yVel = -10; break;
			case 3: xVel = -10; yVel = -10; break;
		}
	need_reset = false;
	}
	
	move();
}

void Ball::move()
{
	x += xVel;
	y += yVel;
	

    if(x >= (SCREEN_WIDTH - BALL_WIDTH) || x <= 0)
    {
    	need_reset = true;
    }
    if(y >= (SCREEN_HEIGHT - BALL_WIDTH) || y <= 0)
    {
    	yVel = yVel * -1;
    }
}

void Ball::show()
{
	display_apply_surface(x, y, ball, screen);
}

void Ball::show_background()
{
	//show the background
	display_apply_surface(0, 0, background, screen);
}
```
ball.h
```
//Pongclone

//ball class

#ifndef DISPLAY_H
#define DISPLAY_H

#include <SDL/SDL.h>

class Ball
{
	protected:
	//x and y offsets of the ball
	int x, y;
	//x and y velocities of the ball
	int xVel, yVel;
	//toggle's reset of the ball on and off
	bool need_reset;
	//the collision box of the ball
	SDL_Rect ball;
	
	public:

    //Initializes the variables

    Ball();



    //Moves the ball

    void move();



    //Shows the ball on the screen

    void show();
    //show the background
    void show_background();
    // Start/reset the ball
    void update();
};

#endif
```
display.cpp
```
//Pongclone
//Display file

#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include "display.h"
#include "global.h"
#include "ball.h"

//Set the screen
SDL_Surface *screen = NULL;
//set the background
SDL_Surface *background = NULL;
//set the ball
SDL_Surface *ball = NULL;
//set the paddle
SDL_Surface *paddle = NULL;

//initialize screen
bool display_init()
{
	if(SDL_Init(SDL_INIT_VIDEO) == -1)
	{
		return false;
	}
	//set screen
	screen = SDL_SetVideoMode(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE);
	if(screen == NULL)
	{
		return false;
	}
	//add caption to window
	SDL_WM_SetCaption("Pongclone", "Pongclone");
	
	return true;
}
//load the imagage
SDL_Surface *load_image(const char *filename)
{
	//The image that's loaded
	SDL_Surface* loadedImage = NULL;

	//The optimized surface that will be used
	SDL_Surface* optimizedImage = NULL;

	//Load the image
	loadedImage = IMG_Load(filename);

	//If the image loaded
	if( loadedImage != NULL )
	{
		//Create an optimized surface
		optimizedImage = SDL_DisplayFormat( loadedImage );

		//Free the old surface
		SDL_FreeSurface( loadedImage );

		//If the surface was optimized
		if( optimizedImage != NULL )
		{
			//map the colorkey to the transparent background of the sprite
			Uint32 colorkey = SDL_MapRGB(optimizedImage->format, 0xff, 0xff, 0xff); 
            
			//Set all colors of the background to be transparent
			SDL_SetColorKey(optimizedImage, SDL_SRCCOLORKEY, colorkey);
		}
	}

	//Return the optimized surface
	return optimizedImage;
}
//load files to be displayed
bool display_load_files()
{	//background image
	background = load_image("SDL_background.png");
	paddle = load_image("pong_paddle.png");
	ball = load_image("pong_ball.png");
	
	if(background == NULL)
		{
		return false;
		}
	return true;
}
//blit an image on the screen
void display_apply_surface(int x, int y, SDL_Surface* source, SDL_Surface* destination)
{
	SDL_Rect offset;
	
	offset.x = x;
	offset.y = y;
	
	SDL_BlitSurface(source, NULL, destination, &offset);
}
//Free surfaces and quit

//Update the display
int display_update()
{
	display_apply_surface(0, 0, background, screen);
	
	if(SDL_Flip(screen) == -1)
		{
			return 1;
		}
	return 0;
}

void clean_up()
{
	SDL_FreeSurface(background);
	
	SDL_Quit();
}
```
This is my first Makefile.  Any ideas?

---

### Post by Zugzwang on 2009-04-22
> **swappo1 said:**
> 
This is my first Makefile.  Any ideas?

Yes. You did not declare "screen" and so on. It looks like you have some header file like "globals.h". It should contain something like:
```

extern SDL_Surface *screen;
//set the background
extern SDL_Surface *background;
//set the ball
extern SDL_Surface *ball;
//set the paddle
extern SDL_Surface *paddle;

```

to declare these variables globally. The definition of these can stay where it is.

---

### Post by swappo1 on 2009-04-22
I have them declared in globals.cpp.
```
//Pongclone
//Globals source
//defines all global constants
//if global constants need to be changed,
//only this file will need to be recompiled

#include "global.h"
#include "ball.h"
#include "display.h"

//screen size in pixels
const int SCREEN_WIDTH = 800;
const int SCREEN_HEIGHT = 600;

//32 bits per pixel
const int SCREEN_BPP = 32;

//width of the ball
const int BALL_WIDTH = 20;
const int BALL_HEIGHT = 20;

//width of the paddle
const int PADDLE_WIDTH = 10;
const int PADDLE_HEIGHT = 60;
```
globals.h
```
//Pongclone

//Global header

#ifndef GLOBAL_H
#define GLOBAL_H

//screen size in pixels
extern const int SCREEN_WIDTH;
extern const int SCREEN_HEIGHT;

//32 bits per pixel
extern const int SCREEN_BPP;

//width of the ball
extern const int BALL_WIDTH;
extern const int BALL_HEIGHT;

//width of the paddle
extern const int PADDLE_WIDTH;
extern const int PADDLE_HEIGHT;

#endif
```

---

### Post by Zugzwang on 2009-04-22
> **swappo1 said:**
> I have them declared in globals.cpp.

No, you haven't. First of all, you *declared* stuff in globals.h and *defined* stuff in globals.cpp. Don't mix that! Furthermore you only declare some integer constants in the .h file but not the variables the compiler complains about. For example, try searching for "display_apply_surface" in your .h files. You won't find it. See what I mean?

---

### Post by swappo1 on 2009-04-22
I tried posting what I thought was relevant to the problem since I didn't want to overwhelm everyone with too much information.  Here is the rest of the files.
display.cpp
```
//Pongclone
//Display file

#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include "display.h"
#include "global.h"
#include "ball.h"

//Set the screen
SDL_Surface *screen = NULL;
//set the background
SDL_Surface *background = NULL;
//set the ball
SDL_Surface *ball = NULL;
//set the paddle
SDL_Surface *paddle = NULL;

//initialize screen
bool display_init()
{
	if(SDL_Init(SDL_INIT_VIDEO) == -1)
	{
		return false;
	}
	//set screen
	screen = SDL_SetVideoMode(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE);
	if(screen == NULL)
	{
		return false;
	}
	//add caption to window
	SDL_WM_SetCaption("Pongclone", "Pongclone");
	
	return true;
}
//load the imagage
SDL_Surface *load_image(const char *filename)
{
	//The image that's loaded
	SDL_Surface* loadedImage = NULL;

	//The optimized surface that will be used
	SDL_Surface* optimizedImage = NULL;

	//Load the image
	loadedImage = IMG_Load(filename);

	//If the image loaded
	if( loadedImage != NULL )
	{
		//Create an optimized surface
		optimizedImage = SDL_DisplayFormat( loadedImage );

		//Free the old surface
		SDL_FreeSurface( loadedImage );

		//If the surface was optimized
		if( optimizedImage != NULL )
		{
			//map the colorkey to the transparent background of the sprite
			Uint32 colorkey = SDL_MapRGB(optimizedImage->format, 0xff, 0xff, 0xff); 
            
			//Set all colors of the background to be transparent
			SDL_SetColorKey(optimizedImage, SDL_SRCCOLORKEY, colorkey);
		}
	}

	//Return the optimized surface
	return optimizedImage;
}
//load files to be displayed
bool display_load_files()
{	//background image
	background = load_image("SDL_background.png");
	paddle = load_image("pong_paddle.png");
	ball = load_image("pong_ball.png");
	
	if(background == NULL)
		{
		return false;
		}
	return true;
}
//blit an image on the screen
void display_apply_surface(int x, int y, SDL_Surface* source, SDL_Surface* destination)
{
	SDL_Rect offset;
	
	offset.x = x;
	offset.y = y;
	
	SDL_BlitSurface(source, NULL, destination, &offset);
}
//Free surfaces and quit

//Update the display
int display_update()
{
	display_apply_surface(0, 0, background, screen);
	
	if(SDL_Flip(screen) == -1)
		{
			return 1;
		}
	return 0;
}

void clean_up()
{
	SDL_FreeSurface(background);
	
	SDL_Quit();
}
```
display.h
```
//Pongclone

//display header

#ifndef DISPLAY_H
#define DISPLAY_H

#include <SDL/SDL.h>

//init display
bool display_init();

//load the image
SDL_Surface *load_image(const char *filename); //must use const char or will get
												//warning: deprecated conversion from
//load the files to be displayed				//string constant to 'char*'
bool display_load_files();

//blit an image on the screen
void display_apply_surface(int x, int y, SDL_Surface* source, SDL_Surface* destination);

//Update the display
int display_update();

//Free surfaces and quit
void clean_up();

#endif
```
Makefile
```
CXXFLAGS = -O2 -Wall -Werror -ansi
LDLIBS = -lSDL_image -lpthread
INCLUDE = .
PROG = Pongclone
NAME = Pongclone
SRCS = main.cpp	global.cpp display.cpp ball.cpp
OBJS = main.o global.o display.o ball.o

$(PROG): $(OBJS)
		$(CXX) -o $(PROG) $(OBJS) $(LDLIBS)
		#mv $(PROG) ..

# How to make the object files:

-include deps.mak

deps:
		$(CXX) -MM $(SRCS) > deps.mak

# Cleaning target (only works with fileutils):

clean:
		$(RM) $(OBJS) $(PROG)


```
main.cpp
```
#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include <iostream>
#include "global.h"
#include "display.h"
#include "ball.h"
#include "time.h"

using namespace std;

SDL_Event event;

int main(int argc, char* args[])
{
	bool quit = false;
	
	//seed rand
	srand(time(NULL));
	//initialize class variables
	
	//Initialize SDL
	if(display_init() == false)
	{
		cout << "SDL failed to initialize" << endl;
		return 1;
	}
	//load files
	if(display_load_files() == false)
	{
		cout << "couldn't load the files" << endl;
		return 1;
	}
	
	//key events
	while(quit == false)
	{
		while(SDL_PollEvent(&event))
		{
			if(event.type == SDL_QUIT || event.key.keysym.sym == SDLK_ESCAPE)
			{
				quit = true;
			}
			else
			{
				quit = false;
			}
		}
		display_update();	//display ball, paddle1 & paddle2
	}

	
	clean_up();	//display.cpp

	return 0;
}
```
> First of all, you *declared* stuff in globals.h and *defined* stuff in globals.cpp. Don't mix that!
I am following another program as an example.  This is how the other program does it.  Can I just use one file global.h and declare my variables there?  Thanks for the help.

---

### Post by Zugzwang on 2009-04-22
> **swappo1 said:**
> Can I just use one file global.h and declare my variables there?  Thanks for the help.

Yes. It does not make a difference where you declare your stuff (of course, for big projects, it is good practice to break up all the declarations into usable pieces).

---

### Post by swappo1 on 2009-04-22
I put the following in global.h.
```
//Set the screen
extern SDL_Surface *screen;
//set the background
extern SDL_Surface *background;
//set the ball
extern SDL_Surface *ball;
//set the paddle
extern SDL_Surface *paddle;
```
Here is the errors I am getting.  I am not sure what this means.
```
g++ -O2 -Wall -Werror -ansi   -c -o global.o global.cpp
In file included from global.cpp:7:
global.h:24: error: expected initializer before ‘*’ token
global.h:26: error: expected initializer before ‘*’ token
global.h:28: error: expected initializer before ‘*’ token
global.h:30: error: expected initializer before ‘*’ token
make: *** [global.o] Error 1

```
One thing I am confused on, is why I can't initialize my variables in global.ccp.  If I declare them in global.h and I want to set them to some value, wouldn't it make sense to put all of them in one file?  Unless I can define and declare them at the same time in global.h?  
Example: extern const int BALL_WIDTH = 20;
This would go in global.h.

---

### Post by dwhitney67 on 2009-04-22
Just a thought for you to consider...


Game.h:
```

#ifndef GAME_H
#define GAME_H

#include <SDL/SDL.h>

class Game
{
  public:
    Game();

    void init();

    void start();
    void stop();
    void pause();

    // etc...

  private:
    SDL_Surface* screen;
    SDL_Surface* background;
    SDL_Surface* ball;
    SDL_Surface* paddle;
};

#endif

```

---

### Post by swappo1 on 2009-04-22
I changed my global.cpp and global.h files to just one global1.h.  Is this correct?
```
//Pongclone

//Global header

#ifndef GLOBAL_H
#define GLOBAL_H

//screen size in pixels
extern const int SCREEN_WIDTH = 800;
extern const int SCREEN_HEIGHT = 600;

//32 bits per pixel
extern const int SCREEN_BPP = 32;

//width of the ball
extern const int BALL_WIDTH = 20;
extern const int BALL_HEIGHT = 20;

//width of the paddle
extern const int PADDLE_WIDTH = 10;
extern const int PADDLE_HEIGHT = 60;

//Set the screen
extern SDL_Surface *screen;
//set the background
extern SDL_Surface *background;
//set the ball
extern SDL_Surface *ball;
//set the paddle
extern SDL_Surface *paddle;

#endif
```
Now I get the following:
```
g++ -O2 -Wall -Werror -ansi   -c -o main.o main.cpp
g++ -O2 -Wall -Werror -ansi   -c -o display.o display.cpp
g++ -O2 -Wall -Werror -ansi   -c -o ball.o ball.cpp
ball.cpp: In member function ‘void Ball::show()’:
ball.cpp:67: error: ‘display_apply_surface’ was not declared in this scope
ball.cpp: In member function ‘void Ball::show_background()’:
ball.cpp:73: error: ‘display_apply_surface’ was not declared in this scope
make: *** [ball.o] Error 1

```
since display_apply_surface is in display.cpp and display.h and display.h is defined in ball.cpp, shouldn't the compiler see these functions?

---

### Post by dwhitney67 on 2009-04-22
> **swappo1 said:**
> I changed my global.cpp and global.h files to just one global1.h.  Is this correct?
```
//Pongclone

//Global header

#ifndef GLOBAL_H
#define GLOBAL_H

//screen size in pixels
extern const int SCREEN_WIDTH = 800;
extern const int SCREEN_HEIGHT = 600;

//32 bits per pixel
extern const int SCREEN_BPP = 32;

//width of the ball
extern const int BALL_WIDTH = 20;
extern const int BALL_HEIGHT = 20;

//width of the paddle
extern const int PADDLE_WIDTH = 10;
extern const int PADDLE_HEIGHT = 60;

//Set the screen
extern SDL_Surface *screen;
//set the background
extern SDL_Surface *background;
//set the ball
extern SDL_Surface *ball;
//set the paddle
extern SDL_Surface *paddle;

#endif
```
Now I get the following:
```
g++ -O2 -Wall -Werror -ansi   -c -o main.o main.cpp
g++ -O2 -Wall -Werror -ansi   -c -o display.o display.cpp
g++ -O2 -Wall -Werror -ansi   -c -o ball.o ball.cpp
ball.cpp: In member function ‘void Ball::show()’:
ball.cpp:67: error: ‘display_apply_surface’ was not declared in this scope
ball.cpp: In member function ‘void Ball::show_background()’:
ball.cpp:73: error: ‘display_apply_surface’ was not declared in this scope
make: *** [ball.o] Error 1

```
since display_apply_surface is in display.cpp and display.h and display.h is defined in ball.cpp, shouldn't the compiler see these functions?

Encapsulate your variables into a class, rather than make them global.  The more effort you place into encapsulating your objects (variables) and methods into classes, the less hassle you will have when it comes times to build the application.

If you insist on remaining with your approach, define methods and variables in the header file.  You should not initialize a variable in a header file (unless it is declared as a const).

The errors in ball.cpp are produced because you have not defined those particular functions in a header file.  They should be in a class, or at a minimum, in a namespace.  Stop programming as if you were developing a C application.

P.S.  I do not believe the 'extern' is needed for 'const' values.

---

### Post by dwhitney67 on 2009-04-22
swappo1 -

Take a look at the attached tar-ball of (ping) pong code which I derived from yours; see if you can use it.  Additional code will need to be added; this includes:

- Handling paddle movement
- Score keeping

The code is organized as follows:

main() instantiates a PingPong object.  It uses this to play the game (i.e. this is the "controller").

The PingPong object contains a Display object (which defines the various surfaces), a Ball object (which defines the movement of the ball), and two Paddle objects (for controlling the positioning of the paddles).

The Display object is the "view" which manages the surfaces, and basically all drawing.

The Ball and Paddle classes use this Display object, for obvious reasons.

The class object, which I have not provided, is Score (or whatever you wish to call it).  It is the "model" that keeps the game state, which in the case of Pong, is merely the score.  It provides feedback to the controller when the game is over, and of course, who won.

P.S.  MVC = Model-Viewer-Controller.

---

### Post by swappo1 on 2009-04-23
dwhitney67,

Thanks, your posts are coming in very handy.  I saw your first post yesterday, as I was getting ready for work and needed time to think about it.  Your ping pong file definately helped expand upon it.  It seems like creating an object to handle display, ball ,paddles... is the way to go.  

My plan is to create a game object.  This object will handle the game loop and will have the other objects(ball, paddles, display...) as private variables. So basically, everything will work through the game object. Is this correct?  Thanks

---

### Post by dwhitney67 on 2009-04-23
> **swappo1 said:**
> ...
So basically, everything will work through the game object. Is this correct?  Thanks

Yes, that is the gist of it.  What I provided is by no means a completed program, nor has it been critically acclaimed to be worth more than a grain of salt.  But hopefully it will assist you with the notion that global variables are unnecessary, and that object should be encapsulated into classes that use them.

Btw, wrt the Ball and Paddle classes, these probably should not have a notion of the Display object; I was lazy and provided them with a reference of that object which was created by the main game object (PingPong).  The Ball and Paddle should provide methods that allow PingPong to query their state (i.e. x and y positions).

Also, the positioning of the Paddle is probably completely wrong, but it is just a matter of setting the x and y positions.  I merely through something together.

I had no hopes of visualizing my work because I did not have the "png" files.

---

