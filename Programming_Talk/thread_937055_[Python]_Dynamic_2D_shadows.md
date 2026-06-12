---
title: "[Python] Dynamic 2D shadows??"
date: 2008-10-03
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-10-03
I have been looking, but found nothing yet. I want to make dynamic 2D shadows around polygons, but how??

Here is an image demonstrating what I want:
[IMG]http://images.gamedev.net/features/programming/2dsoftshadow/03HullGeneration.gif[/IMG]

So how can I do that?

---

### Post by Calmatory on 2008-10-03
Vector from light source towards every vertex which is visible to the light.
Shade the area which the vectors fill.

[http://www.gamedev.net/reference/programming/features/2dsoftshadow/](http://www.gamedev.net/reference/programming/features/2dsoftshadow/)

---

### Post by crazyfuturamanoob on 2008-10-04
But I don't understand those mathematical terms (or math very well at all).
I want an example demonstrating how the vectors would work. What are normals?
How can that normalthing work for finding is the edge either front facing, or back facing???
Could someone explain that tutorial for me a bit clearer?

---

### Post by Calmatory on 2008-10-04
In case you don't find help here, you should take a look at [DevMaster's forums](http://www.devmaster.net/forums/). At least I've got a lot of graphics related help there, even for QuickBASIC. ;)

---

### Post by crazyfuturamanoob on 2008-10-04
Ok, I managed to do the thing with only one light, but two lights?

---

