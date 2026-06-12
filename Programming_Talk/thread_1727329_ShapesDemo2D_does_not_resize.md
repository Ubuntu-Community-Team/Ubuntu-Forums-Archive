---
title: "ShapesDemo2D does not resize"
date: 2011-04-12
forum: Programming Talk
---

### Post by worldsayshi on 2011-04-12
In this java 2d graphics demo:
[http://download.oracle.com/javase/tutorial/2d/geometry/examples/ShapesDemo2D.java](http://download.oracle.com/javase/tutorial/2d/geometry/examples/ShapesDemo2D.java)

When I resize the window, the shapes follow but they are only drawn on the same rectangle as before so that If I maximize the window I can only see a small part of the upper left straight line.

-> Is this a bug in open-jdk or is there a way to modify the code so that drawing will be done over the whole pane? 

I'm not that well experienced on swing/java graphics in general. I've spent some time trying to find answer to this by now anyway. I will try to switch to Sun's java in eclipse now..

---

### Post by worldsayshi on 2011-04-12
This does not happen when using java-6-sun. So, a openjdk bug it is.

---

