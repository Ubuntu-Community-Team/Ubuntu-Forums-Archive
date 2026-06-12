---
title: "sdl rotozoom"
date: 2008-09-12
forum: Programming Talk
---

### Post by Ulrik04 on 2008-09-12
hey all :)

I'm making a game in C++/SDL, where I need to rotate some surfaces. I'm using rotozoomSurface to do it and it's working as it should, but what point does it rotate the surface around? and how do i change this? I just want a surface to be rotated around the middle.

---

### Post by cb951303 on 2008-09-12
just a quick note: if your game requires real-time rotation or zooming then I advice using hardware acceleration (i.e: opengl). Software rendering is just too slow for that purpose.

---

### Post by Ulrik04 on 2008-09-14
hmm... guess I'll have to finish learning OpenGl :P

---

