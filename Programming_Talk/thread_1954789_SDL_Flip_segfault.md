---
title: "SDL_Flip segfault"
date: 2012-04-08
forum: Programming Talk
---

### Post by linc186 on 2012-04-08
I'm aware that trying to flip a null is pointer is what usually gives a segfault, but I'm pretty sure that I don't have any. This code gives a segmentation fault, I have no idea why, and it's driving me insane. Thanks for your help.
```
#include "SDL/SDL.h"
#include "Initilize.h"
#include <string>
#ifndef EVENTS_H
#define EVENTS_H

class Events : Initilize {
	protected:
		SDL_Surface* Load(std::string filename) {
			SDL_Surface* original = SDL_LoadBMP(filename.c_str());
			SDL_Surface* optimized = NULL;
			if(original != NULL) {
				optimized = SDL_DisplayFormat(original);
				SDL_FreeSurface(original);
			}	
			return optimized;
		}
		void Draw(SDL_Surface* buffer, SDL_Surface* image, int X, int Y) {
			SDL_Rect location;
			location.x = X;
			location.y = Y;
			SDL_BlitSurface(image, NULL, buffer, &location);	
		}
	private:
		SDL_Event event;
	public:
		bool EventCatcher() {
			while(SDL_PollEvent(&event)) {
				switch(event.type) {
					case SDL_QUIT:
						return false;
					break;
					case SDL_KEYDOWN:
						switch(event.key.keysym.sym) {
							case SDLK_z:
								SDL_Surface* google = Load("test.bmp");
								if(google == NULL) {
									return false;
								}
								Draw(screen, google, 30, 30);
								if(SDL_Flip(screen) == -1) {
									return false;
								}
							break;
						}
					break;
					}
				}
				return true;
			}
		} event;
#endif

```
Screen is an inherited member of the class Initilize and looks like:
screen = SDL_SetVideoMode(640, 480, 32, SDL_RESIZABLE);

---

