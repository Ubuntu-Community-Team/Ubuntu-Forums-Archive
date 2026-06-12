---
title: "Using gtk stock icons in a pygame application"
date: 2013-09-25
forum: Programming Talk
---

### Post by Tony Flury on 2013-09-25
Rather than hard coding the path to the gtk stock icons in my pygame application - I would like to be able to use the GTK stock ids within my application.

Is there anyway I can get gtk to give up the actual path of the stock icon image file at run time, so i can then load icons and blit them ?

Or is there a simple way of getting a nice gtk wrap around my pygame code.

---

### Post by Bachstelze on 2013-09-25
I don't know about Pygame but if your application doesn't otherwise depend on PyGTK, introducing a dependency just for a bunch of icons seems not a good idea to me. You would probably be better off just copying the GTK icons and making them part of your application--that's what free licenses are for.

---

### Post by Tony Flury on 2013-09-30
It turned out to be easier doing it the other way round - and then i realised i did not need pygame at all (I wasn't doing any complicated sprite stuff or collisions, so i just built a GTK interface in glade, with a drawing area - and drew into the drawing area (well into a pixmap, which then gets drawn).

---

