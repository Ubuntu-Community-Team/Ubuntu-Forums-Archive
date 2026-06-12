---
title: "PyOpenGL"
date: 2008-11-17
forum: Programming Talk
---

### Post by imfromwales on 2008-11-17
I am using DrPython to create PyOpenGL programs. I wrote a program and it worked fine in DrPython, untill i upgraded to Ubuntu 8.10. 

I have re-installed PyOpenGL by downloading and installing it from here [http://packages.ubuntu.com/hardy/python-opengl](http://packages.ubuntu.com/hardy/python-opengl) and when i try to run the program it does not come up with any errors, as if PyOpenGL was not installed, but nothing happens! 

Please help!

---

### Post by crazyfuturamanoob on 2008-11-17
> **imfromwales said:**
> I am using DrPython to create PyOpenGL programs. I wrote a program and it worked fine in DrPython, untill i upgraded to Ubuntu 8.10. 

I have re-installed PyOpenGL by downloading and installing it from here [http://packages.ubuntu.com/hardy/python-opengl](http://packages.ubuntu.com/hardy/python-opengl) and when i try to run the program it does not come up with any errors, as if PyOpenGL was not installed, but nothing happens! 

Please help!

Perhaps the problem is with your code, not with PyOpenGL? Could you possible post the code here?

---

### Post by imfromwales on 2008-11-17
It cant be the code...It works on the university computers and also on my system before i upgraded... but below is the code.

```
#!/usr/bin/env python
####################################################
# Created by: Antonio Morote - sc07am@leeds.ac.uk  #
# Date      : November 2008                        #
# Version   : 1.0                                  #
####################################################
from OpenGL.GLUT import *
from OpenGL.GLU import *
from OpenGL.GL import *
import sys, math, random

def circle(x, y, radius, smoothness):
  ''' Draw a circle.
   Parameters - x - x co-ordinate
                y - y co-ordinate
                radius - radius of the circle
                smoothness - number of triangles to use'''

  glBegin(GL_TRIANGLE_FAN)
  glColor3f(1.0, 0.0, 0.0)
  for i in range(0, smoothness):    
    angle = i * math.pi * 2.0 / smoothness
    glVertex2f(x + radius * math.cos(angle), y + radius * math.sin(angle))
  glEnd() 
    
def tick(tock):
   '''Redraw the scene every 25ms''' 
   global msec
   glutTimerFunc(msec, tick,0)   
   glutPostRedisplay() # Redraw the window 

def createsquare():
  '''Draws a cube'''
  global colour 
  # Create top square
  glColor3f(colour, 0.9, 0.6) 
  glBegin(GL_POLYGON)
  glVertex2f(-0.14, 0.05)
  glVertex2f(0.0, 0.15)
  glVertex2f(0.14, 0.05)
  glVertex2f(0.0, -0.05)
  glEnd()
  # Create left square
  glColor3f(0.75, 0.8, 0.0)
  glBegin(GL_POLYGON)
  glVertex2f(-0.14, -0.1)
  glVertex2f(-0.14, 0.05)
  glVertex2f(0.0, -0.05)
  glVertex2f(0.0, -0.2)
  glEnd()
  glColor3f(0.5, 0.6, 0.0)# Create right square
  glBegin(GL_POLYGON)
  glVertex2f(0.0, -0.05)
  glVertex2f(0.14, 0.05)
  glVertex2f(0.14, -0.1)
  glVertex2f(0.0, -0.2)
  glEnd()
  # Create lines on the cubes
  glColor3f(0.9, 0.9, 0.6) 
  glBegin(GL_LINES)
  glVertex2f(-0.14, 0.045)
  glVertex2f(0.0, -0.05)
  glVertex2f(0.0, -0.05)
  glVertex2f(0.0, -0.2)
  glEnd()

def drawsquares(n):
    '''Draw n cubes side-byside'''
    countsquares = 0
    while countsquares < n:
      glTranslatef(0.28,0.0,0.0)# Make it horizontal alligenment
      createsquare()
      countsquares += 1
    glTranslatef(0.14,0.25,0.0)
    glTranslatef(-0.28*n,0.0,0.0)
    
def animate():
  global updown
  global x
  global y
  global top
  global bottom
  global direction
  global copydirection
  global level
  global colour
  speed = (top-y) / 10 + 0.01

  if updown == 0: # Ball is moving downwards
    if direction == 1: 
        circle(x, y, 0.1, 34)
        x += 0.0040 # Change x co-ordinate by 0.01 every frame 
        y -= speed # Decrease y by the speed
        if y <= bottom:
            updown = 1 # Make ball bounce upwards
            direction = random.randint(0,1) # Change direction randomly
            copydirection = direction # Copy this random direction so it can be used later
            bottom -= 0.257 # Change location of top and bottom boundaries
            top -= 0.257
            level += 1 # The ball has bounced down another level
        if level == 13: 
           direction = 2 # change the direction so ball bounces off pyramid
    elif direction == 0:
       circle(x, y, 0.1, 34)
       x -= 0.0040
       y -= speed          
       if y <= bottom:
           updown = 1 
           direction = random.randint(0,1)
           copydirection = direction
           bottom -=0.257
           top -= 0.257
           level += 1
       if level == 13: # If the ball has hit the bottom level
            direction = 2 
    elif direction == 2: # The ball is to bounce off the pyramid
        circle(x, y, 0.1, 34)
        x -= 0.0040
        y -= speed 
  if updown == 1: # Ball is moving upwards          
    if direction == 0:
        circle(x, y, 0.1, 34)
        x -= 0.0040
        y += speed
        if y >= top:
            updown = 0 
            direction = copydirection 
    elif direction == 1:
        circle(x, y, 0.1, 34)
        x += 0.0040
        y += speed 
        if y >= top:
            updown = 0 
            direction = 1
    elif direction == 2: # The ball is to bounce off the pyramid
        circle(x, y, 0.1, 34)
        x -= 0.0040
        y -= speed 
    
def reshape(w, h):
  '''Called by OpenGL when the windoskew an objectw is first created and 
     each time the window is resized.
    
    Parameters - w - current width of the window
                 h - current height of the window'''                
  glMatrixMode(GL_PROJECTION)
  glLoadIdentity()
  if (w <= h):
    gluOrtho2D(-2.0, 2.0, -2.0 * h / w, 2.0 * h / w)
  else:
    gluOrtho2D(-2.0 * w / h, 2.0 * w / h, -2.0, 2.0)

  # Define a viewport that maps the world to the whole window.
  glViewport(0, 0, w, h)
  glMatrixMode(GL_MODELVIEW)
        
def keyPressed(*args):
    ''' Checks if any buttons have been pressed''' 
    global msec
    global already_pressedS
    global already_pressedQ
    if args[0] == '\163' and already_pressedS == False: # 's' button
      msec = 25 
      glutTimerFunc(msec, tick,0)
      already_pressedS = True
    if args[0] == '\033':  # 'esc' button
        sys.exit()

def display():
  ''' Called by OpenGL each time it needs to redraw the screen''' 
  glClear(GL_COLOR_BUFFER_BIT)  # Clear the window
  glMatrixMode(GL_MODELVIEW)
  glLoadIdentity()
  glTranslatef(-1.80,-1.3,0.0) # Move first cube to correct place on screen

  n = 12
  while n > 0: # Loop through levels of pyramid drawing n squares
    drawsquares(n)
    n -= 1 
    
  animate() # Make the ball bounce   
  glutKeyboardFunc(keyPressed) # Checks for key strokes
  glutSwapBuffers() 
  glFlush() # Flush the buffer drawing contents to the screen

def setup():
  '''Sets up the global variables, background colour and the tick function'''
  global updown # State of direction of the ball (up-down)
  updown = 0  
  global y # Original position of the circle
  y = 0.5  
  global x # The original position of the ball in x direction
  x = 0.06
  global top # The limit the ball should boune upwards to
  top = 0.5
  global bottom # The limit the ball should bounce downwards to
  bottom = 0.0
  global direction # The direction the ball is moving (left-right)
  direction = 1 
  global colour # The colour of the top square of each cube
  colour = 0.9
  global level # Initial level of pyramid the ball is on
  level = 0
  global msec # Screen refresh rate
  msec = "stationary"
  global already_pressedS # Has the 's' key already been pressed?
  already_pressedS = False

  glClear(GL_COLOR_BUFFER_BIT)
  glMatrixMode(GL_MODELVIEW)
  glLoadIdentity() 
  tick(0) #Run the timer
  
glutInit(sys.argv) # Initialise OpenGL.
glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGB) # Use double buffering an RGB

# Create the window.
glutInitWindowSize(600, 600)
glutInitWindowPosition(random.randint(0,1200),random.randint(0,360)) # Randomly position window
glutCreateWindow('sc07am')

# Set callback functions.
glutReshapeFunc(reshape)
glutDisplayFunc(display)

setup()# Set additional properties
glutMainLoop()# Start the openGL event loop
```

---

### Post by crazyfuturamanoob on 2008-11-17
I'd say the problem indeed **IS** in your code. I tried to run it, and it doesn't work.

But instead, my own PyOpenGL scripts work, so the problem must be in your code.

---

### Post by Cracauer on 2008-11-17
Not much opportunity to help if you don't post the error message you got...

---

### Post by imfromwales on 2008-11-17
I dont understand. It works perfectly fine on other computers, and on my computer before i upgraded... When i run it in the terminal (instead of DrPython) i get an error messgae - Segmentation failure.....

---

### Post by rabbitman on 2008-11-17
> **crazyfuturamanoob said:**
> I'd say the problem indeed **IS** in your code. I tried to run it, and it doesn't work.

But instead, my own PyOpenGL scripts work, so the problem must be in your code.

I've got Dr. Python & PyOpenGL installed in Ubuntu & Vista. I just installed Python 2.6 in Vista so I thought I'd try the script & it's appeared to work.

---

### Post by imfromwales on 2008-11-18
> **rabbitman said:**
> I've got Dr. Python & PyOpenGL installed in Ubuntu & Vista. I just installed Python 2.6 in Vista so I thought I'd try the script & it's appeared to work.

Press 's' to watch the animation rabbitman ;)

Yes, im on the university computers now, ran it through DrPython and also the terminal and it works on both! there is no problem with the code, but a problem with the upgrade to ubuntu 8.10 somehow.

---

### Post by steinarhugi on 2008-11-18
Same problem here since I upgraded. Tried downgrading to python 2.4 with the same results. OpenGL/Glut works flawlessly in C/C++ though so it appears to be PyOpenGL related.

```

$ python test.py 
Segmentation fault
```


The libraries are included but as soon as I call glutInitDisplayMode it breaks.

Steinar Hugi

---

### Post by Cracauer on 2008-11-18
Please give specific package names and versions of all relevant packages (python, opengl, video drivers, py wrappers).

Do regular OpenGL programs work, such as glxgears?

---

### Post by imfromwales on 2008-11-18
> **Cracauer said:**
> Please give specific package names and versions of all relevant packages (python, opengl, video drivers, py wrappers).

Do regular OpenGL programs work, such as glxgears?

im not sure if regular opengl programs work, could someone please post some code and il try run it. 

I dont know how to find out what packages and versions i have, how can i find out?

---

### Post by Cracauer on 2008-11-18
Install mesa-utils and call "glxgears".

dpkg-query -l | egrep 'python|opengl|glx|mesa'

---

### Post by rabbitman on 2008-11-18
> **imfromwales said:**
> Press 's' to watch the animation rabbitman ;)

