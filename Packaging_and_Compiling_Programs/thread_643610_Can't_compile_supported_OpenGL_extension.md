---
title: "Can't compile supported OpenGL extension"
date: 2007-12-18
forum: Packaging and Compiling Programs
---

### Post by Roque on 2007-12-18
I am developing an OpenGL application for which I need to use glBlendEquationSeparate(...). My intel 945G claims to support the required extension (EXT_BLEND_EQUATION_SEPARATE). 

It is declared in glext.h, but the linker cannot find a definition for the function. and points to an "undefined reference" at the line in the code where the function should be enabled. I am using several other extensions with no problem, tough.

My libGL is version 1.2 (libGL.so.1.2). It should be 1.4 (BLEND_EQUATION_SEPARATE is implemented in 1.4), but I can't find this version in the repositories. 
I am using libgl1-mesa-dri and libgl1-mesa-glx.

Does Ubuntu support OpenGL 1.4 with mesa implementation? 
Any help will be appreciated.

---

### Post by stroyan on 2007-12-20
I can get it work using glBlendEquationSeparateEXT() and libGLEW.
You need packages libglew1.4 and libglew1.4-dev.
The example below is compiled and linked with
```
cc -o blend blend.c -lglut -lGL -lGLEW
```The include of GL/glew.h needs to be before glut.h or gl.h.
```
#include <GL/glew.h>
#include <GL/glut.h>
#include <stdio.h>
#include <stdlib.h>

void reshape(GLsizei w, GLsizei h)
{
  glViewport(0,0,w,h);
  glFlush();
}

void display(void)
{
  glClearColor(0.3, 0.3, 0.3, 0.0);
  glClear(GL_COLOR_BUFFER_BIT);

  if (GLEW_EXT_blend_equation_separate) {
    glBlendEquationSeparateEXT(GL_FUNC_ADD,GL_FUNC_ADD);
  }
  glBegin(GL_LINES);
  glColor4f(0.0, 1.0, 0.0, 0.1);
  glVertex2f(50,50);
  glColor4f(0.0, 1.0, 0.0, 1.0);
  glVertex2f(450,50);
  glColor4f(1.0, 0.0, 0.0, 0.1);
  glVertex2f(50,100);
  glColor4f(1.0, 0.0, 0.0, 1.0);
  glVertex2f(450,100);
  glEnd();
  if (GLEW_EXT_blend_equation_separate) {
    glBlendEquationSeparateEXT(GL_FUNC_REVERSE_SUBTRACT,GL_FUNC_SUBTRACT);
  }
  glBegin(GL_LINES);
  glColor4f(0.0, 1.0, 0.0, 0.1);
  glVertex2f(50,80);
  glColor4f(0.0, 1.0, 0.0, 1.0);
  glVertex2f(450,80);
  glColor4f(1.0, 0.0, 0.0, 0.1);
  glVertex2f(50,108);
  glColor4f(1.0, 0.0, 0.0, 1.0);
  glVertex2f(450,108);
  if (GLEW_EXT_blend_equation_separate) {
    glBlendEquationSeparateEXT(GL_FUNC_ADD,GL_FUNC_ADD);
  }
  glEnd();
  glFlush();
}

void print_equation(val)
{
    switch(val) {
      case GL_FUNC_ADD:
	  fprintf(stdout, "GL_FUNC_ADD\n");
	  break;
      case GL_FUNC_SUBTRACT:
	  fprintf(stdout, "GL_FUNC_SUBTRACT\n");
	  break;
      case GL_FUNC_REVERSE_SUBTRACT:
	  fprintf(stdout, "GL_FUNC_REVERSE_SUBTRACT\n");
	  break;
      case GL_MAX:
	  fprintf(stdout, "GL_MAX\n");
	  break;
      case GL_MIN:
	  fprintf(stdout, "GL_MIN\n");
	  break;
      default:
	  fprintf(stdout, "unknown\n");
    }
}

int main(int argc, char *argv[])
{
  GLenum err;
  glutInit(&argc, argv);
  glutInitWindowSize(512, 512);
  glutInitDisplayMode(GLUT_SINGLE | GLUT_RGBA);
  glutCreateWindow("blend");

  err = glewInit();
  if (GLEW_OK != err)
  {
    /* Problem: glewInit failed, something is seriously wrong. */
      fprintf(stderr, "Error: %s\n", glewGetErrorString(err));
  }
  fprintf(stdout, "Status: Using GLEW %s\n", glewGetString(GLEW_VERSION));

  glLineWidth(5.0);
  glEnable(GL_BLEND);
  glBlendFunc(GL_SRC_ALPHA, GL_ONE_MINUS_SRC_ALPHA);

  if (GLEW_EXT_blend_equation_separate) {
      GLint blend_rgb, blend_alpha;
      GLint blend_rgb_orig, blend_alpha_orig;
      fprintf(stdout, "GL_EXT_blend_equation_separate supported\n");
      glGetIntegerv(GL_BLEND_EQUATION_RGB_EXT, &blend_rgb_orig);
      glGetIntegerv(GL_BLEND_EQUATION_ALPHA_EXT, &blend_alpha_orig);
      fprintf(stdout, "original GL_BLEND_EQUATION_RGB_EXT: ");
      print_equation(blend_rgb_orig);
      fprintf(stdout, "original GL_BLEND_EQUATION_ALPHA_EXT: ");
      print_equation(blend_alpha_orig);
      /* Set values and read them back */
      glBlendEquationSeparateEXT(GL_FUNC_SUBTRACT,GL_MAX);
      glGetIntegerv(GL_BLEND_EQUATION_RGB_EXT, &blend_rgb);
      glGetIntegerv(GL_BLEND_EQUATION_ALPHA_EXT, &blend_alpha);
      fprintf(stdout, "new GL_BLEND_EQUATION_RGB_EXT: ");
      print_equation(blend_rgb);
      fprintf(stdout, "new GL_BLEND_EQUATION_ALPHA_EXT: ");
      print_equation(blend_alpha);
      /* reset values */
      glBlendEquationSeparateEXT(blend_rgb_orig,blend_alpha_orig);
  }

  glMatrixMode(GL_PROJECTION);
  glLoadIdentity();
  gluOrtho2D(0,512,0,512);

  glMatrixMode(GL_MODELVIEW);
  glLoadIdentity();

  glFlush();

  glutReshapeFunc(reshape);
  glutDisplayFunc(display);

  glutMainLoop();
  return 0;
}
```

---

### Post by Roque on 2007-12-23
Many thanks for your answer!

Your code works fine. I get no linking errors so the extension is implemented in libGL.so.1.2

I wonder what's going on... I'll check GLEW sources.

---

