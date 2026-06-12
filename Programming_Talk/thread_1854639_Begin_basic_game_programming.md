---
title: "Begin basic game programming"
date: 2011-10-04
forum: Programming Talk
---

### Post by mikaelcrocker on 2011-10-04
Hey all, I want to program a game, Something along the lines of Dragon Warrior for the original Nintendo.. just something simplistic and fun!! I just don't know where to start!

I can program and have done so far many years, just never tried game programming.  I am open to different languages and learning new things! Someone please give me some direction on a project I wish to start

Thanks

-Mike

---

### Post by Perfect Storm on 2011-10-05
Moved to Programming Talk.

---

### Post by Pithikos on 2011-10-05
> **mikaelcrocker said:**
> Hey all, I want to program a game, Something along the lines of Dragon Warrior for the original Nintendo.. just something simplistic and fun!! I just don't know where to start!

I can program and have done so far many years, just never tried game programming.  I am open to different languages and learning new things! Someone please give me some direction on a project I wish to start

Thanks

-Mike

Try Python with Pygame. It's simple, clean, fun and with LOADS of support. It's also realistic for a one-man project. There are many tutorials out there to get started ;)

---

### Post by Pynalysis on 2011-10-05
> **Pithikos said:**
> Try Python with Pygame. It's simple, clean, fun and with LOADS of support. It's also realistic for a one-man project. There are many tutorials out there to get started ;)

+1 Pygame with Python.

---

### Post by JDShu on 2011-10-06
Pyglet seems to be favored over pygame these days. I am more familiar with pygame, but from what little I've seen, pyglet is more "pythonic" and modern.

Probably the most important game concept is the game loop, so make sure you understand it well. Game APIs tend to give you access to an event loop to make things easier.

---

### Post by leg on 2011-10-06
For one man enjoyment you could try the [Android]("http://developer.android.com/index.html") environment which will allow you to produce programs for Android devices and if you learn the [AndEngine]("http://www.andengine.org/") lib with it you will have an easy start to creating games. If you want to think of a career you will need C++ and I would look at libs like [Irrlicht]("http://irrlicht.sourceforge.net/") to get a handle on how these programs are put together.

---

### Post by PaulM1985 on 2011-10-06
I would advise you to develop a game in the same way that you would develop any other piece of software.  Look to develop a conceptual model:
What entities exist in you game?  How do these entities link and interact? etc

One thing that I have learnt in the past is don't get bogged down with graphics at an early stage.  Try to keep things very basic (maybe even to the extent of commandline inputs and outputs if it is applicable), then scale it up.  If you write software with a decent architecture using component based design, you should be able to replace one set of graphics classes with an enhanced set in the future.  This is something I have done recently when developing a card game.  Start with commandline and developed further.

Also, alot of people on this thread seemed to instantly recommend using Python.  I would recommend that you use the language that you are already comfortable with.

Good luck.

Paul

---

### Post by DarkAmbient on 2011-10-07
I'd recommend SDL. Platform-independent, fairly easy. And supports 8bits palettes for that ol'school-feeling.

---

