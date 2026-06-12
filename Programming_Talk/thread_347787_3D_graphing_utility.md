---
title: "3D graphing utility"
date: 2007-01-27
forum: Programming Talk
---

### Post by Houman on 2007-01-27
hi there;
I need to plot a 3D shape in ubuntu, but I havnt had any luck so far. I have tried gnuplot and octave but they dont seem to provide what I need. Although you can plot 3D line plots, surfaces and scatter plots, there is no way to visualize a closed shape (or I havnt been able to get it right). I need to visualize a tetrahedron in 3D using some utility. Is there anything you know of which might help?


regards

Houman

---

### Post by kevinlyfellow on 2007-01-27
maybe you can try blender?

---

### Post by Houman on 2007-01-27
well it is for a scientific program and i need to add more shapes at precise locations later on, i mean blender is more for modeling shapes not so much a scientific visualization utility. 
But if nothing works with gnuplot I am thinking of just drawing the thing with hand in gimp or use blender.

thanks

---

### Post by duff on 2007-01-27
I think scilab may be able to help you.  However, I've found it much easier to take the time to learn OpenGL and write my own visualiztion tools.

---

### Post by Houman on 2007-01-27
hi there;
thanks for the advice, I think this is not a visualization task, its a plotting task, in matlab I could do it with plotpoly and maple could also achieve this. I need to save this as an eps and put it on my report, I think writing an openGL app for this is a bit overkill. 

thanks, im checking out scilab ( i think its similar to octave)
regards

---

### Post by Wybiral on 2007-01-27
Writing a small opengl program probably wouldn't be too hard... 

You can do it with python too, for a small app like that glut would really simplify things.

EDIT:

Here's a really quick 3d graph I wrote in python using OpenGL, it can easily be adapted to other graphs as well...

```

#!/usr/bin/env python
 
from OpenGL.GL import *
from OpenGL.GLUT import *
from OpenGL.GLU import *
from math import *
import sys
 
angle = 0.0

# Main drawing function #
def scene():
 global angle
 glLoadIdentity();
 glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT);

 # Push graph back for better view
 glTranslatef(0.0,0.0,-50.0)

 # Rotate on X and Y axis (angle, x, y, z)
 glRotatef(angle,1.0,1.0,0.0)

 # Used to center graph
 glTranslatef(-25, 0, -25)

 glBegin(GL_POINTS)

 # Point plotting stuff
 for z in range(50):
  for x in range(50):
   y = (cos(x*0.2)+cos(z*0.2))*5
   glVertex3f(x, y, z)

 glEnd()
 angle += 0.25
 glutSwapBuffers()


# Initialize everything 
glutInit(sys.argv)
glutInitDisplayMode(GLUT_RGBA | GLUT_DOUBLE | GLUT_ALPHA | GLUT_DEPTH)
glutInitWindowSize(640, 480)
glutCreateWindow("")
glutIdleFunc(scene)
glViewport(0, 0, 640, 480)
glMatrixMode(GL_PROJECTION)
glLoadIdentity()
gluPerspective(45.0, float(640)/480, 0.1, 100.0)
glMatrixMode(GL_MODELVIEW)
glEnable(GL_DEPTH_TEST)
glutMainLoop()

```

---

### Post by jblebrun on 2007-01-27
Have you checked out [PyX]("http://pyx.sourceforge.net/")?

EDIT:
Erm, nevermind. Apparently it *doesn't* handle 3D, even though there's a pretty 3D graph on the home page.

EDIT:
Matplotlib has some sort of 3D plotting capability, but I don't know if it will help you with your polygons:
[http://www.scipy.org/Cookbook/Matplotlib/mplot3D](http://www.scipy.org/Cookbook/Matplotlib/mplot3D)

---

### Post by Houman on 2007-01-27
thank you all, 

thanks Wybiral for the suggestion. I will use your code and write something in C (im not planning on learning python just so i can have a picture of a tetrahedron :P)

thanks again

Houman

---

### Post by Wybiral on 2007-01-27
No problem, btw, I know this is in python again (not that it's hard to transfer to c/c++) but this one is slightly altered to render a sphere of varying levels of detail. It might be more helpful for what you're trying to do...

```

#!/usr/bin/env python
 
from OpenGL.GL import *
from OpenGL.GLUT import *
from OpenGL.GLU import *
from math import *
import sys
 
angle = 0.0

def spherePoint(recip, i1, i2):
 x = cos (i1*pi*2*recip) * sin (i2*pi*recip)
 y = sin (i1*pi*2*recip) * sin (i2*pi*recip)
 z = cos (i2*pi*recip)
 glVertex3f (x, y, z)

def glGenSphere(level):
 recip = float(1.0/level)
 for i1 in range(level+1):
  glBegin(GL_QUAD_STRIP)
  for i2 in range(level+1):
   spherePoint(recip, i1  , i2)
   spherePoint(recip, i1+1, i2)
  glEnd()


# Main drawing function #
def scene():
 global angle
 glLoadIdentity();
 glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT);

 # Push graph back for better view
 glTranslatef(0.0,0.0,-5.0)

 # Rotate on X and Y axis (angle, x, y, z)
 glRotatef(angle,1.0,1.0,0.0)
 glRotatef(angle,1.0,0.0,0.0)

 # Point plotting stuff
 glGenSphere(5)

 angle += 0.25
 glutSwapBuffers()


# Initialize everything 
glutInit(sys.argv)
glutInitDisplayMode(GLUT_RGBA | GLUT_DOUBLE | GLUT_ALPHA | GLUT_DEPTH)
glutInitWindowSize(640, 480)
glutCreateWindow("")
glutIdleFunc(scene)
glViewport(0, 0, 640, 480)
glMatrixMode(GL_PROJECTION)
glLoadIdentity()
gluPerspective(45.0, float(640)/480, 0.1, 100.0)
glMatrixMode(GL_MODELVIEW)
glEnable(GL_DEPTH_TEST)
glPolygonMode(GL_FRONT_AND_BACK, GL_LINE)
glutMainLoop()

```

---

### Post by Steveire on 2007-01-28
Try k3dsurf.

---

### Post by Houman on 2007-01-28
hi there;

thanks, I installed K3dsurf. But It looks like it needs a mathematical function to use for creating a surface. It doesn't seem to take vertices of a closed shape. But I will keep playing with it, I might figure something out (its very cool by the way).

thanks

---

### Post by rosencrantz on 2009-01-21
Just a update: matplotlib > 0.91 has lost 3-d plotting support. If you want to use it, you have to find (and keep) older versions of matplotlib and numpy.

---

### Post by Banter on 2010-09-05
I'm surprised nobody has mentioned Povray. [http://www.povray.org/](http://www.povray.org/)

It might be exactly what you are looking for.

---

