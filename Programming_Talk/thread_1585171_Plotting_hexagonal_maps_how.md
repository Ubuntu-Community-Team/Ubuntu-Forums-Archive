---
title: "Plotting hexagonal maps: how?"
date: 2010-09-30
forum: Programming Talk
---

### Post by erupter on 2010-09-30
I'm developing a program interfaced with player/stage.
It creates an hexagonal map, arranged in a standard rectangular matrix (odd rows spaced half-cell to the right).
Now i need to draw these maps somehow.
Is there any EASY way?
I mean I am not familiar with 2d or 3d libraries or cpp.
Any hint?

---

### Post by erupter on 2010-09-30
Ok i admit it's not something you do everyday, so it's difficult.

I figured i could make bitmap and tile it around, changing colors, luminosity and the like to suit the local cell.
I could replicate this single bitmap over and over, thus making an image.
Is there any library able to do such things?
Maybe this is simpler...

---

### Post by saulgoode on 2010-09-30
If I understand correctly, you can just create a "cell" consisting of:

[IMG]http://flashingtwelve.brickfilms.com/GIMP/Patterns/hexagon.png[/IMG]

and then tile it to fill your region.

---

### Post by erupter on 2010-10-01
Yes well the actual shape of the tile is not important.
What's important is how do i actually do it.
I don't know any graphic library, i don't know if there are any compatible with C sources (i'm totally unfamiliar with c++).
Can you suggest anything?

---

