---
title: "Open GL and Python2-7 issue in Ubuntu 12.04 (x86_64)"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by farrington on 2013-03-27
Hello.  For some reason when I close the OpenGL canvas("screen"), my python IDLE crashes. This is the code:

 import sys
import OpenGL

from OpenGL.GL import *     
from OpenGL.GLU import *    
from OpenGL.GLUT import *

Angle = 0
Incr = 1

def display():
      global Angle
      global Incr
      glClear(GL_COLOR_BUFFER_BIT)
      glLoadIdentity()
      glRotated(Angle,0,1,0)
      glBegin(GL_TRIANGLES) 
      glColor3f(1,0,0)
      glVertex3f(-1,0,0)
      glColor3f(0,1,0)
      glVertex3f(1,0,0)
      glColor3f(0,0,1)
      glVertex3f(0,1,0)
      glEnd()
      Angle = Angle + Incr
      glFlush()
      glutSwapBuffers()

def keyHandler(Key, MouseX, MouseY):
      global Incr
      if Key == 'f' or Key == 'F':
            print "Speeding Up"
            Incr = Incr + 1
      elif Key == 's' or Key == 'S':
            if Incr == 0:
                  print "Stopped"
            else:
                  print "Slowing Down"
                  Incr = Incr - 1
      elif Key == 'q' or Key == 'Q':
            print "Bye"
            sys.exit()
      else:
            print "Invalid Key ",Key

def timer(Dummy):
      glutPostRedisplay()
      glutTimerFunc(30,timer,0)

glutInit(sys.argv)
glutInitDisplayMode(GLUT_DOUBLE|GLUT_RGB)
glutCreateWindow("PyOpenGL Demo")
glutDisplayFunc(display)
glutKeyboardFunc(keyHandler)
glutTimerFunc(0,timer,0)

glMatrixMode(GL_PROJECTION)
glLoadIdentity()
glFrustum(-1,1,-1,1,1,3)
glTranslated(0,0,-2)
glMatrixMode(GL_MODELVIEW)
glutMainLoop()

---

