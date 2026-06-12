---
title: "pixel level modifications on an SDL_Surface"
date: 2009-11-03
forum: Programming Talk
---

### Post by bennn on 2009-11-03
hi guys,

i'm a newbie using sdl in C++. I did my codes to try to get rgb color components from an 8-bit grayscale image using what was taught here : <html>http://sdl.beuc.net/sdl.wiki/SDL_PixelFormat</html>

However, I keep getting this error: incompatible types in assignment at this line:
color = fmt->palette->colors[index];

My partial code as shown below:

void colorInterpolation(SDL_Surface *s)
	{
		SDL_PixelFormat *fmt;
  		Uint32 temp, pixel;
   		Uint8 red, green, blue, alpha, index;
		SDL_Color *color;
		
		fmt=s->format;

 		/* Check the bitdepth of the surface */
 		if(fmt->BitsPerPixel!=8){
 			fprintf(stderr, "Not an 8-bit surface.\n");
 			return;
		}
  		
		SDL_LockSurface(s);
..............
............
		/* Get the topleft pixel */
    		index = *(Uint8 *)s->pixels;
		color = fmt->palette->colors[index]; //ERROR : incompatible types in assignment WHY??????
.............
...........
.......

Your advice is highly appreciated!!! thanks! :D

---

### Post by efexD on 2009-11-03
Did you check the return types of what you're trying to assign?

---

### Post by fct on 2009-11-03
You're getting an SDL_Color type, not a pointer to it (SDL_Color *).

Try redefining your var declaration to "SDL_Color color" or this:

```
color = &(fmt->palette->colors[index]);
```

Should be it, but can't check it right now.

---

