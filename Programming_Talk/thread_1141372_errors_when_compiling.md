---
title: "errors when compiling"
date: 2009-04-28
forum: Programming Talk
---

### Post by swappo1 on 2009-04-28
Hello,

I get the following errors when I compile my program.
```
scott@scott-laptop:~/SDL_Pong2$ make
g++ -O2 -Wall -Werror -ansi   -c -o main.o main.cpp
In file included from /usr/include/c++/4.2/iostream:44,
                 from main.cpp:2:
/usr/include/c++/4.2/x86_64-linux-gnu/bits/c++config.h:149: error: expected unqualified-id before ‘namespace’
In file included from /usr/include/c++/4.2/cstring:51,
                 from /usr/include/c++/4.2/x86_64-linux-gnu/bits/c++locale.h:47,
                 from /usr/include/c++/4.2/iosfwd:45,
                 from /usr/include/c++/4.2/ios:43,
                 from /usr/include/c++/4.2/ostream:45,
                 from /usr/include/c++/4.2/iostream:45,
                 from main.cpp:2:
/usr/include/c++/4.2/cstddef:53: error: expected unqualified-id before ‘namespace’
In file included from /usr/include/c++/4.2/cstring:52,
                 from /usr/include/c++/4.2/x86_64-linux-gnu/bits/c++locale.h:47,
                 from /usr/include/c++/4.2/iosfwd:45,
                 from /usr/include/c++/4.2/ios:43,
                 from /usr/include/c++/4.2/ostream:45,
                 from /usr/include/c++/4.2/iostream:45,
                 from main.cpp:2:
/usr/include/string.h:28: error: expected unqualified-id before string constant
In file included from /usr/include/c++/4.2/x86_64-linux-gnu/bits/c++io.h:43,
                 from /usr/include/c++/4.2/iosfwd:46,
                 from /usr/include/c++/4.2/ios:43,
                 from /usr/include/c++/4.2/ostream:45,
                 from /usr/include/c++/4.2/iostream:45,
                 from main.cpp:2:
/usr/include/c++/4.2/x86_64-linux-gnu/bits/gthr.h:33: error: expected `}' before end of line
/usr/include/c++/4.2/x86_64-linux-gnu/bits/gthr.h:33: error: expected unqualified-id before end of line
/usr/include/c++/4.2/x86_64-linux-gnu/bits/gthr.h:33: error: expected declaration before end of line
make: *** [main.o] Error 1

```
I am not sure where the error is coming from or even what relevent code to post.  It started when I added game.cpp and game.h.  Any thoughts?

---

### Post by dwhitney67 on 2009-04-28
Please post your main.cpp code.

---

### Post by swappo1 on 2009-04-28
main.cpp
```
#include "game.h"
#include <iostream>

int main(int argc, char** args)
{
	Game game;
	
	game.play();
	
	return 0;
}
```
Here is game.cpp and game.h.  Once I added these two files I started having problems.  Game.cpp isn't finished.  I like to compile things every so often since it makes finding errors easier.
```

game.cpp
#include "game.h"
#include "time.h"
#include <iostream>

Game::Game()
{
}

Game::~Game()
{
}

void Game::play()
{
	bool quit = false;
	
	//seed rand
	srand(time(NULL));
	//initialize class variables
	
	while(!quit)
	{
		while(SDL_PollEvent(&event))
		{
			paddle1.get_input();
			if(event.type == SDL_QUIT || event.key.keysym.sym == SDLK_ESCAPE)
			{
				quit = true;
			}
		}
		display.updateDisplay();
	}
}
game.h
#ifndef GAME_H
#define GAME_H

#include "display.h"


class Game
{
	public:
	Game();				//constructor
	~Game();			//destructor - quit SDL
	void play();		//game loop
	
	private:
	Display display();	//class to handle drawing to the screen
};
#endif

```

---

### Post by dwhitney67 on 2009-04-28
You were only compiling main.cpp, so I am only interested in it, and since it seems ok, now I am interested in seeing game.h, and anything that it may include.

P.S.  When coding in C++, a 'return 0' in the main() function is optional.

---------------

EDIT:  In game.h, is this a function declaration or were you defining a member data object?
```

	Display display();	//class to handle drawing to the screen

```
I'm betting on the latter; thus if I am correct, remove the open/close parenthesis.

---

### Post by swappo1 on 2009-04-28
I removed the open/close parenthesis from Display display() and I get the following:
```

scott@scott-laptop:~/SDL_Pong2$ make
g++ -O2 -Wall -Werror -ansi   -c -o main.o main.cpp
In file included from main.cpp:1:
game.h:15: error: field ‘display’ has incomplete type
In file included from /usr/include/c++/4.2/iostream:44,
                 from main.cpp:2:
/usr/include/c++/4.2/x86_64-linux-gnu/bits/c++config.h:149: error: expected unqualified-id before ‘namespace’
In file included from /usr/include/c++/4.2/cstring:51,
                 from /usr/include/c++/4.2/x86_64-linux-gnu/bits/c++locale.h:47,
                 from /usr/include/c++/4.2/iosfwd:45,
                 from /usr/include/c++/4.2/ios:43,
                 from /usr/include/c++/4.2/ostream:45,
                 from /usr/include/c++/4.2/iostream:45,
                 from main.cpp:2:
