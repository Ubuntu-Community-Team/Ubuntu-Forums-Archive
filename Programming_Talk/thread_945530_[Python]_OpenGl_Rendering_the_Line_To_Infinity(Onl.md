---
title: "[Python] OpenGl Rendering the Line To Infinity(Only supposed to go to (20, 20)"
date: 2008-10-12
forum: Programming Talk
---

### Post by xelapond on 2008-10-12
Hello, 

Experimenting with PyGlet OpenGl rendering, and I wrote this simple script.  What it is supposed to do is render a line from (0, 0) to (20, 20).  The goes off the screen though, and I can assume goes for a much longer distance(infinity?).

Here is the code:[PHP]import pyglet
from pyglet.gl import *

def drawLine(points, color=(1, 1, 1)):
    p1, p2 = points[0], points[1]
    glLineWidth (10.0)
    glColor3f(*color)
    glBegin(GL_LINES)
    glVertex2f( p1[0], p1[1] )
    glVertex2f( p2[0], p2[1] )
    glEnd()
    glLineWidth (1.0)


win = pyglet.window.Window(600, 600)

while 1:
    win.clear()
    drawLine(((0, 0), (20, 20)), (.5, .5, 1))
    win.flip()
[/PHP]

Anyone have any idea what it is doing?

---

