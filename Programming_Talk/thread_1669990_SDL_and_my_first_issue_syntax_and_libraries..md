---
title: "SDL and my first issue syntax and libraries."
date: 2011-01-18
forum: Programming Talk
---

### Post by Ravenshade on 2011-01-18
Hi, I'm using the G++ compiler with -lSDL and -lSDL_image libraries. 

I'm using lazy foo's tutorials and I wrote this out line for line, or so I thought. Yet lazy foo's downloaded source compiles successfully and runs as depicted. 

The image is simply just a message, nothing in particular importance. 

However, when I run my source...below. I get a segmentation fault. Yet I can't see any difference. What am I missing? 

[http://lazyfoo.net/SDL_tutorials/lesson04/index.php](http://lazyfoo.net/SDL_tutorials/lesson04/index.php)

Thus far I've...

Gone line by line, checked and rechecked for spelling errors, incorrect syntax. Nothing found. 

I've copied and pasted from the source code into the file replacing everything there...compiled successfully. However, upon trying old code, still doesn't compile. 

Tried compiling multiple times...perhaps a G++ error? Not a fluke, it's a consistent issue. 

I can compile the tutorial otherwise okay. 

I'm wondering if it really matters about whitespace. I don't appear to have gaps in odd places but still...


```

//Headers
#include "SDL/SDL.h"
#include "SDL/SDL_image.h"
#include <string> //just to use std::string

//screenSetup
const int SCREEN_WIDTH = 640;
const int SCREEN_HEIGHT = 480;
const int SCREEN_BPP = 32;

//Load the surfaces or layers
SDL_Surface *image = NULL;
SDL_Surface *screen = NULL;

//The Event structure that will be used...
SDL_Event event;

SDL_Surface *load_image( std::string filename )
{
	//The Image that's loaded
	SDL_Surface* loadedImage = NULL;
	
	//Optimized image to use...
	SDL_Surface* optimizedImage = NULL;
	
	//load the image
	loadedImage = IMG_Load( filename.c_str() );
	
	//Error check. Has image been loaded?
	if( loadedImage != NULL)
	{
		//create image
		optimizedImage = SDL_DisplayFormat( loadedImage );
		
		//free up the old image
		SDL_FreeSurface( loadedImage );
	}
	
	return optimizedImage;
}

void apply_surface( int x, int y, SDL_Surface* source, SDL_Surface* destination )
{
	//Declare temp rectangle to hold the offsets
	SDL_Rect offset;
	
	//Get the offsets
	offset.x = x;
	offset.y = y;
	
	//Blit the surface
	SDL_BlitSurface( source, NULL, destination, &offset );
}

bool init()
{
	//Initialize the subsystems
	if( SDL_Init( SDL_INIT_EVERYTHING ) == -1 )
	{
		return false;
	}
	
	//set up the screen
	screen = SDL_SetVideoMode( SCREEN_WIDTH, SCREEN_HEIGHT, SCREEN_BPP, SDL_SWSURFACE );
	
	//If there was an error...
	if( screen = NULL )
	{
		return false;
	}
	
	//Set the caption window
	SDL_WM_SetCaption( "Testing events!", NULL );
	
	//If everything is good then run...
	return true;	
		
}

bool load_files()
{
	//Load teh image
	image = load_image( "x.png" );
	
	//If there was an error return false
	if( image == NULL )
	{
		return false;
	}
	
	//else...
	return true;
}

void clean_up()
{
	//Free image...
	SDL_FreeSurface( image );
	
	//Quit SDL
	SDL_Quit();
}

int main( int argc, char* args[] )
{
	//make sure program waits for quit...
	bool quit = false;
	
	//Initialise
	if( init() == false)
	{
		return 1;
	}
	
	//Load the files
	if( load_files() == false )
	{
		return 1;
	}
	
	//Apply the surface to the screen
	apply_surface( 0, 0, image, screen );
	
	//update...
	if( SDL_Flip( screen ) == -1 )
	{
		return 1;
	}
	
	//While the user hasn't quit...
	while( quit == false )
	{
		//While there's an event to handle...
		while( SDL_PollEvent( &event ) )
		{
			//if the user has x'ed out of the window...
			if( event.type == SDL_QUIT )
			{
				//quit the program...which quits the loop...
				quit = true;
			}
		}
	}
	
	clean_up();
	
	return 0;
}

```

---

### Post by Arndt on 2011-01-18
[duplicate]

---

### Post by Arndt on 2011-01-18
> **Ravenshade said:**
> Hi, I'm using the G++ compiler with -lSDL and -lSDL_image libraries. 

I'm using lazy foo's tutorials and I wrote this out line for line, or so I thought. Yet lazy foo's downloaded source compiles successfully and runs as depicted. 

The image is simply just a message, nothing in particular importance. 

However, when I run my source...below. I get a segmentation fault. Yet I can't see any difference. What am I missing? 



Some information is missing here. Are you saying that you can download the code, compile and run it, whereas your code gives segmentation fault, although it is identical to the downloaded one?

---

### Post by Simian Man on 2011-01-18
I can see your problem right now, but instead of just telling you, I will show you how you can figure stuff like this out yourself in the future.  What we're going to do is run your program through the debugger.

To start with, we need to compile the program with debugging turned on.  To do this you pass "-g" to g++:
```

g++ **-g** temp.cpp -lSDL -lSDL_image -o temp

```

This allows you to run the gdb or ddd debuggers to see what's going on with your code:
```

**gdb temp**

```

This gives you a screen that looks like this:
```

GNU gdb (GDB) Fedora (7.2-26.fc14)
Copyright (C) 2010 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-redhat-linux-gnu".
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>...
Reading symbols from /home/ian/Projects/temp/temp...done.
(gdb)

```
The (gdb) is a command prompt.  Gdb has a ton of commands, but we only need a few to figure this out.  First we type "run" to run the program through the debugger.  If your program had no bugs, it would run just like normal, but a bit slower.  Since it does have bugs, however, this happens:
```

(gdb) **run**
Starting program: /home/ian/Projects/temp/a.out 
[Thread debugging using libthread_db enabled]
[New Thread 0x7fffee064700 (LWP 3143)]
[Thread 0x7fffee064700 (LWP 3143) exited]
[New Thread 0x7fffee064700 (LWP 3144)]

Program received signal SIGSEGV, Segmentation fault.
0x00000035f202ee68 in SDL_Flip () from /usr/lib64/libSDL-1.2.so.0
(gdb) 

```
It tells you that the program got a segfault, which you already knew, but it also tells you that the segfault was in SDL_Flip.  To see more info, type:
```

(gdb) **backtrace**
#0  0x00000035f202ee68 in SDL_Flip () from /usr/lib64/libSDL-1.2.so.0
#1  0x0000000000400e2f in main (argc=1, args=0x7fffffffdf78) at temp.cpp:125

```
backtrace or "bt" for short gives you the trace of functions that caused the error in addition to the line numbers of each call.  We can see the problem is the SDL_Flip call on line 125.  This seems to indicate that the screen is messed up and we can test that with:
```

(gdb) **print screen**
$2 = (SDL_Surface *) 0x0

```
The print command ("p" for short) prints the type and value of any variable and, as you can see, the screen is NULL.

Now you may be able to see what the problem is already, but we'll keep debugging.  In order to see when the value of a variable changes, we use the watch command.  We also have to run the program again since we already crashed.  To do that, just type run again and say "y" to start at the beginning:
```

(gdb) **watch screen**
Hardware watchpoint 1: screen
(gdb) **run**
The program being debugged has been started already.
Start it from the beginning? (y or n) **y**
Starting program: /home/ian/Projects/temp/temp
[Thread debugging using libthread_db enabled]
[New Thread 0x7fffee064700 (LWP 3233)]
[Thread 0x7fffee064700 (LWP 3233) exited]
[New Thread 0x7fffee064700 (LWP 3234)]
Hardware watchpoint 1: screen

Old value = (SDL_Surface *) 0x0
New value = (SDL_Surface *) 0x663220
init () at temp.cpp:67
67        if( screen = NULL )
(gdb) 

```

Now instead of stopping when the program crashed, it stops when the screen variable is changed.  Here we can see that the value changed from 0 (NULL), to 0x663220 which is a good-looking pointer from SDL_SetVideoMode.  Your exact number will probably be different.  Since everything looks OK, we type "continue" or "c" for short:
```

(gdb) **continue**
Continuing.
Hardware watchpoint 1: screen

Old value = (SDL_Surface *) 0x663220
New value = (SDL_Surface *) 0x0
0x0000000000400cda in init () at temp.cpp:67
67        if( screen = NULL )
(gdb)

```
Gdb has stopped again because the value of screen has been changed again.  This time the value has gone from 0x663220 back to NULL!  This is our problem and gdb has given us a nearby line which has the problem.  (This line also appeared in the last watchpoint, but that was just because it happened to be nearby.)

Your problem was that you have "if( screen = NULL )" instead of "if( screen **==** NULL )".  The single equal sign is assignment and the double equal sign is test for equality.  So your code is assigning NULL to screen right after you create it.

Since we have our answer quit gdb with:
```

(gdb) **quit**
A debugging session is active.

        Inferior 1 [process 3232] will be killed.

Quit anyway? (y or n) **y**
[ian@splinter]$ 

```

With this change the code runs just fine.  In the future, you should get in the habit of compiling your code with warnings turned on:
```

g++ -g **-Wall** temp.cpp -lSDL -lSDL_image -o temp 
temp.cpp: In function ‘bool init()’:
temp.cpp:67:21: warning: suggest parentheses around assignment used as truth value

```
As you can see, with the "-Wall" flag, g++ will tell you about the problem.  It's not the clearest warning, but it does highlight the problem.

Hope all that made sense :)

