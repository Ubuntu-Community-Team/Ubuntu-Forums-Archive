---
title: "SDL, OpenGL, and ray tracing"
date: 2011-05-17
forum: Programming Talk
---

### Post by ApEkV2 on 2011-05-17
Hello, I've recently been working on a ray tracer as a hobby and have stumbled upon a problem. I have a malloced buffer that contains RGBA pixels as floats and was wondering what the best way to get them on the screen.

I'm currently trying to use SDL with OpenGL's glDrawPixels() but that isn't working. Is there a way to take this buffer and turn it into a 2d OpenGL texture or an SDL_surface?

---

### Post by TheStroj on 2011-05-17
Since you're already working with OpenGL I suppose you remember the very first example in every SDL tutorial: Drawing pixels on screen. You already have the colors set, now simply draw them (Lock surface -> draw -> Unlock Surface-> Update). 

I can't think of a better tutorial on starting with SDL than this: the3fold.free.fr/doc/games.pdf (It's a game programming guide but the introduction to SDL is great).

---

### Post by ApEkV2 on 2011-05-17
Well that was easy enough. Thanks for pointing me in the right direction, everything works.

---

