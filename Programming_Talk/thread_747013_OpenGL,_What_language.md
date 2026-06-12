---
title: "OpenGL, What language?"
date: 2008-04-06
forum: Programming Talk
---

### Post by A_B on 2008-04-06
I know python fairly well now and I want to learn OpenGL, especially to make 2D games. I know there is pyOpenGL but there aren't many tutorial specifically for python + openGL (although C tutorials should be easy to copy).

Should I continue using python or should I start learning another language to make (2D) games?

Thanks
Alex

---

### Post by LaRoza on 2008-04-06
Use Python and PyGame, see my wiki.

---

### Post by A_B on 2008-04-06
I won't be using pygame to make my programs because doing it with openGL will also give me a basis to start from when I start learning 3D programming. This is already discussed here:  [http://ubuntuforums.org/showthread.php?t=740000&page=2]("http://ubuntuforums.org/showthread.php?t=740000&page=2")

Thanks for amazingly fast reply though :D
Alex

---

### Post by LaRoza on 2008-04-06
> **A_B said:**
> 
Should I continue using python or should I start learning another language to make (2D) games?

Thanks
Alex

> **A_B said:**
> I won't be using pygame to make my programs because doing it with openGL will also give me a basis to start from when I start learning 3D programming. This is already discussed here:  [http://ubuntuforums.org/showthread.php?t=740000&page=2]("http://ubuntuforums.org/showthread.php?t=740000&page=2")

Thanks for amazingly fast reply though :D
Alex

I wasn't familiar with your other thread, and was responding the the question.

You could browse: [http://pyopengl.sourceforge.net/](http://pyopengl.sourceforge.net/) to get information.

---

### Post by A_B on 2008-04-06
> **LaRoza said:**
> I wasn't familiar with your other thread, and was responding the the question.


Sorry for not including this link in my first post.

So you think I should continue using python?
Does anyone else have an opinion about what language to use woth openGL?

Thanks again
Alex

---

### Post by LaRoza on 2008-04-06
> **A_B said:**
> Sorry for not including this link in my first post.

So you think I should continue using python?
Does anyone else have an opinion about what language to use woth openGL?

Thanks again
Alex

If you know Python stick with it.

When learning new API's, I think it is best to use a language you know, so you can focus on the API.

If you know C or some other language better, then use that.

My wiki has a page for OpenGL (not complete) with links for various languages, if that interests you.

---

### Post by stratavarious on 2008-04-06
.

---

### Post by A_B on 2008-04-06
Well, I think learning it with python now wont make a possible switch to C++ too hard as opengl is practically the same in both languages...

Thakns!

---

### Post by Wybiral on 2008-04-06
Most people use PyGame WITH PyOpenGL. You can't do anything with PyOpenGL on it's own, you need something to initialize the window and manage the events (keys/mouse/etc)... That's what PyGame is for.

---

### Post by Wybiral on 2008-04-06
Here's a really basic example of using PyGame and PyOpenGL together:

```

import pygame
from OpenGL.GL import *
from OpenGL.GLU import *

width, height = 640, 480

# Initialize PyGame
pygame.init()
pygame.display.set_mode((width, height), pygame.DOUBLEBUF | pygame.OPENGL)

# Initialize OpenGL matrices
glMatrixMode(GL_PROJECTION)
glLoadIdentity()
glOrtho(0, width, height, 0, -1, 1)
glMatrixMode(GL_MODELVIEW)
glLoadIdentity()
glDisable(GL_DEPTH_TEST)

angle = 0.0
running = True

while running:
    # Clear color buffer
    glClear(GL_COLOR_BUFFER_BIT)

    # Load identity matrix
    glLoadIdentity()

    # Transform matrix
    glTranslatef(200.0, 200.0, 0.0)
    glRotatef(angle, 0.0, 0.0, 1.0)

    # Draw quad
    glBegin(GL_QUADS)
    glColor3ub(0xff, 0x00, 0x00)
    glVertex2f(-50.0, -50.0)
    glColor3ub(0xff, 0xff, 0x00)
    glVertex2f(50.0, -50.0)
    glColor3ub(0x00, 0xff, 0x00)
    glVertex2f(50.0, 50.0)
    glColor3ub(0x00, 0x00, 0xff)
    glVertex2f(-50.0, 50.0)
    glEnd()

    # Update screen
    pygame.display.flip()

    # Increase angle
    angle += 0.05

    # Check for "quit" event
    for e in pygame.event.get():
        if e.type == pygame.QUIT:
            running = False

```

See, it's easy. Just apply whatever OpenGL tutorials you're reading to that base-code.

---