It reminds me of _[Q*bert](http://en.wikipedia.org/wiki/Q*bert)_. :)

Ok, this morning I tried your program in Ubuntu 8.04 both from the terminal & Dr. Python but I couldn't get it to work. Later this afternoon I updated to Ubuntu 8.10 & tried the program again but I got the same result that steinarhugi got; a segmentation fault.

I've just tried a C++ OpenGL program & that worked, I then downloaded the PyOpenGL demos from _[here](http://sourceforge.net/project/showfiles.php?group_id=5988&package_id=221827&release_id=626288)_ & have got a segmentation fault with everyone I've tried so-far.

---

### Post by steinarhugi on 2008-11-19
[LIST=1]
[*]Clean Ubuntu 8.10 install
[*]aptitude install python python-opengl
[/LIST]


Since then I've been trying various versions, installing and removing packages. Building Python locally had no effect. OpenGL in general seems to be working, glxgears runs without any problems and I'm able to build and run C++ code using OpenGL/glut.

I'm using a Dell Latitude D620 laptop with Intel 945GM graphics card.


```

steinar@steinar-laptop:~$ dpkg-query -l | egrep 'python|opengl|glx|mesa'
ii  libgl1-mesa-dev                           7.2-1ubuntu2                          A free implementation of the OpenGL API -- G
ii  libgl1-mesa-dri                           7.2-1ubuntu2                          A free implementation of the OpenGL API -- D
ii  libgl1-mesa-glx                           7.2-1ubuntu2                          A free implementation of the OpenGL API -- G
ii  libglitz-glx1                             0.5.6-1                               Glitz OpenGL library GLX backend
ii  libglu1-mesa                              7.2-1ubuntu2                          The OpenGL utility library (GLU)
ii  libglu1-mesa-dev                          7.2-1ubuntu2                          The OpenGL utility library -- development fi
ii  libqt4-opengl                             4.4.3-0ubuntu1                        Qt 4 OpenGL module
ii  libqt4-opengl-dev                         4.4.3-0ubuntu1                        Qt 4 OpenGL library development files
ii  mesa-common-dev                           7.2-1ubuntu2                          Developer documentation for Mesa
ii  mesa-utils                                7.2-1ubuntu2                          Miscellaneous Mesa GL utilities
ii  python                                    2.5.2-1ubuntu1                        An interactive high-level object-oriented la
ii  python-apport                             0.119                                 apport crash report handling library
ii  python-apt                                0.7.7.1ubuntu4                        Python interface to libapt-pkg
ii  python-beagle                             0.3.5-1                               Python bindings for beagle
ii  python-brlapi                             3.10-0ubuntu2                         Python bindings for BrlAPI
ii  python-cairo                              1.4.12-1                              Python bindings for the Cairo vector graphic
ii  python-central                            0.6.7ubuntu1                          register and build utility for Python packag
ii  python-compizconfig                       0.7.8-0ubuntu1                        Compiz configuration system bindings
ii  python-ctypes                             1.0.2-5ubuntu2                        Python package to create and manipulate C da
ii  python-cups                               1.9.41-0ubuntu1                       Python bindings for CUPS
ii  python-cupshelpers                        1.0.5+git20080819-0ubuntu6            Python modules for printer configuration wit
ii  python-dbus                               0.82.4-2                              simple interprocess messaging system (Python
ii  python-debian                             0.1.11                                Python modules to work with Debian-related d
ii  python-gconf                              2.22.3-0ubuntu1                       Python bindings for GConf2
ii  python-gdata                              1.0.9-1ubuntu1                        Google Data Python client library
ii  python-gdbm                               2.5.2-1ubuntu1                        GNU dbm database support for Python
ii  python-glade2                             2.13.0-0ubuntu8                       GTK+ bindings: Glade support
ii  python-gmenu                              2.24.1-0ubuntu1                       an implementation of the freedesktop menu sp
ii  python-gnome2                             2.22.3-0ubuntu1                       Python bindings for the GNOME desktop enviro
ii  python-gnome2-desktop                     2.24.0-0ubuntu1                       Python bindings for the GNOME desktop enviro
ii  python-gnomecanvas                        2.22.3-0ubuntu1                       Python bindings for gnomecanvas (debug exten
ii  python-gnupginterface                     0.3.2-9ubuntu1                        Python interface to GnuPG (GPG)
ii  python-gobject                            2.15.3-0ubuntu5                       Python bindings for the GObject library
ii  python-gst0.10                            0.10.13-1                             generic media-playing framework (Python bind
ii  python-gtk2                               2.13.0-0ubuntu8                       Python bindings for the GTK+ widget set
ii  python-gtkhtml2                           2.19.1-0ubuntu11                      Python bindings for the GtkHTML2 library
ii  python-gtksourceview2                     2.4.0-0ubuntu1                        Python bindings for the GtkSourceView widget
ii  python-imaging                            1.1.6-3                               Python Imaging Library
ii  python-launchpad-bugs                     0.3.1                                 simple Python Interface to Bugs in Launchpad
ii  python-launchpad-integration              0.1.21                                library for launchpad integration
ii  python-libxml2                            2.6.32.dfsg-4ubuntu1                  Python bindings for the GNOME XML library
ii  python-minimal                            2.5.2-1ubuntu1                        A minimal subset of the Python language (def
ii  python-notify                             0.1.1-2build1                         Python bindings for libnotify
ii  python-numeric                            24.2-9                                Numerical (matrix-oriented) Mathematics for 
ii  python-numpy                              1:1.1.1-1                             Numerical Python adds a fast array facility 
ii  python-opengl                             3.0.0~b3-1ubuntu2                     Python bindings to OpenGL
ii  python-opengl-doc                         3.0.0~b3-1ubuntu2                     Documentation for PyOpenGL
ii  python-openssl                            0.7-2                                 Python wrapper around the OpenSSL library
ii  python-pkg-resources                      0.6c9-0ubuntu1                        Package Discovery and Resource Access using 
ii  python-problem-report                     0.119                                 Python library to handle problem reports
ii  python-pyatspi                            1.24.0-0ubuntu3                       Assistive Technology Service Provider Interf
ii  python-pyorbit                            2.24.0-0ubuntu1                       A Python language binding for the ORBit2 COR
ii  python-rdflib                             2.4.0-5                               RDF library containing an RDF triple store a
ii  python-setuptools                         0.6c9-0ubuntu1                        Python Distutils Enhancements
ii  python-sexy                               0.1.9-1ubuntu1                        python language bindings for libsexy
ii  python-software-properties                0.68.1                                manage the repositories that you install sof
ii  python-support                            0.8.4                                 automated rebuilding support for Python modu
ii  python-tk                                 2.5.2-1ubuntu1                        Tkinter - Writing Tk applications with Pytho
ii  python-uno                                1:2.4.1-11ubuntu2                     Python interface for OpenOffice.org
ii  python-usb                                0.4.1-4                               USB interface for Python
ii  python-virtkey                            0.50ubuntu1                           Library to emulate keyboard keypresses.
ii  python-vte                                1:0.17.4-0ubuntu1                     Python bindings for the VTE widget set
ii  python-xapian                             1.0.7-3                               Xapian search engine interface for Python
ii  python-xdg                                0.15-1.1ubuntu4                       A python library to access freedesktop.org s
ii  python-xkit                               0.3.6                                 library for the manipulation of the xorg.con
ii  python2.4                                 2.4.5-5ubuntu1                        An interactive high-level object-oriented la
ii  python2.4-minimal                         2.4.5-5ubuntu1                        A minimal subset of the Python language (ver
ii  python2.5                                 2.5.2-11.1ubuntu1                     An interactive high-level object-oriented la
ii  python2.5-minimal                         2.5.2-11.1ubuntu1                     A minimal subset of the Python language (ver
ii  rss-glx                                   0.8.1-10ubuntu2                       Really Slick Screensavers GLX Port
ii  xlibmesa-gl-dev                           1:7.4~5ubuntu3                        transitional package for Debian etch

```

---

### Post by rabbitman on 2008-11-19
I found _[this](https://sourceforge.net/mailarchive/forum.php?thread_name=c9a625a90811111256k6dbb3cfaqbb26d7356cffa8b0%40mail.gmail.com&forum_name=pyopengl-users)_ post on the PyOpenGL mailing list yesterday.

Apparently other people are having this problem too. :(

---

### Post by steinarhugi on 2008-11-23
Simple two line script which produces this behaviour:
**Test.py**:
```

from OpenGL.GLUT import *
glutInitDisplayMode(GLUT_RGB)
```

I have an Intel 945GM graphics card, wonder if this is driver related.

---

### Post by rabbitman on 2008-11-23
> **steinarhugi said:**
> I have an Intel 945GM graphics card, wonder if this is driver related.

It might be, I've got an Intel 965GM graphics card & got the same results you did when running that short routine. :(

---

### Post by steinarhugi on 2008-11-23
Reformatted and reinstalled Ubuntu to see if something else I had installed was affecting Python without success. However Python 2.4 with [PyOpenGL 2.0.1.09-1.1ubuntu3]("http://ftp.linux.org.tr/ubuntu/pool/universe/p/pyopengl/python2.4-opengl_2.0.1.09-1.1ubuntu3_i386.deb") works.

---

### Post by psychok7 on 2009-03-12
hi have the same segmentations fault problem.. is there a solution yet? im runnning ubuntu 8.10, and i installed pyopengl through synaptic.
also get segmentation fault with examples from pyopengl site..please help

---

### Post by rabbitman on 2009-03-12
The information in this thread was posted onto the [_PyOpenGL-Users Mailing list_](https://lists.sourceforge.net/lists/listinfo/pyopengl-users) some months ago. 

If I recall the problem was to do with initializing a context before certain GL commands can be called.

Perhaps you should make a new post regarding the problem on the mailing list?

---

### Post by psychok7 on 2009-03-12
> **rabbitman said:**
> The information in this thread was posted onto the [_PyOpenGL-Users Mailing list_](https://lists.sourceforge.net/lists/listinfo/pyopengl-users) some months ago. 

If I recall the problem was to do with initializing a context before certain GL commands can be called.

Perhaps you should make a new post regarding the problem on the mailing list?

ok, but do u know if the problem was solved?.. the thing is.. in my friends computer it works..actually hes running debian with some experimental repositorys maybe its coz of that

---

### Post by rabbitman on 2009-03-12
Personally speaking it wasn't solved for me. :(

I last tried using PyOpenGL in Ubuntu about a week ago & encountered the same problems again. I'm currently using Mandriva & haven't got around to installing PyOpenGL.

It may be the experimental repositories or it could be your friends graphics card. You aren't using an Intel card on your computer are you?

---

### Post by psychok7 on 2009-03-12
> **rabbitman said:**
> Personally speaking it wasn't solved for me. :(

I last tried using PyOpenGL in Ubuntu about a week ago & encountered the same problems again. I'm currently using Mandriva & haven't got around to installing PyOpenGL.

It may be the experimental repositories or it could be your friends graphics card. You aren't using an Intel card on your computer are you?

yeah im using an intel and hes using an ati

---

### Post by rabbitman on 2009-03-12
I think it could well be a problem with Intel Graphics cards then. :frown:

Later on I might make a post on the mailing list to see if there has been any progress solving this issue.

---

### Post by psychok7 on 2009-03-12
> **rabbitman said:**
> I think it could well be a problem with Intel Graphics cards then. :frown:

Later on I might make a post on the mailing list to see if there has been any progress solving this issue.

ok thanks.. please report back if u have an answer... how about a virtual machine? would it be very slow?i have to develop a 3d game

---

### Post by rabbitman on 2009-03-12
I've never used a Virtual Machine so I wouldn't know if they were slow or not, sorry. :P

I'm currently running a Dual-boot system, Windows Vista & Mandriva, so I can develop my PyOpenGL app in Windows. ;)

---

