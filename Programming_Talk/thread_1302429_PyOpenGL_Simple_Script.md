---
title: "PyOpenGL Simple Script"
date: 2009-10-27
forum: Programming Talk
---

### Post by Baerun on 2009-10-27
I've been messing around with pygame and OpenGL but couldn't seem to get it to work. I've made a real simple script to try to test it, but I still can't get any primitives to show. The window is created and the clear color will change the color, but for some reason I can't see the triangle I am trying to draw. I've used OpenGL in C++ before and I can't understand what I am doing wrong. Does this code look right to you?

```



def main():

    width = 800
    height = 600
    
    pygame.display.init()

    pygame.display.set_mode((width,height),pygame.HWSURFACE|pygame.OPENGL|pygame.DOUBLEBUF)
  
    glClearColor(0.0, 0.0, 0.0, 1.0)
    glClear(GL_COLOR_BUFFER_BIT)
    

    glViewport(0, 0, width, height)

    glMatrixMode(GL_PROJECTION)

    glLoadIdentity()

    gluPerspective(60.0, float(width)/height, .1, 1000.)

    glMatrixMode(GL_MODELVIEW)

    glLoadIdentity()
      
    pygame.display.flip()
            
    while (True):
        glClear(GL_COLOR_BUFFER_BIT)
        glPushMatrix()

        glColor3f(1.0, 0.0, 0.0)
        glBegin(GL_TRIANGLES);
        glVertex3f(100.0, 100.0, 0.0);
        glVertex3f(150.0, 100.0, 0.0);
        glVertex3f(125.0, 50.0, 0.0);
        glEnd( );


        glPopMatrix()
        pygame.display.flip()
        time.sleep(0.01)


	

if __name__ == "__main__":

	main()

```

---

### Post by Marco A on 2009-10-27
.

---

### Post by Baerun on 2009-10-27
Ah yes, the field of view stuff always confuses me. I changed my script and I can now see my red triangle. I'm reading up on glFrustum right now and it actually seems pretty simple.

Thanks for the help.

---

