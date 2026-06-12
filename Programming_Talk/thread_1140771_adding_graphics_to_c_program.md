---
title: "adding graphics to c program"
date: 2009-04-27
forum: Programming Talk
---

### Post by sherlock domed on 2009-04-27
Can anyone help me add graphics to my c program?

i'm making a queue of a stop sign and i need to add cars to it, for a graphical representation.

Thanks

---

### Post by jinksys on 2009-04-29
When you say 'adding graphics', do you mean implementing a gui?  What OS is this program running on?

---

### Post by blingo on 2009-04-30
Graphics, is a big subject, You really should give us much more detail.

Also you may also consider using some other tools rather than just plain C, that is Flash, etc', which may be much easier.

With that said, on C 
If you want graphical user interfaces, etc:

[http://www.gtk.org/screenshots.html](http://www.gtk.org/screenshots.html)

If you want game like graphics, animation:

you can use the highly known SDL library, you can install it with synaptic, look for 'Simple DirectMedia Layer development files'

One thing to consider is whether to use plain .bmp files, or maybe openGl.

This is the site
[http://www.libsdl.org/](http://www.libsdl.org/)
look at tutorials.

---

### Post by hessiess on 2009-04-30
If you do use SDL, I highly recommend using OpenGL as the renderer as it allows alpha blitting(anti-aliasing), scaling and rotation with very little performance loss, and is normally a lot faster than SDLs software blits even if these features aren't required.

---

