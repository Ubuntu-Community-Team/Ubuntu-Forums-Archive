---
title: "OpenGL programming in C"
date: 2007-03-28
forum: Programming Talk
---

### Post by Lster on 2007-03-28
Hi all

So I already know (a bit!) of OpenGl (on Windows) and wanna be able to do OpenGL in C on Ubuntu. Im sure there was a thread a while back that was about this but I cant find it. I remember needing to install dev libraries... can anyone tell me which to install. Also, a small OpenGL program to test would be great.

Thanks,
Lster

---

### Post by Wybiral on 2007-03-28
You should go to synaptic...

First, and MOST important, you need: **build-essential**
It's the package that has all of your C standard headers and whatnot.

Then, you'll want an easy way to initialize a window with an OpenGL surface...
I would suggest SDL for that, so runtime and dev libraries: **libsdl1.2debian** & **libsdl1.2-dev**

Now you're going to need OpenGL (obviously)...
The development libraries would be: **libgl1-mesa-dev** & **libglu1-mesa-dev**

You should have the GL runtimes installed already (I think they come installed).

Anyway, good luck... OpenGL is a lot of fun.

OH! While you're there, you might want to go ahead and grab: **libsdl-image1.2** & **libsdl-image1.2-dev**

SDL_image will make loading textures for SDL and OpenGL a breeze (in all kinds of formats too)

You can knock all of those out from the command line with:
```

sudo apt-get install build-essential libsdl1.2debian libsdl1.2-dev libgl1-mesa-dev libglu1-mesa-dev libsdl-image1.2 libsdl-image1.2-dev

```

---

### Post by Lster on 2007-03-28
Thank you Wybiral. Ive installed all the packages! I am not familiar with SDL (but I wanna use it) so could you post a simple C app that sets up the screen and renders a triangle (or something simple!).

Once into OGL Im fine... Thanks,
Lster

---

### Post by Wybiral on 2007-03-28
Something like this...

```

// Save as:
//    triangle.c
//
// Compile with:
//    gcc triangle.c -o triangle -lSDL -lGLU -lGL
//
// Execute with:
//    ./triangle

#include <GL/gl.h>
#include <GL/glu.h>
#include <SDL/SDL.h>

// Initialize opengl...
void init_opengl(int width, int height)
{
   glViewport(0, 0, width, height);
   glMatrixMode(GL_PROJECTION);
   gluPerspective(60, (GLfloat)width/height,  1, 2000);

   glMatrixMode(GL_MODELVIEW);
   glEnable(GL_DEPTH_TEST);
}

// Initialize an SDL_Surface as the window surface
// Most of this should explain itself...
SDL_Surface* init_sdl(int width, int height)
{
   SDL_Surface* surface;
   if(SDL_Init(SDL_INIT_VIDEO)< 0)
   {
      return NULL;
   }
   const SDL_VideoInfo* info = SDL_GetVideoInfo();
   if(!info)
   {
      return NULL;
   }
   int flags = SDL_OPENGL | SDL_GL_DOUBLEBUFFER;
	if (info->hw_available)
   {
      flags |= SDL_HWSURFACE;
   }
	else
   {
      flags |= SDL_SWSURFACE;
   }
   surface=SDL_SetVideoMode(width, height, info->vfmt->BitsPerPixel, flags);
   if(surface==0)
   {
      return NULL;
   }
   return surface;
}

int main()
{
   // Create our window and initialize opengl...
   SDL_Surface* buffer = init_sdl(640, 480);
   init_opengl(640, 480);

   // OpenGL code...
   glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT);
   glLoadIdentity();
   glTranslatef(0, 0, -5);
   glBegin(GL_TRIANGLES);
   glColor3ub(0, 255, 0); glVertex2i( 0, 1);
   glColor3ub(255, 0, 0); glVertex2i(-1,-1);
   glColor3ub(0, 0, 255); glVertex2i( 1,-1);
   glEnd();

   // Swap buffers...
   SDL_GL_SwapBuffers();

   // Pause for a couple of seconds...
   SDL_Delay(2000);
}

```

Good luck!

Btw, SDL also has a nice event system for key/mouse/window events.
There are also more SDL libraries that you can use in combination with SDL+OpenGL.
It truly is the easiest way to handle portable OpenGL code.

---

### Post by Lster on 2007-03-28
Thank you again - that was perfect. I will now go learn SDL - it sounds very good indeed :).

Lster

---

### Post by Lster on 2007-03-29
Wow... SDL is easy - Ive already learnt how to get keyboard/ mouse input! I look at a Nehe tutorial for OpenGL (with SDL) it has a way to load a .bmp. I really wanna load PNGs but cant find anything on how to...

Can anyone make me a small PNG load demo... that would rock!

Thanks,
Lster

---

### Post by xtacocorex on 2007-03-29
From quickly looking at stuff, the third paragraph here has a means to load images:
[http://www.de-brauwer.be/wiki/wikka.php?wakka=SDLPlayground](http://www.de-brauwer.be/wiki/wikka.php?wakka=SDLPlayground)

---

### Post by Lster on 2007-03-29
Im fine now... That was a bit tricky though. SDL's website is very good :).

---

### Post by tunisia on 2007-07-03
So I have been playing with C for about two months. Are there any good OpenGL tutorials for linux that I might have any chance of understanding?

thanks

---

### Post by Lux Perpetua on 2007-07-03
Try these: [http://nehe.gamedev.net/](http://nehe.gamedev.net/)

(By the way, just FYI, since your question does not continue the original topic, this belongs in a new thread.)

---

