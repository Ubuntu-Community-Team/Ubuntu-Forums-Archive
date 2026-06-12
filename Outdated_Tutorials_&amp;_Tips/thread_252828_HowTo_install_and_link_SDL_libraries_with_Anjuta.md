---
title: "HowTo install and link SDL libraries with Anjuta"
date: 2006-09-07
forum: Outdated Tutorials &amp; Tips
---

### Post by siDDis on 2006-09-07
SDL is a great library for cross-platform multimedia applications and Anjuta is a great Gnome based IDE to program in. This HowTo should make it easy for newcomers to get Anjuta and SDL working just fine without going the “difficult” way to setup a SDL project.

**The first step is for those who doesn't have installed Anjuta. To install Anjuta and all the build packages you type**

```
sudo apt-get install anjuta build-essential autoconf libtool automake libglib2.0-dev
```

Now you should have everything you need to make “Hello World” :)

**The second step is to get all the SDL packages,**

```
sudo apt-get install libsdl1.2-dev libsdl-gfx1.2-dev libsdl-image1.2-dev libsdl-net1.2-dev libsdl-ttf2.0-dev
```

This is the libraries for most things like graphics, bitmaps, network, fonts, keyboard and so on. I didn't include the sound libraries because it's heavily recommended to use OpenAL for that ;)

To get OpenAL you type

```
sudo apt-get install libopenal-dev
```

If you still want to use SDL sound alternatives,

```
sudo apt-get install libsdl-mixer1.2-dev libsdl-sound1.2-dev
```

**For the third step you configure Anjuta to use the SDL libraries.**

First click on file and select “New Project”. Select “Generic/Terminal project”. Give your project a name like SDLTest and just click continue.

Now we need to add a linker to SDL. Click on “Settings” and select “Compiler and Linker Settings”. Select “Libraries” and just type in **SDL** and click add.

Now you need to change the main.c file

Delete everything and copy this in

```
#include "SDL/SDL.h"
const int WINDOW_WIDTH = 640;
const int WINDOW_HEIGHT = 480;
const char* WINDOW_TITLE = "SDL Start";

int main(int argc, char **argv)
{
	SDL_Init( SDL_INIT_VIDEO );
	SDL_Surface* screen = SDL_SetVideoMode( 
		WINDOW_WIDTH, WINDOW_HEIGHT, 0, 
		SDL_HWSURFACE | SDL_DOUBLEBUF );
	SDL_WM_SetCaption( WINDOW_TITLE, 0 ); 
	SDL_Event event;
	int gameRunning = 1;
	while (gameRunning)
	{
		if (SDL_PollEvent(&event))
		{
			if (event.type == SDL_QUIT)
			{
				gameRunning = 0;
			}
		} 
	}
	SDL_Quit();
	return 0;
}
```

Build & compile this and then run it from the terminal,

```
./Projects/SDLTest/src/sdltest
```

Your first SDL application should now run with a small black window :)

If you need to use to other libraries like SDL TrueType fonts you add it at the same place as you did with SDL

Settings --> Compiler and Linker Settings ---> Libraries and type **SDL_ttf** and click Add.

Add this to your main.c and build the project again. 
```
#include “SDL/SDL_ttf.h” 
TTF_Init();
TTF_Quit();
```

If you've linked it properly you should get a successful build!

Great SDL tutorials can be found here: [http://www.aaroncox.net/tutorials/index.html](http://www.aaroncox.net/tutorials/index.html)

Good luck with your SDL programming! :)

---

### Post by kendase3 on 2007-12-20
First of all, I'd just like to say this guide was very informative and well-written.  However, "Compiler and Linker settings don't come up for me in my version of Anjuta, even though I'm running Ubuntu Gutsy and have installed everything you recommended.  My settings options are much more sparse, with only 4 options, and linker settings nowhere in sight.  I'd really like to be able to set up the IDE and use SDL so any help would be greatly appreciated.

As a separate issue, I'm not entirely sure how I go about making my basic "Hello World!" application runnable.  It compiles just fine but I'm having trouble seeing a way to run i, either within Anjuntu or outside.  Any help on either of these issues would be greatly appreciated.

update: I've actually solved my second problem, don't know why I couldn't figure out how to run a simple shell script followed by make, but now I have!  My first, somewhat graver SDL problem remains though, and any help would be greatly appreciated.

---

### Post by kiaran on 2009-09-21
Thank you for the tutorial!

This might be a little out of date now though. Anjuta now has a wizard to create an SDL project. I just tried it and had a basic SDL system running in a just a few clicks.

It remains to be seen how difficult it will be when I need to link to some other libraries, but so far it's pretty smooth. :)

-K

---

