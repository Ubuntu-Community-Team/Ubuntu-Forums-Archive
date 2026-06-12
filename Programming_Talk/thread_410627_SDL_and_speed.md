---
title: "SDL and speed"
date: 2007-04-16
forum: Programming Talk
---

### Post by tht00 on 2007-04-16
Ok.  I'm looking at doing some hobbyist game programming, and I'm looking at starting with porting an asteroids game of mine from VB.

So, I've been looking at SDL, and it looks promising.  However, I'm hitting a few snags with just getting up and running.

I've got a very basic C++ program that initiates SDL, uses the SDL_gfx library ( [http://www.ferzkopp.net/joomla/content/view/19/14/](http://www.ferzkopp.net/joomla/content/view/19/14/) ), and draws a moving triangle (clear surface, move coords, draw 3 lines, update to screen, repeat).  Now, the problem is with the speed of execution.  It isn't horribly slow, but I do want to be able to boost the resolution up a bit, and as the resolution increases, the FPS drops. 

At 800x600, it sits at around 24 frames per second, which isn't horrible, but at the same time, I picked C++ for speed.  Potentially, I'm going to be doing a lot of crunching with this program, and I don't need the CPU working overtime just to keep up on mediocre frame rates.

So, are there any 'quick fixes'?  I'm guessing not, but I figured I'd ask.  I could go ahead and go with SDL + OpenGL, but that seems like overkill, and I'm not sure that there's a decent (or even existent) primitives library for that.  For now, I'm wanting to keep it strictly with primitives (lines, circles), and I can do that through the added SDL_gfx.

Options?  Cut the resolution?  Go OpenGL?  Anything else?  What about primitives?

Thanks,
Tom

---

### Post by loicp on 2007-04-16
Hello,

Can you show us the source code ?

---

### Post by IronAvatar on 2007-04-16
Are you using the default drivers for your video card?  You shouldn't see such huge drops in performance when rendering one triangle, unless you're using software rendering  instead of direct rendering via the native drivers.

---

### Post by Wybiral on 2007-04-16
I've never had any speed problems with SDL_gfx... Maybe it was a bad example?

You can cache a lot of the elements to their own SDL_Surface and just blit them to the screen surface in some cases, which might help.

---

### Post by tht00 on 2007-04-16
> **loicp said:**
> Hello,

Can you show us the source code ?

Yeah.  I took the one of the examples (TestGfxPrimitives.c) and stripped it down (it is now C++ now too).

I think I've got it down to the basics.  It sped up a little when I took out the unneeded headers from the example.

Also, the color depth was 16, which was default and also what I thought I had read was fastest for the library.  However, changing it to either 8 or 32 speeds it up dramatically.  Almost double fps now.

Here's the code:
(proto.cpp)
```
/*compile with:
g++ proto2.cpp -I /usr/include/SDL -lSDL -lSDL_gfx -o test
*/
#include <iostream>
#include "SDL/SDL.h"
#include "SDL_gfxPrimitives.h"

int main(int argc, char *argv[]) {
	SDL_Surface *screen;
	
	atexit(SDL_Quit);
	
	SDL_Init( SDL_INIT_EVERYTHING );
	
	Uint32 videoflags = SDL_SWSURFACE | SDL_SRCALPHA | SDL_RESIZABLE;
	
	screen = SDL_SetVideoMode(800, 600, 8, videoflags);
	
	SDL_SetAlpha(screen, SDL_SRCALPHA, 255);
	
	Uint32 color=SDL_MapRGBA(screen->format, 0,0,0,255);
	SDL_FillRect (screen, NULL, color);
	
	int mkX1 = 100;
	int mkY1 = 50;
	int mkX2 = 50;
	int mkY2 = 100;
	int mkX3 = 150;
	int mkY3 = 100;
	
	int ticks = SDL_GetTicks();
	for(int i=0; i<200; i++){
		
		SDL_FillRect (screen, NULL, color); //clear
		mkX1++;
		mkX2++;
		mkX3++;
		lineRGBA(screen, mkX1, mkY1, mkX2, mkY2, 0, 255, 0, 255);
		lineRGBA(screen, mkX1, mkY1, mkX3, mkY3, 255, 255, 255, 255);
		lineRGBA(screen, mkX2, mkY2, mkX3, mkY3, 255, 0, 0, 255);	
	
		SDL_UpdateRect(screen, 0, 0, 0, 0);
	}
	double time = SDL_GetTicks() - ticks;
	double sec = time/1000;
	std::cout << 200/sec << "fps" << "\n";
	
	return 0;

}
```

