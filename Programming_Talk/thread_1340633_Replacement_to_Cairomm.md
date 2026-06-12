---
title: "Replacement to Cairomm"
date: 2009-11-28
forum: Programming Talk
---

### Post by talguy on 2009-11-28
Over the past week I have had a lot of free time on my hands since schools been pretty slow.  I want back and took a look at my EE senior project and decided to redo the majority of stuff we designed over the past year.  Basically what we did was designed an embedded system that monitored the sensors around your vehicle which would return the values back to a central computer to be drawn to the screen.  We also interfaced with the vehicles OBD port using a serial/USB to the central computer.  To draw the graphics to the screen we used Cairomm and Gtkmm. I found cairo to be to slow when drawing each frame even when reading the data from a simulated text file.  Every time I would redraw each frame completely cause when I would clip one gauge off the screen and redraw just the gauge I found the graphics to be choppy.  the system was not tested on a bad *** machine basically our plat consisted of a 1.6GHz single core laptop running Ubuntu 8.10.  So long story short is there another C++ vector graphics library that draws faster than Cairomm that is able to draw png images to the screen also since we implemented a skinable system.  Also I would perfer to stay away from OpenGL since I can't really figure out how to make a skinable system with it.

Also I was thinking that I should compile my own Linux system that is just running our App so that it has more resource dedicated to our application vs running a full desktop.  I never compiled my own linux system and some pointers or tips about this idea would be most appreciated.

---

### Post by froggyswamp on 2009-11-29
I'm not an expert but I think you should take a closer look at your rendering tactics, whether you're not doing duplicate computations, making sure you're using double buffering, something else..
I mean it's usually the programmer to blame when the animation is not smooth or so (talking from my own experience) rather than the api.

---

### Post by froggyswamp on 2009-11-29
Anyway, if you're sure Cairo is bad try this:
[http://www.xaraxtreme.org/about-performance.html](http://www.xaraxtreme.org/about-performance.html)

---

### Post by talguy on 2009-11-29
froggyswamp, I just took a look at xarax and it would work just that I would have to pull out the library i need from its source.  You also could be correct about it being the programmer I think our bottle neck might be at the datalogger since it is communicating with the computer over serial

---