/usr/include/c++/4.2/cstddef:53: error: expected unqualified-id before ‘namespace’
In file included from /usr/include/c++/4.2/cstring:52,
                 from /usr/include/c++/4.2/x86_64-linux-gnu/bits/c++locale.h:47,
                 from /usr/include/c++/4.2/iosfwd:45,
                 from /usr/include/c++/4.2/ios:43,
                 from /usr/include/c++/4.2/ostream:45,
                 from /usr/include/c++/4.2/iostream:45,
                 from main.cpp:2:
/usr/include/string.h:28: error: expected unqualified-id before string constant
In file included from /usr/include/c++/4.2/x86_64-linux-gnu/bits/c++io.h:43,
                 from /usr/include/c++/4.2/iosfwd:46,
                 from /usr/include/c++/4.2/ios:43,
                 from /usr/include/c++/4.2/ostream:45,
                 from /usr/include/c++/4.2/iostream:45,
                 from main.cpp:2:
/usr/include/c++/4.2/x86_64-linux-gnu/bits/gthr.h:33: error: expected `}' before end of line
/usr/include/c++/4.2/x86_64-linux-gnu/bits/gthr.h:33: error: expected unqualified-id before end of line
/usr/include/c++/4.2/x86_64-linux-gnu/bits/gthr.h:33: error: expected declaration before end of line
make: *** [main.o] Error 1

```

Here is display.cpp display.h global.h
```

display.cpp
#include "display.h"
#include "global.h"
#include <stdexcept>
#include <SDL/SDL.h>
#include <SDL/SDL_image.h>

Display::Display()
{
	if(SDL_Init(SDL_INIT_VIDEO) == -1)
	{
		throw std::runtime_error("Could not initialize video.");
	}
	//set screen
	screen = SDL_SetVideoMode(SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE);
	if(!screen)
	{
		throw std::runtime_error("Could not set screen.");
	}
	//add caption to window
	SDL_WM_SetCaption("Pongclone", "Pongclone");
	
	background = loadedImage("background.png");
	ball = loadedImage("ball.png");
	paddle = loadedImage("paddle.png");
}

Display::~Display()
{
	SDL_FreeSurface(background);
	SDL_FreeSurface(ball);
	SDL_FreeSurface(paddle);
}

void Display::updateBall(int x, int y)
{
	updateSurface(int x, int y, ball, screen);
}
	
void Display::updateDisplay()
{
	updateSurface(0, 0, background, screen);
	SDL_Flip(screen);
}
	
void updateSurface(int x, int y, SDL_Surface* source, SDL_Surface* destination)
{
	SDL_Rect offset;
	
	offset.x = x;
	offset.y = y;
	
	SDL_BlitSurface(source, NULL, destination, &offset);
}

SDL_Surface* Display::load_image(const char *filename);		//load the image
{
	//The image that's loaded
	SDL_Surface* loadedImage = IMG_Load(filename);

	//If the image loaded
	if(!loadedImage)
	{
		throw std::runtime_error((std::string("Could not load image from ") + filename).c_str());
	}
	
	//Create an optimized surface
	SDL_Surface* optimizedImage = SDL_DisplayFormat( loadedImage );
	//Free the old surface
	SDL_FreeSurface( loadedImage );
	if(!optimizedImage)
	{
		throw std::runtime_error((std::string("Could not optimize image from ") + filename).c_str());
	}
	//map the colorkey to the transparent background of the sprite
	Uint32 colorkey = SDL_MapRGB(optimizedImage->format, 0xff, 0xff, 0xff); 
            
	//Set all colors of the background to be transparent
	SDL_SetColorKey(optimizedImage, SDL_SRCCOLORKEY, colorkey);

	//Return the optimized surface
	return optimizedImage;
}

display.h
#ifndef DISPLAY_H
#define DISPLAY_H

class SDL_Surface;

class Display
{
	public:
		Display();		//constuctor -- initialize SDL
		
		~Display();		//destructor -- free SDL_Surface
		
		void updateBall(int x, int y);	//update the surface with ball
		void updateDisplay();		//update the display with background

	private:
		void updateSurface(int x, int y, SDL_Surface* source, SDL_Surface* destination);	//apply surface

		SDL_Surface* load_image(const char *filename);		//load the image
		
		//Set the screen
		SDL_Surface *screen;
		//set the background
		SDL_Surface *background;
		//set the ball
		SDL_Surface *ball;
		//set the paddle
		SDL_Surface *paddle;
		
#endif

global.h
#ifndef GLOBAL_H
#define GLOBAL_H

static const int SCREEN_WIDTH = 800;
static const int SCREEN_HEIGHT = 600;

//32 bits per pixel
static const int SCREEN_BPP = 32;

//width of the ball
static const int BALL_WIDTH = 20;
static const int BALL_HEIGHT = 20;

//width of the paddle
static const int PADDLE_WIDTH = 10;
static const int PADDLE_HEIGHT = 60;

#endif

```

---

### Post by dwhitney67 on 2009-04-28
Check your display.h; from what you posted, it appears incomplete.  It's missing the closing } bracket and semi-colon (before the #endif).

Otherwise, everything else you posted compiles fine.

---

### Post by swappo1 on 2009-04-28
Thanks for picking that up.  I only looked at it a dozen times.  I guess it helps to have a fresh pair of eyes.

---

