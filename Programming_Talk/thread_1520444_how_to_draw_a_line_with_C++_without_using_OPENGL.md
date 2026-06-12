---
title: "how to draw a line with C++ without using OPENGL?"
date: 2010-06-29
forum: Programming Talk
---

### Post by bahador.saket on 2010-06-29
Dear all

I am going to write the text editor.
I want to make it more interested by using some graphical shapes.
how can I draw a line or some shapes without using OpenGL? 

Cheers,
Bahador

(I am beginner)

---

### Post by Tahakki on 2010-06-29
SDL, possibly?

---

### Post by Yes on 2010-06-29
If you just need simple shapes like lines or circles, drawing them directly with X will probably work.

---

### Post by phrostbyte on 2010-06-29
In Xlib the function is [XDrawLine]("http://tronche.com/gui/x/xlib/graphics/drawing/XDrawLine.html").

You can also use Qt or Cario for portability.

---

### Post by Tahakki on 2010-06-30
Cairo is very nice, and easy to extend into Clutter if you want animations and things.

---

### Post by bahador.saket on 2010-06-30
Tnx for your helps.

> 
In Xlib the function is [XDrawLine]("http://tronche.com/gui/x/xlib/graphics/drawing/XDrawLine.html").

You can also use Qt or Cario for portability.



Can you please bring the example of how to use XDrawLine()?

Cheers,
Bahador

---

### Post by bahador.saket on 2010-06-30
I am trying to use cario, I have run a program in following link.

[http://library.gnome.org/devel/gtkmm-tutorial/stable/sec-cairo-drawing-lines.html.en](http://library.gnome.org/devel/gtkmm-tutorial/stable/sec-cairo-drawing-lines.html.en)

but my editor (codeblock) can not recognize #include <gtkmm/drawingarea.h> 
what should i do?

---

### Post by Yes on 2010-06-30
Here's a good tutorial for using Xlib: [http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html#preface](http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html#preface).  Search for XDrawLine to get to the bit about that.

You have gtkmm installed, right?

---

### Post by bahador.saket on 2010-07-02
tnx guys, I could solve my problem with some things like setconsole........() functions.

---

### Post by bstree on 2010-09-05
hi,

i created window with menu and drawing area in a v-box.

i am trying to draw a line on with cairo but the line have the offset of the menu.

how do i fix this[FONT=Arial]

[/FONT]

---

