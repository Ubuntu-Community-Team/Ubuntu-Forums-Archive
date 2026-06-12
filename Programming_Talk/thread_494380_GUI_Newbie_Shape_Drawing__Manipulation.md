---
title: "GUI Newbie: Shape Drawing / Manipulation"
date: 2007-07-06
forum: Programming Talk
---

### Post by tonyr1988 on 2007-07-06
I want to create a very simple gravity simulator for a quick project. I need to be able to draw some circles (representing planets, or any other object) of particular sizes, and move them to particular locations after every "refresh." Does that make any sense? It's really basic - circles only (no other shapes), but I need to be able to control each one as if it were a separate object.

What's the best way to accomplish this? I'm just learning how to use Glade to make Gnome GUI apps, but it doesn't seem like it'll work for what I need. Do I need to use something like OpenGL, or is there something easier for 2D graphics?

I can use Java or Python. I could also use C, but it's my last preference if possible.

Gracias!

---

### Post by runningwithscissors on 2007-07-07
Cairo is a decent library to draw 2D stuff.

Although I wouldn't say that it is very easy to work with.

---

### Post by dwblas on 2007-07-08
google for "pic groff"  Pic is a diagraming language, so the 'circle' command  will draw a circle with a standard diameter if you don't specify a diameter.  You can use a simple Python script to output the pic file and can then convert to postscript, tiff, or any other format that you may want.  Also, I would think that Python's Imaging Library would work but it sounds like overkill.
See the smiley example here:
[http://www.onlamp.com/pub/a/onlamp/2007/06/21/in-praise-of-pic.html?page=last](http://www.onlamp.com/pub/a/onlamp/2007/06/21/in-praise-of-pic.html?page=last)

---

### Post by tonyr1988 on 2007-07-09
Thanks for the suggestions - I'll definiately look into those and see what I can get out of them.

Also, in the meantime (waiting for replies), I stumbled across pyGame, which looks like decent and pretty simple. Then, another question came to mind:

With any of these, is it possible to integrate it into a "regular" Gnome application? If possible, I'd like to have Gnome / Gtk2 / Glade menus along the top, and probably some Gnome-style dialog boxes. It's far from a necessity, but it would help a lot.

What do default Gnome programs, like AisleRiot, use? For example, how does AisleRiot draw the cards?

---

### Post by tonyr1988 on 2007-07-12
Sorry for the double-post / bump, but I was wondering if anyone else had problems starting with GUI programming?

I feel fairly confident in my CLI programming skills. I'm sure I don't write the most efficient code, but I can usually produce code that works. When looking at super-basic GUI programs, I feel so discouraged. Nothing seems to do anything correctly, and there seems to be a drought of walkthrough tutorials.

I see all of these programs like Solitare, Mines, and Iagno, thinking they are (fairly) simple. After all, I'm 98% sure I could make a commandline program that works just like Iagno does. Furthermore, it's not even scalable, so you're talking a fixed size window. It seems so simple, yet when I "apt-get source gnome-games" and look through it, none of it makes any sense whatsoever.

Sorry for the rant, I'm just kind of lost right now. I'm not sure if I should try and learn GUI programming, or give up and refine my CLI skills, leaving the GUI to someone else.

Any advice from other people who eventually had to go over the GUI learning curve?

---

### Post by runningwithscissors on 2007-07-12
It can be a bit discouraging at first, like trying out anything sufficiently complicated for the first time. But once you get the hang of it, it's quite natural.

Now, going through sources that use GTK isn't the friendliest way to learn GUI programming.

I started writing GUI programs with Java's Swing API (which isn't very easy either) and it was a bit strange at first, but manageable. I dislike it now.

Try out some of the tutorials on gtk.org and see how it goes. (Or maybe the ones for PyGTK if you don't want C, but I haven't got a link for it right now)
[http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/)
We'll try to help if you run into any problems.

Or if you know some C++, you could try using Qt. I've heard it's a lot easier to program with, but I haven't any experience with it.


I must say though, that the planets thing you mentioned earlier is quite an ambitious project if you don't know some basic GUI programming.

---

### Post by c174 on 2007-07-12
You could have a look at GtkGlExt [http://www.k-3d.org/gtkglext/Main_Page]("http://www.k-3d.org/gtkglext/Main_Page")

This is an OpenGL extension to GTK, so you can do GUI and graphics at the same time. There is also Python bindings - even as an Ubuntu package :)  (I didn't try myself, but it says on the above link)

---

### Post by tonyr1988 on 2007-07-12
Thanks for the help. I actually semi-understand general GUI things - I've made a few (albeit simple) programs using Glade + pyGTK). I can understand event handling and all that junk (somewhat, anyway).

The problems arise when I start going to the next step: drawing things. OpenGL, et al, seems so foreign and confusing to me. On one hand, it seems like a waste of time, since I'm not getting anywhere with it. Then again, I understand that there are huge learning curves to anything worth learning :). It seems so hard to do simple things, like draw a circle (any circle) on the screen (any part of the screen). :P

---

### Post by Wybiral on 2007-07-12
Have you considered SDL?

SDL_gfx has built in circle/ellipse functions.

Unfortunately I haven't seen any raw python implementation of SDL yet.

Although, it's not too hard in OpenGL either, you just have to do it manually (PM me if you're interested).

---

### Post by tonyr1988 on 2007-07-12
I've seen SDL mentioned in some tutorials, but I didn't know it could do that. I'll definately look into it. It doesn't have to be in Python. I noticed on the SDL_gfx site that it says:

> Its is written in plain C and can be used in C++ code.

Can it be used in C code as well, or only C++? I know C, but am pretty new at C++.

---

### Post by Wybiral on 2007-07-12
It's perfect for plain C.

---

### Post by AlexThomson_NZ on 2007-07-12
Drawing with gtk on C is a bit confusing to get your head around, but is quite nifty once you get used to it.

I found the 'scribble' tutorial (a VERY simple drawing app) here ( [http://www.gtk.org/tutorial/](http://www.gtk.org/tutorial/) ) useful as a template to start from

---

### Post by skullmunky on 2007-07-14
i always suggest Processing to start learning drawing and opengl-ish 3D.  unfortunately it won't get you entirely to where you want to be - building, say, Minesweeper in a nice gtk window with buttons and such.  it's awkward for building GUI's, but awesome for programmatic drawing.

---

