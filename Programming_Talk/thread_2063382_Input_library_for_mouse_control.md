---
title: "Input library for mouse control"
date: 2012-09-26
forum: Programming Talk
---

### Post by Belopius on 2012-09-26
I use a cross-platform input library called [OIS]("http://sourceforge.net/projects/wgois/") for mouse and keyboard input for my game.  I've noticed the mouse movement is a lot flakier in linux than it is in windows.   The mouse cursor moves unevenly (fast, then slow) even with a smooth mouse motion.

I'm thinking of trying out [SDL]("http://www.libsdl.org/") for input instead.  Is this the most commonly used input library for gaming under linux?  Does anyone have experience with this sort of stuff, with some advice or battle stories to tell?

---

### Post by MG&amp;TL on 2012-10-04
> **Belopius said:**
> The mouse cursor moves unevenly (fast, then slow) even with a smooth mouse motion. 

Odd. I've used OIS before (not seriously), and it worked okay, if I recall.

> 
I'm thinking of trying out [SDL]("http://www.libsdl.org/") for input instead.  Is this the most commonly used input library for gaming under linux?  Does anyone have experience with this sort of stuff, with some advice or battle stories to tell?

SDL works great for that sort of stuff, and you can get an OpenGL rendering context from it as well, so you should be okay. If you're going down the SDL route, have you looked at: [Lazyfoo's tutorials]("http://lazyfoo.net/SDL_tutorials/index.php")?

---

