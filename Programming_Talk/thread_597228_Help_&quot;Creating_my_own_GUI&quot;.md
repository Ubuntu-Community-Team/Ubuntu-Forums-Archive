---
title: "Help &quot;Creating my own GUI&quot;"
date: 2007-10-30
forum: Programming Talk
---

### Post by jordigasau on 2007-10-30
Hello,

I'm willing to develop an application that shows the spectrum in real-time of an audio signal (Mic or Line-in). 

I'm quite new in developing GUI in linux and I would like to ask you for some help.

My idea is to create my own widget with a 2D plot of the spectrum. Because is in real-time, I need to update the plot every X miliseconds. 

I have good image processing skills so my first idea was to create an image every X miliseconds and update the image but I would like to ask you if anyone knows a good tutorial so I can understand the best way to achieve the real-time plot. I do believe that I can use the Graphics card resources to make this process more efficient.

My idea is to create a control or widget that shows the spectrum in the background. Then, I would like to add other parameters in the gui such as the Sound Pressure Level (a number), and a option where the user can place the mouse in the spectrum area and a couple of values ( Amplitude and Frequency) apear near the cursor.

Should I use Open GL, MESA, GTK+,..? I'm a bit confused right now so a bit of help could be excellent!

Thanks very much!

:guitar:

---

### Post by AlexThomson_NZ on 2007-10-30
I would use Glade + GTK for this, but rather than make my own Widget, would probably just use a Pixbuff and draw on as part of the program

As a good first step, it may be best to go through the 'official' GTK tutorial which has a simple drawing program (there's quite a bit to learn before doing anything too tricky).  Good luck with the project!  As a bit of a sound-engineering buff myself I can see a good benefit in programs like this :)

---

### Post by Wybiral on 2007-10-30
Do you need other widgets like text input / buttons? If not, then I would definitely suggest [SDL]("http://libsdl.org/") / [OpenGL]("http://nehe.gamedev.net/") or a combination of the two. Either will give you access to the real-time graphics primitives that you're looking for. For SDL, I would especially recommend SDL_gfx. In fact, [here's]("http://www.aaroncox.net/tutorials/2dtutorials/sdlshapes.html") a good tutorial.

There is also [GtkGlExt]("http://www.k-3d.org/gtkglext/Main_Page") if you end up using GTK that will allow you to use OpenGL in a normal GUI. And also [cairo]("http://cairographics.org/").

---

### Post by AlexThomson_NZ on 2007-10-30
I suspect he will need other widgets (he hints that he needs at least a mic/line selection option).  Good suggestion re: GtkGlExt- probably easier than using pixbuf/canvas for a beginner, and I assume it inherits mouse events(?- I haven't used it)

---

