---
title: "Basic GTK+ Drawing commands."
date: 2009-02-28
forum: Programming Talk
---

### Post by Coder543 on 2009-02-28
Hello, I was wondering if (using C or C++) I could be given some examples of how to draw lines, rectangles, JPEGs, and text onto an empty window. As part of the above, how do I implement the paint responder. (I am not inexperienced with programming, I am just not familiar with GTK+.)

I will be using GTK+ as the basis for a project I plan on writing for a science fair. Due to the classes I am taking in school next year, I must all but finish this project before the end of the summer.

Samples I need:
use of Paint Responder Function
Drawing Lines
Drawing Rectangles
Drawing Text
Drawing Images.

I would *greatly* appreciate it if links could be provided, or source code be pasted here. I *do* know about the GTK links in the stickies. I think, however, that I would get better material from this thread.

---

### Post by Can+~ on 2009-02-28
You mean using the Gtk Drawin Area Widget?

Personally, I think you would be better off with [Cairo]("http://cairographics.org/samples/").

---

### Post by kknd on 2009-02-28
New version of GTK+ (> = 2 . 8 ) uses cairo for the drawings. [http://zetcode.com/tutorials/cairographicstutorial/](http://zetcode.com/tutorials/cairographicstutorial/)

---

### Post by cph05a on 2009-03-01
Cairo works great, but to answer the question, your basic drawing functions for GTK+ are here:

[http://library.gnome.org/devel/gdk/stable/](http://library.gnome.org/devel/gdk/stable/)

---

