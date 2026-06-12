---
title: "C++ SDL Image Transparency"
date: 2011-01-20
forum: Programming Talk
---

### Post by Ravenshade on 2011-01-20
I'm using G++ -lSDL, lSDL_image
Gedit for editing

Hi, 

I'm using IMG_Load() to load an image into my program, happens to be a png I haven't particularly tested with others. I used gimp to fade out the edges. When I give this to the program however I get one a number of results. 

If I merge all visible layers... the image I give it gets a darker background layer (considering I deleted it, which is a puzzle in itself) and doesn't show through what's underneath. Secondly it gets a 1px Black Single Line border all around it. 

Now. If I 'flatten' the image, I get a white background, to be honest I expected this, as it just seems to wipe out the transparency effects. 

Does anyone know why this is happening and how I can solve the problem? 

I haven't tried Colorkeying, as for the fact that on Lazy Foo's website it suggests that if I combined png's and color keying I would get 'funky' results, and as a beginner, I'm not wanting to get funky results just yet. 

Thanks for reading.

---

### Post by fct on 2011-01-20
Might be a problem with the alpha value? Check the alpha blending settings before blitting with this function:

[http://www.libsdl.org/cgi/docwiki.cgi/SDL_SetAlpha](http://www.libsdl.org/cgi/docwiki.cgi/SDL_SetAlpha)

values should be SDL_SRCALPHA for flags, and 0 (I think) for alpha?

Hope it helps.

---

### Post by fct on 2011-01-20
* double post *

---

### Post by Ravenshade on 2011-01-20
It was indeed to do with the alpha settings, but it wasn't quite that solution, I was using the wrong syntax... 

> 
Quoting lazy foo...

Trying to color key an image that already has a transparent background is going to cause funky results. You'll also lose the alpha transparency if you use SDL_DisplayFormat() instead of SDL_DisplayFormatAlpha(). To retain transparency on the PNG simply don't color key it.


Guess who was using the former....

---

