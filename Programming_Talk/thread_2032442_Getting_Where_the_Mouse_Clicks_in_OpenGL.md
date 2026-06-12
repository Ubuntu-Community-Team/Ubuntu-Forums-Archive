---
title: "Getting Where the Mouse Clicks in OpenGL?"
date: 2012-07-23
forum: Programming Talk
---

### Post by theopfor on 2012-07-23
Hello, I am making a OpenGL game in C++ and it relies on where the mouse clicks in the 3D space for movement, placing objects, and probably other stuff too. I can't seem to figure out how to do this though. How do I find the coordinates where a user clicks?

---

### Post by the_unforgiven on 2012-07-24
> **theopfor said:**
> Hello, I am making a OpenGL game in C++ and it relies on where the mouse clicks in the 3D space for movement, placing objects, and probably other stuff too. I can't seem to figure out how to do this though. How do I find the coordinates where a user clicks?
You could use [glutMouseFunc()]("http://www.opengl.org/resources/libraries/glut/spec3/node50.html") to set the callbacks.

Here is a GLUT tutorial for mouse events:
[http://programming-technique.blogspot.in/2012/01/glut-tutorial-how-to-detect-mouse-click.html](http://programming-technique.blogspot.in/2012/01/glut-tutorial-how-to-detect-mouse-click.html)

---

### Post by Hetepeperfan on 2012-07-24
Keep in mind that opengl is only for the graphics, the windowing library you are using can provide you with information where your user clicks within your window. (but you'll probably end up with a 2D coordinate...)

cheers

---

### Post by theopfor on 2012-07-24
> **the_unforgiven said:**
> You could use [glutMouseFunc()]("http://www.opengl.org/resources/libraries/glut/spec3/node50.html") to set the callbacks.

Here is a GLUT tutorial for mouse events:
[http://programming-technique.blogspot.in/2012/01/glut-tutorial-how-to-detect-mouse-click.html](http://programming-technique.blogspot.in/2012/01/glut-tutorial-how-to-detect-mouse-click.html)

I think that might be what I need, thanks!

---

