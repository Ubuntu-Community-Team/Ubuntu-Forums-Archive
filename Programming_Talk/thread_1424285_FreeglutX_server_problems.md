---
title: "Freeglut/X server problems"
date: 2010-03-07
forum: Programming Talk
---

### Post by Mach1723 on 2010-03-07
Attempting to create a simple window with freeglut and i get the error:

```

freeglut (./ogl_tri):  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  20
  Current serial number in output stream:  23

```

Heres the code i am attempting to compile:

```

//build args: gcc -g ogl_tri.c -o ogl_tri -lglut

#include <GL/freeglut_std.h>


const int  width = 800;
const int  height = 600;


GLvoid InitGL(GLvoid);
GLvoid DrawGL(GLvoid);
GLvoid ResizeGL(GLsizei  width,GLsizei height);

int main(int argc, char** argv)
{
  glutInit(&argc, argv);

  glutInitDisplayMode(GLUT_DOUBLE || GLUT_RGB || GLUT_DEPTH);

  glutInitWindowSize(width,height);

  glutCreateWindow("");

  InitGL();

  glutDisplayFunc(DrawGL);
  glutReshapeFunc(ResizeGL);
  glutMainLoop();

  return 0;
}


GLvoid ResizeGL(GLsizei width,GLsizei height)
{
  if(height == 0)
    {
      height = 1;
    }

  glViewport(0,0,width,height);
  glMatrixMode(GL_PROJECTION);
  glLoadIdentity();

  gluPerspective(45.0f,(GLfloat)width /(GLfloat)height,0.1f,100.0f);
  glMatrixMode(GL_MODELVIEW);

  glLoadIdentity();



}

GLvoid InitGL(GLvoid)
{
  glShadeModel(GL_SMOOTH);
  glClearColor(0.0f,0.0f,0.0f,0.0f);
  glClearDepth(1.0f);
  glEnable(GL_DEPTH_TEST);
  glDepthFunc(GL_LEQUAL);
  glHint(GL_PERSPECTIVE_CORRECTION_HINT , GL_NICEST);



}

GLvoid DrawGL(GLvoid)
{
  glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);
  glLoadIdentity();
}

```

---

### Post by Mach1723 on 2010-03-07
glutInitDisplayMode(GLUT_DOUBLE || GLUT_RGB || GLUT_DEPTH); - the problem was apparently the || changed |.

it opens a entry on the taskbar, but no display, that could be double buffering though.

EDIT: Not double buffering still no window
EDIT2: Turned off compiz got a window no contents, regardless of double buffering.

---

### Post by Mach1723 on 2010-03-07
The code in its current state.

```
//build args: gcc -g ogl_tri.c -o ogl_tri -lglut

#include <GL/glut.h>
#include <unistd.h>

const int  width = 800;
const int  height = 600;


GLvoid InitGL(GLvoid);
GLvoid DrawGL(GLvoid);
GLvoid ResizeGL(GLsizei  width,GLsizei height);

int main(int argc, char** argv)
{
  glutInit(&argc, argv);

  glutInitDisplayMode(GLUT_DOUBLE |GLUT_RGBA |GLUT_DEPTH);

  glutInitWindowSize(width,height);

  glutCreateWindow("Window");

  InitGL();

  glutDisplayFunc(DrawGL);
  glutReshapeFunc(ResizeGL);
  glutMainLoop();

  return 0;
}


GLvoid ResizeGL(GLsizei width,GLsizei height)
{
  if(height == 0)
    {
      height = 1;
    }

  glViewport(0,0,width,height);
  glMatrixMode(GL_PROJECTION);
  glLoadIdentity();

  gluPerspective(45.0f,(GLfloat)width /(GLfloat)height,0.1f,100.0f);
  glMatrixMode(GL_MODELVIEW);

  glLoadIdentity();

}

GLvoid InitGL(GLvoid)
{
  glShadeModel(GL_SMOOTH);//activates smooth shading
  glClearColor(0.0f,0.0f,0.0f,0.0f);//makes bg color black
  glClearDepth(1.0f);//sets depth to 1.0?
  glEnable(GL_DEPTH_TEST);//tests depth
  glDepthFunc(GL_LEQUAL);//depth testing functions
  glHint(GL_PERSPECTIVE_CORRECTION_HINT , GL_NICEST);//hints what perspective to use



}

GLvoid DrawGL(GLvoid)
{
  glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT); //clears the buffer before rendering
  glLoadIdentity(); //rerenders?
  glBegin(GL_TRIANGLES);//creates a tri
    glVertex3f( 0.0f, 1.0f, 0.0f);
    glVertex3f(-1.0f,-1.0f, 0.0f);
    glVertex3f( 1.0f,-1.0f, 0.0f);
    glEnd();//ends
}
```

with compiz off the window opens but displays nothing but whatever the spawned window was infront as can be seen in this screeny.

[IMG]http://lh3.ggpht.com/_hvYTk6wBQV8/S5RdFIeqkaI/AAAAAAAABoo/js5sWqpa59s/s912/2344.png[/IMG]

---

