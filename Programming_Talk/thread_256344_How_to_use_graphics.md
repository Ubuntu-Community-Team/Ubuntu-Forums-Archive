---
title: "How to use graphics"
date: 2006-09-12
forum: Programming Talk
---

### Post by pikeblodd on 2006-09-12
Hi all, Ive been taking c++ classes in college for about a year now, and I trying to learn how to develop my own games.  I know how to write the code, and compile it.  However, Im terribly overwhelmed by the different programs for developing graphics.  

Right now Im trying to just create a basic tetris clone, and Im at a loss as to what to use to draw the blocks and window Ill need for the game.

any suggestions?

---

### Post by toojays on 2006-09-12
Cairo is is really nice library for drawing graphics. The C++ library for it is called cairomm. You would use gtkmm to draw the window, and also to get a cairo context. See for install [The Drawing Area Widget](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch15.html) from the gtkmm tutorial.

Except . . . the version of gtkmm which is in Dapper does not support cairo directly. [This email](http://lists.freedesktop.org/archives/cairo/2006-March/006532.html) describes a workaround which allows you to get a cairo context with the 2.8 series of gtkmm.

---

### Post by pikeblodd on 2006-09-13
and here lies the problem, ive seen the bazillion programs out there, but what im looking for is some documentation of the code i will need to integrate any kind of graphics into my programs.  

i can write all the code but i dont know how to connect the code to the graphics and control the graphics with the code.

---

### Post by toojays on 2006-09-13
I don't understand. Here are links to the [gtkmm documentation](http://www.gtkmm.org/docs/gtkmm-2.4/docs/), the [gtkmm tutorial](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html) and the [cairomm API reference](http://cairographics.org/documentation/cairomm/reference/index.html).

Do you mean that you don't know how to use a library at all? For that, look at [Chapter 3 of the gtkmm tutorial](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/index.html), which shows how to write and build the most basic gtkmm example.

---

