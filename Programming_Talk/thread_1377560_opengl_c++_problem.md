---
title: "opengl c++ problem"
date: 2010-01-10
forum: Programming Talk
---

### Post by bigrockcrasher on 2010-01-10
I have this issue with opengl. i am currently writing a template C++ program that uses openGL. currently I am using scripts i find on the Internet. I am testing two scripts which is shown below. I have used this script a long time ago and it did work well. but after several years of not doing anything with opengl it does not seem to work. what it does is a small window will opens which is what suppose to do. the window do not have borders and it does some thing weird with move things over it. attached to this post is what it looks like. the rainbow-ish thing next to the terminal is what it looks like. I moved the terminal window over it looks. I know the program works I think it is my computer. i ran this cope on two computers and got the same result. 
 to compile code: "cc -o simple simple.c -lglut -lGLU -lGL -lXmu -lXext -lX11 -lm"  I ran another c++ code and it did the same thing. does anyone know how to fix this 
 I am runnnig ubuntu 9.10 and the other computer used is version 9.04




/* This program is freely distributable without licensing fees 
   and is provided without guarantee or warrantee expressed or 
   implied. This program is -not- in the public domain. */

/* This program is a response to a question posed by Gil Colgate
   <gcolgate@sirius.com> about how lengthy a program is required using
   OpenGL compared to using  Direct3D immediate mode to "draw a
   triangle at screen coordinates 0,0, to 200,200 to 20,200, and I
   want it to be blue at the top vertex, red at the left vertex, and
   green at the right vertex".  I'm not sure how long the Direct3D
   program is; Gil has used Direct3D and his guess is "about 3000
   lines of code". */

/* X compile line: cc -o simple simple.c -lglut -lGLU -lGL -lXmu -lXext -lX11 -lm */

#include <GL/glut.h>
void setup() {
       glClearColor(.0f, .0f, .0f, .0f);
}

void
reshape(int w, int h)
{
  /* Because Gil specified "screen coordinates" (presumably with an
     upper-left origin), this short bit of code sets up the coordinate
     system to correspond to actual window coodrinates.  This code
     wouldn't be required if you chose a (more typical in 3D) abstract
     coordinate system. */

  glViewport(0, 0, w, h);       /* Establish viewing area to cover entire window. */
  glMatrixMode(GL_PROJECTION);  /* Start modifying the projection matrix. */
  glLoadIdentity();             /* Reset project matrix. */
  glOrtho(0, w, 0, h, -1, 1);   /* Map abstract coords directly to window coords. */
  glScalef(1, -1, 1);           /* Invert Y axis so increasing Y goes down. */
  glTranslatef(0, -h, 0);       /* Shift origin up to upper-left corner. */
}

void
display(void)
{
  glClear(GL_COLOR_BUFFER_BIT);
  glBegin(GL_TRIANGLES);
    glColor3f(0.0, 0.0, 1.0);  /* blue */
    glVertex2i(0, 0);
    glColor3f(0.0, 1.0, 0.0);  /* green */
    glVertex2i(200, 200);
    glColor3f(1.0, 0.0, 0.0);  /* red */
    glVertex2i(20, 200);
  glEnd();
  glFlush();  /* Single buffered, so needs a flush. */
}

int
main(int argc, char **argv)
{
  glutInit(&argc, argv);
  glutCreateWindow("single triangle");
  setup();
  glutDisplayFunc(display);
  glutReshapeFunc(reshape);
  glutMainLoop();
  return 0;             /* ANSI C requires main to return int. */
}

---

### Post by Zugzwang on 2010-01-10
Did you try turning off the desktop effects before running the program? Search in this forum for details.

---

### Post by bigrockcrasher on 2010-01-10
Dude you are the man. it worked. By any chance do you know why it does this.

---

### Post by bigrockcrasher on 2010-01-11
Since i have disabled the desktop effects another problem has occurred. on my computer my whole screen turns black.if i have select another window. a the black screen goes away and you can see the program working current. on my other computer, the image does not refresh itself. I have a keyboard function running on it that chages the shape of the triangle. I have to minimize the window and then maximize it to see any changes.  does anyone how to fix this

---

