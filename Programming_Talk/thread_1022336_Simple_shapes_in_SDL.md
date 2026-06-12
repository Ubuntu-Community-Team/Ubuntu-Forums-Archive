---
title: "Simple shapes in SDL"
date: 2008-12-26
forum: Programming Talk
---

### Post by happysmileman on 2008-12-26
Probably a stupid question but is there a way to draw simple shapes (circles are what I have in mind) in SDL?
Tutorials I've seen only show importing images and displaying them.
Looking through the API I find SDL_FillRect for rectangles but no way to draw a circle.

Am I expected to draw a circle and then load it as an image and display it or am I just missing the function to do this?

Oh and I've googled and found people advising to use OpenGL for this, or SDL-draw, but  I assumed there must be a way to do this in pure SDL

---

### Post by kjohansen on 2008-12-26
here is someone that has hacked up there own circle.  it appears there is no built in circle.

[http://lists.libsdl.org/pipermail/sdl-libsdl.org/2002-January/022651.html](http://lists.libsdl.org/pipermail/sdl-libsdl.org/2002-January/022651.html)

---

### Post by happysmileman on 2008-12-26
Well I'll probably just used QPainter instead then, I'm just messing around with some Physics and Applied Maths for school now anyway, not making anything specific, I chose SDL without actually looking at what it actually does :S.

---

### Post by wmcbrine on 2008-12-27
SDL is very focused on blitting. The only thing you might call a drawing primitive is colored rectangles. Of course, you can build anything else out of that, since the smallest possible rectangle is one pixel... Anyway, it's not part of standard SDL, but there drawing libraries built on SDL. From the repos, try libsdl-gfx.

---

