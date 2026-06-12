---
title: "SDL OpenGL and Hardware Acceleration"
date: 2007-08-30
forum: Programming Talk
---

### Post by fatalGlory on 2007-08-30
I've programmed my first sdl pong game and I want to make the leap to openGL next.  However, from what I've been reading today around the web, it appears that there is no (good) way to use hardware acceleration with SDL in linux.  Something about using the dga driver?  

I thought I'd try to write something resembling a less mathematical glxgears for an entry level project (just some 3D animation that spits out a framerate for a very basic benchmark).  But if I can't get hardware acceleration, there's not a lot of point benchmarking, lol.

Am I better off to just learn to go through glut or glx instead?

Any wisdom appreciated.

---

### Post by fct on 2007-08-30
You won't get acceleration with the SDL functions like SDL_Blit_Surface(), but **any** OpenGL call will use the hardware acceleration of your system, if available.

Basically:

SDL with no OpenGL -> no acceleration
SDL with OpenGL -> acceleration, if available, to the point that 2D games can be much faster if programmed using OpenGL calls instead of SDL ones.

---

### Post by fatalGlory on 2007-08-30
If that is the case then I have another strange question.  I have compiled a dead simple SDL+openGL app from nehe.gamedev.net (tutorial 2) that just renders a triangle and a square.  Why does this app only render 3000-5000fps whereas glxgears can render 14000fps on my (quite new) system?

Is GLX just a much faster framework for general application stuff and openGL is actually going no slower?  Or is there a detrimental effect to doing openGL with SDL?

Is it perhaps something to do with GLX allowing direct rendering in contrast to SDL?

---

### Post by fct on 2007-08-30
You're getting direct rendering with SDL+GL, as long as your drivers are properly installed. 3000-5000 fps is a high enough value to consider direct rendering is being used.

Anyway, GLX only takes care of graphics and is specific to the X-Window system (if I remember correctly), so it's normal that you lose some performance when using a multi-platform library like SDL which also includes input and audio subsystems. Oh, and GLX uses OpenGL, not another different API.

Plus it's possible that the tutorial code is not as optimized as glxgears', or updates the screen less frequently, etc. Another possible reason is the flags used when initializing video in SDL, there are lots of ways there to increase the frame rate depending on the machine.

The point is SDL+OpenGL is already using hardware acceleration, so don't worry about that part.

---

### Post by fatalGlory on 2007-08-30
Thanks heaps, that takes a load off my mind.  I really like SDL and I didn't want to have to learn a whole new API just to effectively get an openGL context with hardware acceleration.  

Cheers bro.

---

