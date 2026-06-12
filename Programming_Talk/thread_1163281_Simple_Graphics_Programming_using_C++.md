---
title: "Simple Graphics Programming using C++"
date: 2009-05-18
forum: Programming Talk
---

### Post by TKC747 on 2009-05-18
There is a post from 2007 regarding programming Graphics in ubuntu.  It left me a bit confused.  

I am interested in doing computer simulation of physical systems, which requires plotting pixels to get a graph, like a sine wave, output from a c or c++ program.  How do you open up a window, plot the function and exit? What do I install to be able to open up a window and plot points?  

The old post mentions things like openGL, Cairo, qt and GTK+. I have looked on wikipedia for what these technologies are and I am still confused. Can someone explain what I need to do and what these software technologies are?

Thanks in advance

---

### Post by C-- on 2009-05-18
> **TKC747 said:**
> There is a post from 2007 regarding programming Graphics in ubuntu.  It left me a bit confused.  

I am interested in doing computer simulation of physical systems, which requires plotting pixels to get a graph, like a sine wave, output from a c or c++ program.  How do you open up a window, plot the function and exit? What do I install to be able to open up a window and plot points?  

The old post mentions things like openGL, Cairo, qt and GTK+. I have looked on wikipedia for what these technologies are and I am still confused. Can someone explain what I need to do and what these software technologies are?

Thanks in advance

OpenGL is a specification for which hardware vendors create implementations that allow for graphics acceleration. It is used for 2D and 3D graphics rendering (i.e. taking polygons and converting them to pixels). It is basically the equivalent of Windows' DirectX. If you wanted to make a game, a 3D simulation, and so forth, you would use OpenGL.

Cairo is a vector graphics library. Vector graphics refers to graphics drawn by mathematical equations, as opposed to arrays of pixels (raster graphics). Cairo is used for 2D graphics, and is used to draw widgets in Gtk+. It has no concept of what a "button" is, rather it draws and fills rectangles, etc. to give the appearance of a button.

Gtk+ is a widget toolkit implemented in C but for which a multitude of language wrappers exist. You use Gtk+ to build graphical user interfaces with buttons, windows, scroll bars, etc. Widgets emit "events" or "signals" when a user interacts with them to which functions can be connected to perform some functionality. Other toolkits include wxWidgets, Qt, and Swing.

In short, OpenGL is best used for rendering polygons, Cairo is best used for rendering 2D shapes/animations, and Gtk+ is a widget toolkit that encapsulates rendered graphics with "events" used in GUI development, such as a rectangle signifying a "button" with a "clicked" event.

It sounds like in your case, you would want to pick a widget toolkit, such as Gtk+, to set up your window. Inside your window, you would embed a custom widget that you have to write that is rendered with Cairo (or whatever the rendering engine is for your toolkit) to produce the graph.

---

### Post by gtr32 on 2009-05-18
Double post

---

### Post by gtr32 on 2009-05-18
You would need one of OpenGL (Open Graphics Library) libraries to use OpenGL. glut, freeglut, sdl etc. The functions should be same or very similar to OpenGL calls.

Lets say you get sdl:

```
sudo apt-get install g++
sudo apt-get install libsdl1.2-dev libsdl-ttf2.0-dev libglew1.5-dev
```

Follow one of the instruction on how to set up a display, there should be plenty out there. For plot, you could do something like (partly taken from [F.S. Hill's OpenGL book]("http://www.prenhall.com/hill_kelley/")):

```

glClear(GL_COLOR_BUFFER_BIT);
glBegin(GL_POINTS);
for (GLdouble x = 0; x < 1.0; x += 0.001);
{
   GLdouble func = exp(-x) * cos( 2 * PI * x);
   glVertex2d(640 * x, 240 * func + 240); // for 640x480 screen
}
glEnd();
glFlush();

```

---

### Post by TKC747 on 2009-05-18
Thank you guys, that clears things up enough for me to get started:D

---

### Post by C-- on 2009-05-18
You probably won't need OpenGL for what you want to do, but if you want to learn about it here are some video tutorials:

[http://www.videotutorialsrock.com/opengl_tutorial/basics/home.php](http://www.videotutorialsrock.com/opengl_tutorial/basics/home.php)

---

### Post by skullmunky on 2009-05-20
also have some fun with Processing ([www.processing.org](www.processing.org)), which is terrific for doing this kind of stuff quickly (until you have a lot of particles, that is).

---

### Post by yanom on 2010-07-07
> **skullmunky said:**
> also have some fun with Processing ([www.processing.org](www.processing.org)), which is terrific for doing this kind of stuff quickly (until you have a lot of particles, that is).

is Processing any good for game programming in 2d?

---

