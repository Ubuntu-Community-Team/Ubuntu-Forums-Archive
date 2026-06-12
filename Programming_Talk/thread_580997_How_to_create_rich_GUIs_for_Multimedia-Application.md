---
title: "How to create rich GUIs for Multimedia-Applications?"
date: 2007-10-19
forum: Programming Talk
---

### Post by lone1 on 2007-10-19
Hello,

I'm looking for a GUI-Toolkit that allows me to easily create simple, fullscreen-based, animated applications like Tivo or MythTV. What would you recommend? I've thought about libsdl, but the documentation seems a bit too focussed on games.

---

### Post by archivator on 2007-10-19
SDL (or pygame) could be a good starting point. They give you most control over what's being drawn. 

If you want something easy, try [clutter](http://clutter-project.org/) ;)

---

### Post by lone1 on 2007-10-19
Thank you, that's what I'm looking for. Unfortunately it requires OpenGL, so I can't use it :(

SDL is not an option since it's not a toolkit, it's too low-level. I more looking for an oo-library that lets me create widgets and such, but with big fonts and animations. 

Is there maybe anything else, that does not require OpenGL?

edit:
Pigment looks promising: [https://code.fluendo.com/pigment/trac](https://code.fluendo.com/pigment/trac)

---

### Post by Nekiruhs on 2007-10-19
Just curious, but why the no OpenGL requirement? OpenGL is a widely accepted set of libraries.

---

### Post by slavik on 2007-10-19
I'm sure GTK would be able to handle this (so shoudl QT4).

---

### Post by Wybiral on 2007-10-20
Are you trying to play videos or write games/interactive 2d graphics? If you're aiming at videos, I suggest gstreamer (there is a [GStreamer module for Python]("http://pygstdocs.berlios.de/pygst-tutorial/index.html")). I use gstreamer in one of my applications that requires playing videos of various formats and it works great (and it integrates great with GTK). If it's game/interactive 2d graphics you want, then [SDL]("http://www.libsdl.org") or [PyGame]("http://pygame.org/news.html") will work fine (btw, SDL isn't game specific, it's just a general media library). And PyGame can be used for 2d graphics, it doesn't require the use of OpenGL (it's based on SDL).

---

### Post by lone1 on 2007-10-22
Thanks for the replys so far,

I'm working on a UPnP AV client that is supposed to let a user browse through a media library. I'm looking for a simple way to create animated menus. SDL isn't all bad, but I'm looking for something simpler, that ist object-oriented and let's me get things done faster.

Correct me if I'm wrong, but I don't  think GTK is suitable to create something like this:
[img]http://geexbox.org/img/freevo-scr-menu.png[/img]

I know GStreamer and that it's capable of rendering media, but  I don't see how it can be used to design a user-interface.

My target device has no OpenGL, that's why clutter is not an option.

---

### Post by gthm159 on 2008-06-10
Bump.

Hi Lone1,

Did you choose a GUI toolkit to work with?
I'm at a stage where I'm evaluating clutter and pigment to choose one that suits me better.

Any inputs on these (or other similar toolkits) would be very helpful.

Regds,
Gautam

---

### Post by loell on 2008-06-10
[http://wiki.enlightenment.org/index.php/Creating_Edje_User_Interfaces]("http://wiki.enlightenment.org/index.php/Creating_Edje_User_Interfaces")

---

### Post by gthm159 on 2008-06-16
Thanks for the link loell. It looks like now I have another graphical toolkit to evaluate besides Clutter and Pigment :)

Why is it that most applications having really cool user interfaces are written in Python?
I have never programmed with Python, and I don't have much knowledge about it. Is it more suitable for writing UIs than C or C++?

Regds,
Gautam

---

### Post by LaRoza on 2008-06-16
> **gthm159 said:**
> 
Why is it that most applications having really cool user interfaces are written in Python?
I have never programmed with Python, and I don't have much knowledge about it. Is it more suitable for writing UIs than C or C++?


I don't know if that is true or not, but Python can use the same toolkits as C or C++ (and other languages) so it really isn't dependent on the language. However, a language like Python makes makes GUI programming less painful as you don't have to deal with static typing.

---

