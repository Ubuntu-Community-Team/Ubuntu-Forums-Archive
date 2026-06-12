---
title: "C++ Library and tutorials for very simple 2-D graphics"
date: 2009-05-14
forum: Programming Talk
---

### Post by morty35 on 2009-05-14
I would like to be able to produce just very simple graphics.  I need be able to make dots at specified coordinates, create lines using 2 coordinates, and write text at different coordinates.  I would also need a very simple color palette (just using RGB values would be fine).  

Making shapes like circles and ovals and being able to fill regions with color would be nice but optional.  Changing the text size would also be nice but optional.  

I want to be able to do this with as little hassle as possible.  Preferably, I would like to learn how to do this in just a few hours.  Is there a library that I can use for C++ that allows me to make these simple graphics.  I want to display data graphically (but not in plots).

It would be nice if there was a simple tutorial as well to show me how to get this up and running very quickly.

Any help would be appreciated. Thanks.

---

### Post by jimi_hendrix on 2009-05-14
OpenGL will work, but is there anything easier?

---

### Post by haTem on 2009-05-14
An easier alternative to OpenGL is using a 2d graphics library, like Allegro. You can find out all you need to accomplish your goals here:

[http://www.cppgameprogramming.com/cgi/nav.cgi?page=allegbasics](http://www.cppgameprogramming.com/cgi/nav.cgi?page=allegbasics)
[http://www.cppgameprogramming.com/cgi/nav.cgi?page=allegprimitive](http://www.cppgameprogramming.com/cgi/nav.cgi?page=allegprimitive)
[http://www.connellybarnes.com/documents/quick_reference.html#tex](http://www.connellybarnes.com/documents/quick_reference.html#tex)

Are you already familiar with a GUI toolkit? If you know Qt, have a look at QPainter or QGraphicsView. If you know gtk, have a look at cairo (or cairomm for C++). Both are pretty simple if you already have experience with the respective toolkit. But allegro (or a similar library) is probably your best bet.

---

### Post by Marco A on 2009-05-14
.

---

### Post by NathanB on 2009-05-14
In a *nix environment (like Ubuntu), you have the option of using Xlib.

The most cross-platform approach is to use SDL (works on Mac OS X, Windows 98, etc... just about _everywhere_).  Tutorials are here:

[http://www.libsdl.org/tutorials.php](http://www.libsdl.org/tutorials.php)

When your projects graduate to the more adventurous, take a look at NeHe's OpenGL tutes:

[http://nehe.gamedev.net/](http://nehe.gamedev.net/)

---

### Post by jimi_hendrix on 2009-05-14
> **NathanB said:**
> 
[http://nehe.gamedev.net/](http://nehe.gamedev.net/)

the setting up a window part is for windows

look at the bottom of the tutorials, you will see three ways to setup a window in linux and see how to use the OpenGL code with these ways

---

### Post by hessiess on 2009-05-15
See signature.

---

### Post by Mad Hacker on 2009-05-15
[SDL]("http://www.libsdl.org") is a good cross-platform library, and although it doesn't have any line/putpixel/circle type functions by itself, there are several libraries made using it


for things like lines, circles, boxes, etc with SDL [SDL_gfx]("http://www.ferzkopp.net/joomla/content/view/19/14/") is easy to learn, there is also [SGE]("http://www.etek.chalmers.se/%7Ee8cal1/sge/index.html")(also for SDL), although i haven't used it, so i don't know much about it, it appears to be quite extensive.

SDL tutorials:
[http://gpwiki.org/index.php/C:SDL_tutorials](http://gpwiki.org/index.php/C:SDL_tutorials)
[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)
[http://sol.gfxile.net/gp/](http://sol.gfxile.net/gp/)

SDL_gfx tutorial
[http://www.aaroncox.net/tutorials/2dtutorials/sdlshapes.html](http://www.aaroncox.net/tutorials/2dtutorials/sdlshapes.html)

---

### Post by hessiess on 2009-05-16
> **Mad Hacker said:**
> [SDL]("http://www.libsdl.org") is a good cross-platform library, and although it doesn't have any line/putpixel/circle type functions by itself, there are several libraries made using it


for things like lines, circles, boxes, etc with SDL [SDL_gfx]("http://www.ferzkopp.net/joomla/content/view/19/14/") is easy to learn, there is also [SGE]("http://www.etek.chalmers.se/%7Ee8cal1/sge/index.html")(also for SDL), although i haven't used it, so i don't know much about it, it appears to be quite extensive.

SDL tutorials:
[http://gpwiki.org/index.php/C:SDL_tutorials](http://gpwiki.org/index.php/C:SDL_tutorials)
[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)
[http://sol.gfxile.net/gp/](http://sol.gfxile.net/gp/)

SDL_gfx tutorial
[http://www.aaroncox.net/tutorials/2dtutorials/sdlshapes.html](http://www.aaroncox.net/tutorials/2dtutorials/sdlshapes.html)

SDL is implemented in software, hence is slow, and lacks basic stuff like rotation and scaling. It is also resolution dependent which is bad considering the wide variation in monitor sizes available. It is handy for setting up and OpenGL context tho.

---

