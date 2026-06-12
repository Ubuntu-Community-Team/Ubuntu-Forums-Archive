---
title: "Compiling SDL and fmod (code::blocks)"
date: 2008-12-13
forum: Packaging and Compiling Programs
---

### Post by tradet on 2008-12-13
I've been working on this little program of mine on windows but now it's time for a change. I used code::blocks and I'm planning to continue to use it, same goes with SDL and fmod. I'll be switching from openlayer to glut.

For SDL I searched the package manager and installed the *libsdl.1.2debian-all* which is supposed to use all SDL options. I'll be needing *SDL_thread* and *SDL_net* as addons.

Under other linker settings I have:
```

-luser32 -lgdi32 -lglu32 -lopengl32
-lSDLmain -lSDL -lSDL_ttf -lSDL_image -lSDL_net
-lfmod
```
I'm not sure if I need all linkers. Isn't the 32 destined for win32? And what should I use instead to get opengl and glut?

In my cpp files I've included:
```
#include <sdl.h>
#include <SSDL_thread.h>
#include <sdl_net.h>
#include <sdl_image.h>
#include <sdl_ttf.h>
#include <fmod.h>
```
I'm getting error on all files here. Fmod I know I don't have but their [release]("http://www.fmod.org/index.php/download#FMODExProgrammersAPI") are only for amd, which I don't have. I don't know how to compile from source or even where to find their source.

Also I had this for glut:
```
#include <GL/gl.h>
#include <GL/glu.h>
```
I don't have any code using glut atm but for the future.

---

### Post by tradet on 2008-12-13
Sigh...

Got SDL working:
[howto]("http://ubuntu-gamedev.wikispaces.com/How-To+Setup+SDL+for+games+development")
Just case problem, I should know better. SDL/SDL.h is right.

Only fmod to go, wouldn't be surprised if I found another howto.

---