I'm not real clear about the initialization process... Is there anything else that could be optimized and is it correct?  C++ lets you get away with doing a lot of things, so even when things 'work', they aren't always 'right'.

> **IronAvatar said:**
> Are you using the default drivers for your video card?  You shouldn't see such huge drops in performance when rendering one triangle, unless you're using software rendering  instead of direct rendering via the native drivers.

I've got the proprietary drivers for my Nvidia card installed.

Also, my CPU is throttling way up when this is running.  Does SDL automatically use hardware acceleration if it is available, or is my CPU still taking the brunt of everything? 

> **Wybiral said:**
> I've never had any speed problems with SDL_gfx... Maybe it was a bad example?

You can cache a lot of the elements to their own SDL_Surface and just blit them to the screen surface in some cases, which might help.

Yeah, that's why I was checking.  My laptop isn't a monster, but it does have some oomph to it. Intel Core Duo 1.6Ghz, 1 GB ram, Nvidia 7300 Go.  Something doesn't seem right about getting 20-40 FPS for drawing some lines on a 800x600 surface.

I'll definitely keep the caching of images in mind if/when I ever start using images/sprites. :)

---

### Post by cabalas on 2007-04-16
Looking at your code it seems you are using software rendering, to change it to hardware rendering change SDL_SWSURFACE to SDL_HWSURFACE in videoflags and it should do the trick.

---

### Post by slavik on 2007-04-17
I recommend learning OpenGL :)

---

### Post by snoop on 2007-04-17
> **slavik said:**
> I recommend learning OpenGL :)

I would recommend using OpenGL and sdl together for the best of both worlds. :D 

SDL itself is a great start and makes game programming easy! 

I myself started off by looking at this tutorial ( [http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php) ). Its very easy to understand and even goes into openGl a bit at the end.

Good luck and happy programming!

---

### Post by Lster on 2007-04-17
> **snoop said:**
> I would recommend using OpenGL and sdl together for the best of both worlds. :D 

SDL itself is a great start and makes game programming easy! 

...

I would second that.

---

### Post by Damaniel on 2007-04-17
Another thing to try (at least in this example) is to limit the amount of the screen that you update every frame by calling SDL_UpateRect with a set of boundaries that encompasses just the parts that changed -- [FONT="Courier New"]**SDL_UpdateRect(screen, mkX2-1, mkY3-1, mkX3-mkX2+1, mkY3-mkY1+1)** [/FONT] would contain just the triangle and the cleared part of the screen that represents the previous location of the triangle.  You could also consider calling SDL_FillRect on just the parts of the screen that need to be cleared. 

Of course, in a real game, if large parts of the screen change every frame, it becomes more efficient to just update the entire screen each time -- but if you have a static background and moving objects, you'll probably get some performance improvement by running SDL_UpdateRects on just the changed object boundaries.

---

### Post by tht00 on 2007-04-17
> **cabalas said:**
> Looking at your code it seems you are using software rendering, to change it to hardware rendering change SDL_SWSURFACE to SDL_HWSURFACE in videoflags and it should do the trick.

Good catch.  As I said before, this is basically a copy of one of their examples, but _very_ much stripped down.

I have been able to boost it up around 210 FPS (depending on processor activity), although I'm still not convinced it is doing much with my video card -- the difference between the software surface and hardware surface is small -- couple frame/sec difference at most.

