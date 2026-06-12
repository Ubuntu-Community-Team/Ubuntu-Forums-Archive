---
title: "SDL2 Renderer Viewport"
date: 2014-07-26
forum: Programming Talk
---

### Post by mode7 on 2014-07-26
(I can go ask around the SDL forum, but I already had an account here, figured I would try here first EDIT: Made an account there, but have to wait for approval)
I have been messing around with doing a moving camera, for the usual issue of navigating an area larger than your display size.

Actually implementing a viewport using SDL_RenderSetViewport was quite easy, but I've noticed an issue.
The renderer only seems to draw to an area that maps out to the size of the created window.

So, supposing that I have a level that is 1024x768 in size, and I create a 640x480 window, it only draws to that original 640x480 chunk from 0,0.
The viewport will move along with the player in the center, but if I move away from the top left of the screen, it won't render anything past in-game 640X and 480Y.

I can understand the renderer being able to only output to the dimensions of the created window, but why is the renderer incapable of rendering outside that chunk of in-game world?
The renderer still clears the whole screen with it's draw color.
I also tried rendering to a texture with render targets, but then the viewport doesn't work. I tried resetting the render target right before the set viewport call as well.

Anyhow, if anyone has messed with SDL2 development, I'd appreciate any assistance. I'm having a very hard time finding good documentation for these renderer functions. If I need to rethink the way I'm doing the viewport as well, I'm open to that too. Thanks in advance!

---

### Post by Ghostmn on 2014-07-27
[https://wiki.libsdl.org/](https://wiki.libsdl.org/)
[http://lazyfoo.net/tutorials/SDL/index.php](http://lazyfoo.net/tutorials/SDL/index.php)

These are the best sources I have found online for sdl2 development. I tend to use the api reference from the official website, since SDL2 is sort of easy to get into. The latter has a tutorial on just about everything with regards to SDL2.

I'm sorry I can't help you any further. I only use SDL2 for handling input and initializing a screen. I do all my rendering with opengl.

---

### Post by mode7 on 2014-07-27
Thanks for the response, Ghostmn.
I do use the SDL wiki, and have went through several of the Lazyfoo tutorials (They are excellent for teaching specific components).

I guess the problem is that I can't really find too much info on SDL2's renderer. I think there is a limitation that the created renderer context is tied to the resolution of the window it is attached to.
What confused me, though, was that it tied itself to the same spot in the in-game world coordinates. It's quite hard to explain, without showing it.
I think I'm probably going to stop using the viewport, and just shift everything (when drawing) relative to camera view, which seems to be the usual approach.

I would like to learn OpenGL at some point, but am sticking to SDL's rendering features for now, because I am still trying to learn how to tie specific components together.
Speaking of which, if anyone has any good resources for explaining those object-oriented component concepts, I would love to check them out. (Game states, messaging, tying input/video/sound together to an entity based system, etc)

---

