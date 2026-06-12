---
title: "C/C++ and Game Development Libraries"
date: 2011-02-15
forum: Programming Talk
---

### Post by nair on 2011-02-15
The following questions pertain strictly to the topics of the C/C++ languages and game development libraries.

 What are some of the similarities and differences (or strengths and weaknesses) of the major developer libraries out there that could be used for game development (for both 2D and 3D games).  Are libraries like GTK+ and Qt for simple, generic GUI development that would not generally be associated with game development?  Are other libraries like SDL, OpenGL, Direct3D, and Allegro more robust and therefore recommended over GTK+/Qt for game development?  Should some combination of these libraries be used for game development, depending on the complexity of the GUI?

 I am asking these questions as a very novice programmer, relatively unfamiliar with C++ and completely ignorant as to how to make a GUI-based application from scratch.  I am interested in making the simplest game possible, something along the lines of Pacman or Tetris or Tic-Tac-Toe--strictly for the purposes of learning how to program a game that has a GUI.  I do not care what platform is used or that this game is cross-platform; I only care that I am writing this game in C++.

Regardless of my individual ambitions, however, for the purposes of this thread, I am mainly interested in comparing all of the libraries that could be used for a development task comparable to the one I seek to undertake.

---

### Post by fct on 2011-02-16
Qt and GTK+ provide an extensive framework that isn't focused on game development and thus you'll end up messing with code you normally wouldn't care about (for example UI layout behavior on window size changes) and a vast array of controls you'll probably never use (progress bars, tooltips, treeviews...).

SDL, Allegro, etc. are focused on games and multimedia apps. The API is smaller, but all you'll need for game development is most surely already there. You can also expect easier access to specific optimizations, like double buffering. Also, the footprint of the library in memory is smaller.

About combining different libraries, it's a choice to go by case-by-case. For example, to overcome limitations: SDL by default provides enough functions for 2D rendering, but if you want the fastest hardware acceleration and/or decent 3D graphics, you'd better use OpenGL functions from SDL (this is the official recommended choice).

Another good example is level editors: you might be developing some platformer using SDL, but if you want a level editor with a canvas, tile palette, toolbar, etc... it'll be faster to learn and use a GUI toolkit rather than writing your own.

---

### Post by nair on 2011-02-16
If Qt and GTK+ are "bigger" than Allegro, SDL, OpenGL, (I'm assuming you are referring to the actual size of the libraries, not their levels of popularity), is it fair to say that they are generally more powerful libraries for game development?  It sounds like, from your description, that they require the programmer to do more work, but they offer more control and power, even in the area of game development where the typical game libraries dominate.

---

### Post by worksofcraft on 2011-02-16
> **nair said:**
> If Qt and GTK+ are "bigger" than Allegro, SDL, OpenGL, (I'm assuming you are referring to the actual size of the libraries, not their levels of popularity), is it fair to say that they are generally more powerful libraries for game development?  It sounds like, from your description, that they require the programmer to do more work, but they offer more control and power, even in the area of game development where the typical game libraries dominate.

Gtk and Qt have lots of stuff you would not use in the actual game. Like all the GUI widgets and handling of international character strings etcetera. The [Qt tutorial]("http://doc.trolltech.com/4.3/tutorial.html") actually builds up quite a cute cannon game so it's not a bad place to start. The actual graphics facilities in Gtk are implemented as a library known as [Cairo]("http://cairographics.org/manual/") which only as very primitive capabilities IMHO. IDK if either Qt or Gtk have much in the way of sound capabilities.

---

### Post by Vaphell on 2011-02-16
bigger is not always better. Games are an area of programming where performance is king - leaner, tailored for the specific purpose libraries are better than the 'everything and the kitchen sink' scope of generalist frameworks like Qt.

---

