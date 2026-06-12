---
title: "OpenGL: problem with glVertex2iv()"
date: 2010-03-20
forum: Programming Talk
---

### Post by akudewan on 2010-03-20
Hi,

I'm learning OpenGL, and I'm having some trouble using the glVertex2iv() function:

```

#include<GL/gl.h>
#include<GL/glu.h>
#include<GL/glut.h>

void init()
{
  glClearColor(0.0, 0.0, 0.0, 0.0);
  glShadeModel(GL_FLAT);
}

void display()
{
  glClear (GL_COLOR_BUFFER_BIT);
  glColor3f (1.0, 1.0, 1.0);
  GLint foo[] = {100,100,300,300};
  glBegin(GL_LINES);
   [COLOR="Red"]glVertex2iv(foo);[/COLOR]
   [COLOR="SeaGreen"]//glVertex2i(100,100);
   //glVertex2i(300,300);[/COLOR]
  glEnd();
  glFlush();
}

void reshape(int w, int h)
{
  glViewport(0,0, (GLsizei) w, (GLsizei) h);
  glMatrixMode(GL_PROJECTION);
  glLoadIdentity();
  gluOrtho2D(0.0, (GLdouble)w, 0.0, (GLdouble)h);
}

int main(int argc, char** argv)
{
  glutInit(&argc, argv);
  glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB);
  glutInitWindowSize(640,480);
  glutInitWindowPosition(100,100);
  glutCreateWindow(argv[0]);
  init();
  glutDisplayFunc(display);
  glutReshapeFunc(reshape);
  glutMainLoop();
  return 0;
}

```

The line in red doesn't work, but the lines in green work. I'm quite new to graphics programming. Am I doing something wrong here?

---

### Post by pbrane on 2010-03-20
glVertext2iv wants a pointer to an array of two elements.

```

GLint foo1[] = {100, 100};
GLint foo2[] = {300, 300};
glVertex2iv(foo1);
glVertex2iv(foo2);

```

you may want to look at vertex arrays

---

### Post by akudewan on 2010-03-20
Thanks for the help :) It works now. I did check out vertex arrays, I was getting confused between the two.

---

