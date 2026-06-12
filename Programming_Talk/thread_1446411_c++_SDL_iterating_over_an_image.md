---
title: "c++ SDL iterating over an image"
date: 2010-04-04
forum: Programming Talk
---

### Post by Xender1 on 2010-04-04
Trying to figure out how I can look at what color each pixel is of a SDL_Surface. Here is my code:
```

#include <stdlib.h>
#include <iostream>
#include "SDL/SDL.h"
#include "SDL/SDL_image.h"

using namespace std;

/*
 * 
 */
int main(int argc, char** argv) {
    SDL_Init(SDL_INIT_VIDEO);

    SDL_Surface *image;
    image = IMG_Load("testimg.gif");

    cout << "Height: " << image->h << endl;
    cout << "Width: " << image->w << endl;
    
    //FOR LOOP to look at each pixel
    for (Sint32 y = 0; y < image->h; y++) {
        for (Sint32 x = 0; x < image->w; x++) {
            //something

        }
    }


    return (EXIT_SUCCESS);
}

```
Now I am just curious as to know how to access the color of the pixel im looking at and compare it to see what color it is. Thanks.

---

### Post by Zugzwang on 2010-04-04
In the SDL documentation wiki, the is some "getpixel" function code: [http://www.libsdl.org/cgi/docwiki.cgi/Pixel_Access](http://www.libsdl.org/cgi/docwiki.cgi/Pixel_Access)

Don't forget to lock the surface before doing that (and unlocking the surface afterwards)!

---

### Post by Drone022 on 2010-04-04
I have been using this:
```
Uint32 get_pixel32(SDL_Surface *surface, int x, int y){
	//Convert pixels to 32 bits
	Uint32 *pixels = (Uint32*)surface->pixels;

	return pixels[(y*surface->w) + x];
}
```

This is obviously restricted to a 32 bit pixel depth though.

```


SDL_Surface* hello = NULL;
Uint32 temp = 0;


if(SDL_MUSTLOCK(hello)){
		SDL_LockSurface( hello );
	}

	for(int x =0; x < hello->w; x++){
		for(int y = 0; y < hello->h; y++){
			temp = get_pixel32(hello, x, y);
                        // do something with the retrieved value?
		}
	}

if( SDL_MUSTLOCK( hello ) ) {
	SDL_UnlockSurface( hello ); 
}
```

---

