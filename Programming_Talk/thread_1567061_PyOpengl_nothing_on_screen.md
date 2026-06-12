---
title: "PyOpengl nothing on screen"
date: 2010-09-03
forum: Programming Talk
---

### Post by matmatmat on 2010-09-03
Hi, I've been trying to use Python + OpenGl to draw a cube:
```

from __future__ import division
from OpenGL.GL import *
from OpenGL.GLU import *
import pygame
from pygame.locals import *
from math import log,ceil

def resize(width, height):
    glViewport(0,0,width,height)
    glMatrixMode(GL_PROJECTION)
    glLoadIdentity()
    gluPerspective(60.0, float(width)/height, .1, 1000.)
    glMatrixMode(GL_MODELVIEW)
    glLoadIdentity()
    
def init():
    glEnable(GL_DEPTH_TEST)
    glShadeModel(GL_FLAT)
    glClearColor(0.0,0.0,0.0,0.0)
    glEnable(GL_TEXTURE_2D)
    glEnable(GL_COLOR_MATERIAL)
    glEnable(GL_LIGHTING)
    glEnable(GL_LIGHT0)
    glLight(GL_LIGHT0, GL_POSITION, (0,1,1,0))
    
def run():
    pygame.init()
    screen = pygame.display.set_mode((600,800), HWSURFACE|OPENGL|DOUBLEBUF)
    resize(600,800)
    init()
    t = Texture("Cursor_flying_away.png")
    while True:
        for event in pygame.event.get():
            if event.type == QUIT:
                return
        glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT)                
        #glClear()
        #t.draw()
        glBegin(GL_QUADS)
        glColor(1.0,0.0,0.0)
        glVertex(100.0,100.0,0.0)
        glVertex(200.0,100.0,0.0)
        glVertex(200.0,200.0,0.0)
        glVertex(100.0,200.0,0.0)
        glEnd()
        pygame.display.flip()
        
def next_power_of_2(size):
    return 2 ** ceil(log(size,2))

if __name__ == '__main__':
    run()

```

When I run this code the cube is not displayed!

---

### Post by Wybiral on 2010-09-03
It's because your quad is somewhere floating around in outer-space (off the screen).

Before the glBegin line, add this to translate your viewport to make it more within the viewport:
```

        glLoadIdentity()
        glTranslate(-150.0, -150.0, -500)

```
But, my guess is that you're wanting to do some 2d rendering? OpenGL's coordinates aren't pixel coordinates, they're points in 3d. If you want 2d, you have to set the projection matrix to do so. Something like this in your resize function (instead of the 3d projection you have right now):
```

glMatrixMode(GL_PROJECTION)
glLoadIdentity()
glOrtho(0, width, height, 0, -1, 1)
glMatrixMode(GL_MODELVIEW)
glLoadIdentity()

```
Then you wont need to translate it into the viewport.

---

