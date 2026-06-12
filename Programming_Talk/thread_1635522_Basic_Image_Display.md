---
title: "Basic Image Display"
date: 2010-12-01
forum: Programming Talk
---

### Post by roadkillguy on 2010-12-01
Hi, I was just wondering the best way to display an image using OpenGL, SDL, and c++.

Also, I'd like to avoid texture mapping.

I've looked into glDrawPixels, but I haven't seen any examples. Has anyone used this function before?  I think it's similar to glBitmap, but I'm not sure how to define color and/or load an image.

Thanks!

---

### Post by fct on 2010-12-02
You can skip opengl and use SDL's functions, or the SDL image library ([http://www.libsdl.org/projects/SDL_image/](http://www.libsdl.org/projects/SDL_image/)) to load from different image formats into an SDL surface.

If you want to apply complicated transformations to the displayed image (like 3d positioning in a scene) then I'm afraid you'll have to look into using the image as a texture.

Hope it helps.

---

