---
title: "OpenGL and SDL"
date: 2008-11-14
forum: Programming Talk
---

### Post by Emill on 2008-11-14
Hello. I am trying to use a 8-bit video mode in OpenGL and show a .bmp-file that is 8-bit color indexed. I use the glTexImage2D-method, but the picture becomes black and white.
I use
SDL_Surface* bmp = SDL_LoadBMP("image.bmp");
to load the picture.

With this code nothing is drawn:
```

glTexImage2D(GL_TEXTURE_2D, 0, 1, bmp->w, bmp->h, 0,
		GL_COLOR_INDEX, GL_UNSIGNED_BYTE, bmp->pixels);

```
With this code, the image becomes black and white:
```

glTexImage2D(GL_TEXTURE_2D, 0, 1, bmp->w, bmp->h, 0,
		GL_RED, GL_UNSIGNED_BYTE, bmp->pixels);

```

I also have a color key that should make it transparent I don't know how to fix.

---

