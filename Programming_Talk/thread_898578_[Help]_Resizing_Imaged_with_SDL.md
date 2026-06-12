---
title: "[Help] Resizing Imaged with SDL"
date: 2008-08-23
forum: Programming Talk
---

### Post by loganwm on 2008-08-23
I've got a directory with images, the images vary in sizes and I'm attempting to resize them all to roughly 100x100 pixels [for thumbnails] in an applicating using SDL Surfaces.

It's just a see-if-you-can-do-it kind of thing as I'm messing with SDL.

I've seen the SDL_gfx rotozoom function, but it uses a scale factor rather than a size measurement, I could possibly write an algorithm for that, but I want to know if there are any alternatives?

All Help is appreciated.

---

### Post by mike_g on 2008-08-23
Assuming you know your image size you could convert a fixed width/height to a scale factor. Something like:
```
scale_width = (1.0 / original_width) * new_width;
```
Same for height.

Alternatively could could write your own image scaling code; its not too hard. If you like I can post some code I wrote in basic for this.

---

### Post by loganwm on 2008-08-23
> **mike_g said:**
> Assuming you know your image size you could convert a fixed width/height to a scale factor. Something like:
```
scale_width = (1.0 / original_width) * new_width;
```
Same for height.

Alternatively could could write your own image scaling code; its not too hard. If you like I can post some code I wrote in basic for this.

Out of curiousity, with SDL, is there a way to get the image attributes (size, etc)?

---

### Post by mike_g on 2008-08-23
yes, width and height are stored in the SDL_Surface struct:
[http://docs.mandragor.org/files/Common_libs_documentation/SDL/SDL_Documentation_project_en/sdlsurface.html](http://docs.mandragor.org/files/Common_libs_documentation/SDL/SDL_Documentation_project_en/sdlsurface.html)

---

### Post by loganwm on 2008-08-23
> **mike_g said:**
> yes, width and height are stored in the SDL_Surface struct:
[http://docs.mandragor.org/files/Common_libs_documentation/SDL/SDL_Documentation_project_en/sdlsurface.html](http://docs.mandragor.org/files/Common_libs_documentation/SDL/SDL_Documentation_project_en/sdlsurface.html)

Much thanks!

---

