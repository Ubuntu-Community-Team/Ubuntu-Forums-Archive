---
title: "SDL steals mouse after killing app"
date: 2007-05-23
forum: Programming Talk
---

### Post by ManSizeRooster on 2007-05-23
Hi all,

I've just started working with SDL, and have encountered an odd problem.

I'm programming a fullscreen application, and want to hide the mouse cursor. However, when I call SDL_ShowCursor(1) to hide it, after I have killed the application all mouse functionality is dead. I'm stumped. I'm using SDL_Quit();, and have tried using SDL_ShowCursor(0); at the end of my program to undo what SDL_ShowCursor(0) does.

Thanks for any help,

ManSizeRooster

PS

Can anyone recommend an OpenGL tutorial better than, or at least comparable to, the NeHe ones?

---

### Post by DoktorSeven on 2007-05-24
From the SDL docs:

> int SDL_ShowCursor(int toggle);

Description
Toggle whether or not the cursor is shown on the screen. Passing SDL_ENABLE displays the cursor and passing SDL_DISABLE hides it. The current state of the mouse cursor can be queried by passing SDL_QUERY, either SDL_DISABLE or SDL_ENABLE will be returned.
The cursor starts off displayed, but can be turned off.

So you need to do SDL_DISABLE and SDL_ENABLE rather than 0 and 1.

The following code works fine for me:

```
#include <SDL/SDL.h>
#include <stdio.h>
#include <stdlib.h>

int main(void)
{
	int leaveprogram = 0;
	SDL_Surface *screen;
	SDL_Event event;
	if (SDL_Init(SDL_INIT_VIDEO) < 0)
	{	
		fprintf (stderr, "SDL init error: %\n", SDL_GetError());
		return EXIT_FAILURE;			
	}
	atexit (SDL_Quit);
	screen = SDL_SetVideoMode (1024, 768, 24, SDL_HWSURFACE | SDL_FULLSCREEN);
	if (screen == NULL) 
	{
		fprintf (stderr, "Could not set 1024x768x24 surface: %s\n", SDL_GetError());
		return EXIT_FAILURE;
	}
	SDL_ShowCursor(SDL_DISABLE);
	
	while (!leaveprogram)
	{
		while (SDL_PollEvent(&event))
		{
			switch (event.type)
			{
				case SDL_KEYUP:
					leaveprogram = 1;
					break;
			}
		}
	}
	SDL_ShowCursor (SDL_ENABLE);
	SDL_Quit();
	return 0;
}

```

---

