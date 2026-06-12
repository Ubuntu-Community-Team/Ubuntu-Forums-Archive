---
title: "GLUT vs. FreeGLUT"
date: 2007-07-07
forum: Programming Talk
---

### Post by AlexThomson_NZ on 2007-07-07
Hi all, just a quick Q

Should I be using Glut 3.7, or has this been taken over by FreeGLUT?

Specifically full-screen gameglut in glut 3.7 seems to be broken (or is it just me?).  Usual story- can't find any documentation after 1999/2000

Anyway ideas?  anyone?

---

### Post by DougB1958 on 2007-07-07
As far as I know, nothing much has been done with GLUT per se since about 1999 (anyone else know differently?) But I've been happily using freeGlut for many years now, and I like it. It seems to faithfully implement the GLUT 3.7 features, plus add a few extensions of its own.

---

### Post by AlexThomson_NZ on 2007-07-07
That's great- thanks very much for the reply! :)

---

### Post by AlexThomson_NZ on 2007-07-07
Actually is freeglut still maintained?

I've done some googling and from what I gather gamemode is broken on it and has been for some years now, as has keyboard handling.  Can you (or anyone) confirm?  What should I use in that case for full-screen 3d applications?

---

### Post by Wybiral on 2007-07-07
SDL is great for OpenGL. I prefer it over GLUT because it's less restrictive (you control the flow, you don't pass it over like with GLUT).

It handles events and also offers some stuff in the area of timing/texture loading/2d graphics/audio

SDL is also super-portable and very commonly used.

PS: SDL has a working fullscreen mode

---

### Post by AlexThomson_NZ on 2007-07-07
Thanks for the tip Wybiral, think you might be onto a winner

have been going through some sample progs and looks quite nice

Cheers!

---

### Post by slavik on 2007-07-08
> **Wybiral said:**
> SDL is great for OpenGL. I prefer it over GLUT because it's less restrictive (you control the flow, you don't pass it over like with GLUT).

It handles events and also offers some stuff in the area of timing/texture loading/2d graphics/audio

SDL is also super-portable and very commonly used.

PS: SDL has a working fullscreen mode

GLUT was originally to get a window open as fast as possible with least amount of code possible (for quick OpenGL programs) and for simple keyboard interface ...

SDL on the other hand is designed to be used more extensively

---

### Post by Wybiral on 2007-07-08
> **slavik said:**
> GLUT was originally to get a window open as fast as possible with least amount of code possible (for quick OpenGL programs) and for simple keyboard interface ...

SDL on the other hand is designed to be used more extensively

Maybe, but still, SDL isn't hard to set up either...

And with all the extras it has, I'd say it's the way to go.

---

### Post by DougB1958 on 2007-07-08
> **AlexThomson_NZ said:**
> Actually is freeglut still maintained?

I've done some googling and from what I gather gamemode is broken on it and has been for some years now, as has keyboard handling.  Can you (or anyone) confirm?

I've got several freeGLUT-based projects in progress now, on several platforms (Ubuntu, Windows XP, Mac OS X -- though it has its own implementation of GLUT), and I've never seen problems with fullscreen mode (don't know if that's all you mean by "gamemode" though) or keyboard handling.

But as someone else mentioned, GLUT in all its versions is designed to make bare-bones windows and input available easily, which is all I want out of it. If you want to build a serious user interface, something else might be better -- I've never used SDL, but what's been said about it here is interesting enough that I think I'll look into it....

---

