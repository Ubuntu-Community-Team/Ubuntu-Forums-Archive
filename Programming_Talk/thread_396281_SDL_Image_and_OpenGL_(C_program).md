---
title: "SDL_Image and OpenGL (C program)"
date: 2007-03-29
forum: Programming Talk
---

### Post by Lster on 2007-03-29
Im using SDL for OpenGL in C.

Im just learning SDL (I already know a bit of OpenGL) and Im using the IMG_Load function (in SDL_image) to load a PNG. That was fine, but the color is strange (because of different color encoding?). So I looked on Nehe and hacked around with some BMP loader and made a PNG loader with OK color.

However I cant get transparency which I really need. I learn best from examples - if anyone could be *really* kind and show me some simple SDL/ OpenGL PNG load code that would be great!

Otherwise any ideas?

Thanks all
Lster

---

### Post by Wybiral on 2007-03-29
You have to check the surface for a "Amask", then you have to use the right GLU function to load it (with GL_RGBA).

This function will handle both, although I suppose it would be better to add a function parameter for alpha being on/off (if an image has any alpha).

```

GLuint load_texture(const char* file)
{
   SDL_Surface* surface = IMG_Load(file);
   GLuint texture;
   glPixelStorei(GL_UNPACK_ALIGNMENT,4);
   glGenTextures(1, &texture);
   glBindTexture(GL_TEXTURE_2D, texture);
   SDL_PixelFormat *format = surface->format;
   if (format->Amask)
   {
      gluBuild2DMipmaps(GL_TEXTURE_2D, 4,
         surface->w, surface->h, GL_RGBA,GL_UNSIGNED_BYTE, surface->pixels);
   }
   else
   {
      gluBuild2DMipmaps(GL_TEXTURE_2D, 3,
         surface->w, surface->h, GL_RGB, GL_UNSIGNED_BYTE, surface->pixels);
   }
   SDL_FreeSurface(surface);
   return texture;
}

```

---

### Post by Lster on 2007-03-29
The new code still doesnt do alpha. It loads the image and displays it perfectly but no alpha. The image really does have alpha (both GIMP and F-Spot show it with alpha).

Maybe I setup OpenGL wrong? Any more ideas - youve been *really* helpful :).

Thanks,
Lster

---

### Post by Wybiral on 2007-03-29
That loads alpha textures for me. Maybe your OpenGL isn't set up.

To render things with alpha enables you have to enable GL_ALPHA_TEST

Then, you have to set the glAlphaFunc to the right alpha function.

Something like this should work (in your OpenGL initialization):

```

glEnable(GL_ALPHA_TEST);
glAlphaFunc(GL_GREATER, 0.5);

```

This will ignore drawing any pixels with alpha less then 50%.

Check this page out:

[http://www.opengl.org/documentation/specs/man_pages/hardcopy/GL/html/gl/alphafunc.html](http://www.opengl.org/documentation/specs/man_pages/hardcopy/GL/html/gl/alphafunc.html)

---

### Post by Lster on 2007-03-29
Thank you sooooooooooooooooooooooooooooooooooooo much Wybiral :). All perfect!

---

