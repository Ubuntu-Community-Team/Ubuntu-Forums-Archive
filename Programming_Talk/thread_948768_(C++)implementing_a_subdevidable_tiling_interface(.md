---
title: "(C++)implementing a subdevidable tiling interface(like Blender, Vim etc)"
date: 2008-10-15
forum: Programming Talk
---

### Post by hessiess on 2008-10-15
so, im still trying to implement a 'blender like' window manager. basicky heares what im trying to think of an algorithm for:

when started there would be a single tile, which can be 'sub divided' eather horizontally or vertically. creating two tiles, these tiles can then be subdivided into 2 and so on. however I'm having trouble thinking of a way to implement this, currently my only idea is to create a class which contains two tiles, one of which can be hidden if the window isn't subdivided, and having an instance of that same class within itself, this , however dousen't seam to be passable.

any suggestions?

---

### Post by snova on 2008-10-15
How about a class that contains the direction of the split, and a list of regions?

Initially, there would be just one instance of the class. The direction can be anything at this point and the list only contains one region, which occupies the entire screen.

When you split the first time, it sets the direction appropriately and adds an element to the list. Both regions are set to half the size of the original one.

When you split again in a different direction, it's the same thing- except you use the opposite direction.

---

### Post by issih on 2008-10-15
I'd just have a class that represents the "windows" and then a class that represents a "container", both inheriting off an abstract "containable" superclass that abstracts all the drawing methods out.

The class of interest is the container class.

Set that up so it contains two pointers to objects of type "containable" and draws them when it is drawn (ideally make it so that the position of the split can be adjusted, be it horizontal or vertical and what ratio the two drawable objects occupy).

Now all you do to split a window is create a new container object add the current window's pointer as one of the new containers "containable" objects and then use the new container's pointer to replace the current window's one in the parent object.

Simple and extendable

---