Revised code (anything else that can be fixed?)
```
/*compile with:
g++ proto2.cpp -I /usr/include/SDL -lSDL -lSDL_gfx -o test
*/
#include <iostream>
#include "SDL/SDL.h"
#include "SDL_gfxPrimitives.h"

int main(int argc, char *argv[]) {
	SDL_Surface *screen;
	
	atexit(SDL_Quit);
	
	SDL_Init( SDL_INIT_EVERYTHING );
	
	Uint32 videoflags = SDL_HWSURFACE | SDL_ASYNCBLIT | SDL_DOUBLEBUF | SDL_ANYFORMAT ; 
	//| SDL_FULLSCREEN; //| SDL_DOUBLEBUF;
	// | SDL_SRCALPHA | SDL_RESIZABLE;
	//Uint32 videoflags = SDL_SWSURFACE | SDL_SRCALPHA | SDL_RESIZABLE;
	
	screen = SDL_SetVideoMode(640, 480, 8, videoflags);
	
	//SDL_SetAlpha(screen, SDL_SRCALPHA, 255);
	
	Uint32 color=SDL_MapRGBA(screen->format, 0,0,0,255);
	SDL_FillRect (screen, NULL, color);
	
	int mkX1 = 100;
	int mkY1 = 50;
	int mkX2 = 50;
	int mkY2 = 100;
	int mkX3 = 150;
	int mkY3 = 100;
	
	bool direction = true;
	int ticks = SDL_GetTicks();
	int frames = 400;
	for(int i=0; i<frames; i++){
		if(mkX1 > 500)
			direction = false;
		else if(mkX1 < 100)
			direction = true;
		if(direction){
			mkX1++;
			mkX2++;
			mkX3++;
		}
		else{
			mkX1--;
			mkX2--;
			mkX3--;		
		}
		SDL_FillRect (screen, NULL, color); //clear
		lineRGBA(screen, mkX1, mkY1, mkX2, mkY2, 0, 255, 0, 255);
		lineRGBA(screen, mkX1, mkY1, mkX3, mkY3, 255, 255, 255, 255);
		lineRGBA(screen, mkX2, mkY2, mkX3, mkY3, 255, 0, 0, 255);	
		
		SDL_Flip(screen);
		
		//SDL_UpdateRect(screen, 0, 0, 0, 0);
	}
	double time = SDL_GetTicks() - ticks;
	double sec = time/1000;
	std::cout << frames/sec << "fps" << "\n";
	
	return 0;

}
```

> **snoop said:**
> I would recommend using OpenGL and sdl together for the best of both worlds. :D 

SDL itself is a great start and makes game programming easy! 

I myself started off by looking at this tutorial ( [http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php) ). Its very easy to understand and even goes into openGl a bit at the end.

Good luck and happy programming!

Yeah, I found that and I'll definitely use it for building the game engine.  Wish it had a little more with OpenGl, but still good theory/technique 

I think I'll give OpenGL a shot and see how it benchmarks comparatively.  I'd like to get whatever will give me the most overhead.

Does OpenGL have the ability to draw primitives?  Lines and circles (at the least)?  What about the ability to alter the alpha (transparency) of said primitives?  Just wondering if anyone knows off-hand.

Also, how well does OpenGL do with blitting graphics?

> **Damaniel said:**
> Another thing to try (at least in this example) is to limit the amount of the screen that you update every frame by calling SDL_UpateRect with a set of boundaries that encompasses just the parts that changed -- [FONT="Courier New"]**SDL_UpdateRect(screen, mkX2-1, mkY3-1, mkX3-mkX2+1, mkY3-mkY1+1)** [/FONT] would contain just the triangle and the cleared part of the screen that represents the previous location of the triangle.  You could also consider calling SDL_FillRect on just the parts of the screen that need to be cleared. 

Of course, in a real game, if large parts of the screen change every frame, it becomes more efficient to just update the entire screen each time -- but if you have a static background and moving objects, you'll probably get some performance improvement by running SDL_UpdateRects on just the changed object boundaries.

Yeah, that crossed my mind, but I'm not sure how practical that would be in some cases.  I'll may test it later if I decide to stick with SDL.

This has been an excellent discussion so far.  Thanks guys. :D

---

### Post by snoop on 2007-04-18
OpenGL will let you draw lines,points, and polygons, it is going to be faster (i believe) than sdl, but it does not provide you with a framework to do the things sdl lets you. So if you use OpenGL and sdl, you get the benefits of speed, ability to make anything with primitives, and sdl provides you with a nice framework that you can use to create an engine (without having to start from stratch with only OpenGL).

---

### Post by tht00 on 2007-04-18
> **snoop said:**
> OpenGL will let you draw lines,points, and polygons, it is going to be faster (i believe) than sdl, but it does not provide you with a framework to do the things sdl lets you. So if you use OpenGL and sdl, you get the benefits of speed, ability to make anything with primitives, and sdl provides you with a nice framework that you can use to create an engine (without having to start from stratch with only OpenGL).

Yeah, that's what I've been noticing.  I tried the demo at [http://lazyfoo.net/SDL_tutorials/lesson36/index.php](http://lazyfoo.net/SDL_tutorials/lesson36/index.php) and checked the max FPS with it, and it is upwards of 900. :D  *Plenty* of overhead there.

I'll definitely stick with using SDL for the rest.  It is certainly a decent library and the potential for cross platform development is nice.

---