---

### Post by nvteighen on 2011-01-19
This also teaches another lesson: the whole debugging process becomes slightly more complex because you're using global variables. If you had used local variables and passed them to functions, as soon as you knew that the segfault was related to a function call using the screen variable, you could have reduced your search just to those functions that accepted that variable as a parameter. Instead, by using global variables, you had to check the whole code.

---

### Post by Ravenshade on 2011-01-19
> **nvteighen said:**
> This also teaches another lesson: the whole debugging process becomes slightly more complex because you're using global variables. If you had used local variables and passed them to functions, as soon as you knew that the segfault was related to a function call using the screen variable, you could have reduced your search just to those functions that accepted that variable as a parameter. Instead, by using global variables, you had to check the whole code.

I have no choice with the global and local variables at the moment, this is how the tutorial is laid out and I'm just following it. I'll send a message to the tutorial creator. 

@Simianman. Thank you very much for your help...who knew debugging would be so complex... >.< I had assumed there was something wrong with my code, never thought it'd be because I used an assignment instead of a logical equals.

---

### Post by unknownPoster on 2011-01-19
> **Ravenshade said:**
> 

@Simianman. Thank you very much for your help...who knew debugging would be so complex... >.< I had assumed there was something wrong with my code, never thought it'd be because I used an assignment instead of a logical equals.

gdb is a good base to start at in my opinion. However, if you use any of the OOP features of C++ or dynamic memory management you'll eventually want to familiarize yourself with Valgrind, which checks for memory leaks.

---

