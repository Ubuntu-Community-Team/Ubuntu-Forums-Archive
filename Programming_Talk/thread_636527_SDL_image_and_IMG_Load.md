---
title: "SDL_image and IMG_Load"
date: 2007-12-09
forum: Programming Talk
---

### Post by Kver on 2007-12-09
Hey;

I've been trying to work on a basic SDL program, and other than SDL I have not been able to get any other libraries working. I'm developing in Anjuta and via Terminal.

I've used the #include "SDL_image.h", and apt-get for the image library. I've also downloaded the source files for the library and development libraries and installed with the instructions in them; The installations say they worked, but I still get the message "error: 'IMG_Load' was not declared in this scope" whenever I try to compile.

I'll upload the whatever files or data anyone might need, thanks for any help!
-Ken

---

### Post by Compyx on 2007-12-10
Have you downloaded and compiled/installed the libraries? That's probably not the best way of going about it, what I'd do is:
```

sudo apt-get install libsdl-dev

```
to install the libraries and associated headers.

After that I can compile and link against SDL with:
```

gcc `pkg-config --libs --cflags sdl` <sourcefile.c>

```

Although many tutorials claim an #include <SDL.h>, on my system I need an #include <SDL/SDL.h>

Here's a link to setting up Anjuta to work with SDL: [http://lazyfoo.net/SDL_tutorials/lesson01/linux/anjuta/index.php]("http://lazyfoo.net/SDL_tutorials/lesson01/linux/anjuta/index.php")
(I have no idea whether these instructions are correct, I don't use Anjuta.)

HTH.

---

### Post by svamppi on 2008-04-26
You may already have figured this out yourself like I did.
You probably need to add the parameter -lSDL_image when using gcc.

---

