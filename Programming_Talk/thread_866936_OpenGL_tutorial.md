---
title: "OpenGL tutorial"
date: 2008-07-22
forum: Programming Talk
---

### Post by happysmileman on 2008-07-22
I was wondering if there's any good OpenGL tutorials for Linux out there, I could only find Windows specific ones (as in, they use windows.h a lot).

I've been using Qt and KDE libs for my GUIs so I was thinking of using the Qt OpenGL bindings, but I'm not sure it's that's be a good idea when just starting off, does anyone know if they're very different, would just using pure OpenGL be better?

Edit: Just looked into it and it seems that Qt's OpenGL libraries just provide a few (6) classes to make OpenGL integrate better with Qt programs, all the rendering itself uses the exact same functions as pure OpenGL, so at least I won't have to re-learn anything for either.

---

### Post by happysmileman on 2008-07-22
Forgot to mention I'm using C++

---

### Post by Lster on 2008-07-22
Have a look at these:

[http://nehe.gamedev.net/](http://nehe.gamedev.net/)
[http://www.gamedev.net/reference/list.asp?categoryid=31](http://www.gamedev.net/reference/list.asp?categoryid=31)

---

### Post by happysmileman on 2008-07-22
> **Lster said:**
> Have a look at these:

[http://nehe.gamedev.net/](http://nehe.gamedev.net/)
[http://www.gamedev.net/reference/list.asp?categoryid=31](http://www.gamedev.net/reference/list.asp?categoryid=31)

I've looked at the tutorials at [http://nehe.gamedev.net](http://nehe.gamedev.net) and they seem pretty good, but the Linux code for them seems to be very different to the code used in the tutorial and makes it kinda hard to follow (the Linux code isn't very well commented in places so I can't really just use that to learn from).

I was wondering if there's any up to date ones specifically for Linux.

---

### Post by bsund on 2008-07-22
[GLUT]("http://en.wikipedia.org/wiki/OpenGL_Utility_Toolkit") will set up a window etc so you don't need to bother with linux specific code.

---

### Post by happysmileman on 2008-07-22
> **bsund said:**
> [GLUT]("http://en.wikipedia.org/wiki/OpenGL_Utility_Toolkit") will set up a window etc so you don't need to bother with linux specific code.

I know that there shouldn't be Linux specific code, the problem is that tutorials tend to have Windows specific code, including that tutorial posted, there is Linux code available from the tutorial but much of it is very different, there's less code in some places and it's not very well commented.

I've found what appears to be a basic tutorial on OpenGL [here](http://www.glprogramming.com/red/chapter01.html). From the URL and the chapter titles I am guessing it's an older version of "the red book", it uses GLUT in some examples and uses only OpenGL functions, nothing OS specific, which is perfect.

I was thinking about getting a new version of the red book if I get through some tutorials well, since it's nice to have an up to date, printed copy of a guide rather than read online, if anyone here has read it would you recommend it? Or are there other good guides?

---

### Post by Senesence on 2008-07-23
I think this is what you're looking for:

[http://lazyfoo.net/SDL_tutorials/lesson36/index.php](http://lazyfoo.net/SDL_tutorials/lesson36/index.php)

Regardless of the platform, OpenGL is still OpenGL, even if the input/window handling code is platform specific.

The painful part is getting to the level where you can understand the code enough to find that "split", and work around it (or at least, it was for me).

---

### Post by abdullahValter on 2008-11-11
Yes I've found this place:

[http://www.videotutorialsrock.com/](http://www.videotutorialsrock.com/)

Valter

---

