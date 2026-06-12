---
title: "Intention to (re)make a game"
date: 2007-06-15
forum: Programming Talk
---

### Post by vexorian on 2007-06-15
Hey I once made a game using SDL, at [http://xye.sourceforge.net](http://xye.sourceforge.net) , the project failed because I had issues with interfaces and internationalization (was not able to have internationalization at all, would I require a giantic font image that contains every single possible character... that's not good.

Decided I still wanted to make the game but need an actual GUI library, that way it would be more like original kye, I've been thinking on gtk which is also cross platform thus I wouldn't lose the windows target yet.

Any directions on programming for gtk? Also, how does gtk do on drawing on the window/a control? I need somethings like stamping images in certain positions and also need alpha support for rendering the images.


Something that would make everything much easier would be the ability to have SDL and gtk at the same time.

---

### Post by pmasiar on 2007-06-15
[Pygame](http://en.wikipedia.org/wiki/Pygame)?

---

### Post by vexorian on 2007-06-15
gtk? AFAIK pygame just uses SDL which is what caused me the issues I am trying to solve, unless I am missing something.

---

### Post by chriswyatt on 2007-06-27
Are you aware of Python Kye?  Just downloaded it today.  Used to have this game (well, the original) on our old PC after one of my dad's old workmates gave him a floppy disk worth of games.

[http://games.moria.org.uk/kye/pygtk]("http://games.moria.org.uk/kye/pygtk")

---

### Post by vexorian on 2007-06-27
I am aware of it,

A long ago I just decided that I'll stay in SDL, I got SDL_ttf so It is finally able to handle international characters, the only extra annoyance pending would be lack of desktop theme support but I guess people can live with it.

---

