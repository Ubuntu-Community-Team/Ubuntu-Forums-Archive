---
title: "allegro and G++"
date: 2005-07-30
forum: Programming Talk
---

### Post by jasonpeinko on 2005-07-30
how do i compile a code using allegro in G++?
i know it is -lSDL for sdl (i dont quite understand SDL yet so im going back to allegro.

---

### Post by jasonpeinko on 2005-07-30
o yea and what version should i install with synaptic

---

### Post by ios_base on 2007-05-01
Hey, I just got help with compiling source with Allegro 4.2

by adding a few extra flags my code compiled nicely:

g++ file.cpp `allegro-config --cflags` `allegro-config --libs`

---

