---
title: "SDL static background"
date: 2009-08-06
forum: Programming Talk
---

### Post by chris200x9 on 2009-08-06
I am just learning SDL, after reading the wiki I get this ```
 #include "stdio.h"
#include "SDL/SDL.h"

int main(int argc, char *argv[])
{
	SDL_Surface *screen;	//This pointer will reference the backbuffer
	SDL_Surface *image;	//This pointer will reference our bitmap sprite
	SDL_Surface *temp;	//This pointer will temporarily reference our bitmap sprite
	SDL_Rect src, dest;	//These rectangles will describe the source and destination regions of our blit
	
	//We must first initialize the SDL video component, and check for success
	if (SDL_Init(SDL_INIT_VIDEO) != 0) {
		printf("Unable to initialize SDL: %s\n", SDL_GetError());
		return 1;
	}
	
	//When this program exits, SDL_Quit must be called
	atexit(SDL_Quit);
	
	//Set the video mode to fullscreen 640x480 with 16bit colour and double-buffering
	screen = SDL_SetVideoMode(640, 480, 16, SDL_DOUBLEBUF);
	if (screen == NULL) {
		printf("Unable to set video mode: %s\n", SDL_GetError());
		return 1;
	}
	
	//Load the bitmap into a temporary surface, and check for success
	temp = SDL_LoadBMP("image.bmp");
	if (temp == NULL) {
		printf("Unable to load bitmap: %s\n", SDL_GetError());
		return 1;
	}
	
	//Convert the surface to the appropriate display format
	 image = SDL_DisplayFormat(temp);
	
	//Release the temporary surface
	SDL_FreeSurface(temp);
	
	//Construct the source rectangle for our blit
	src.x = 0;
	src.y = 0;
	src.w = image->w;	//Use image->w to display the entire width of the image
	src.h = image->h;	//Use image->h to display the entire height of the image
	
	//Construct the destination rectangle for our blit
	dest.x = 100;		//Display the image at the (X,Y) coordinates (100,100)
	dest.y = 100;
	dest.w = image->w;	//Ensure the destination is large enough for the image's entire width/height
	dest.h = image->h;
	
	//Blit the image to the backbuffer
	SDL_BlitSurface(image, &src, screen, &dest);
	
	//Flip the backbuffer to the primary
	SDL_Flip(screen);
	
	//Wait for 2500ms (2.5 seconds) so we can see the image
	 SDL_Delay(2500);
	
	//Release the surface
	SDL_FreeSurface(image); 
	
	//Return success!
	return 0;
}

```

how do I create a static background that just stays there instead of disapearing after 2.5 seconds?

---

### Post by Simian Man on 2009-08-06
You need to make an event loop that waits for the user to quit:
```

#include "stdio.h"
#include "SDL/SDL.h"

int main(int argc, char *argv[])
{
  SDL_Surface *screen;  //This pointer will reference the backbuffer
  SDL_Surface *image; //This pointer will reference our bitmap sprite
  SDL_Surface *temp;  //This pointer will temporarily reference our bitmap sprite
  SDL_Rect src, dest; //These rectangles will describe the source and destination regions of our blit
  
  //We must first initialize the SDL video component, and check for success
  if (SDL_Init(SDL_INIT_VIDEO) != 0) {
    printf("Unable to initialize SDL: %s\n", SDL_GetError());
    return 1;
  }
  
  //When this program exits, SDL_Quit must be called
  atexit(SDL_Quit);
  
  //Set the video mode to fullscreen 640x480 with 16bit colour and double-buffering
  screen = SDL_SetVideoMode(640, 480, 16, SDL_DOUBLEBUF);
  if (screen == NULL) {
    printf("Unable to set video mode: %s\n", SDL_GetError());
    return 1;
  }
  
  //Load the bitmap into a temporary surface, and check for success
  temp = SDL_LoadBMP("temp.bmp");
  if (temp == NULL) {
    printf("Unable to load bitmap: %s\n", SDL_GetError());
    return 1;
  }
  
  //Convert the surface to the appropriate display format
   image = SDL_DisplayFormat(temp);
  
  //Release the temporary surface
  SDL_FreeSurface(temp);
  
  //Construct the source rectangle for our blit
  src.x = 0;
  src.y = 0;
  src.w = image->w; //Use image->w to display the entire width of the image
  src.h = image->h; //Use image->h to display the entire height of the image
  
  //Construct the destination rectangle for our blit
  dest.x = 100;   //Display the image at the (X,Y) coordinates (100,100)
  dest.y = 100;
  dest.w = image->w;  //Ensure the destination is large enough for the image's entire width/height
  dest.h = image->h;
  

  [B]// main game loop
  SDL_Event event;
  int playing = 1;

  while(playing) {
    while(SDL_PollEvent(&event)) {
      if(event.type == SDL_QUIT)
        playing = 0;
    }

    //Blit the image to the backbuffer
    SDL_BlitSurface(image, &src, screen, &dest);
  
    //Flip the backbuffer to the primary
    SDL_Flip(screen);
  }
[/B]
  
  //Release the surface
  SDL_FreeSurface(image); 
  
  //Return success!
  return 0;
}

```

You can also handle other types events besides SDL_QUIT such as keyboard, mouse, joystick and so on.

---

### Post by chris200x9 on 2009-08-06
thank you! :)

---

