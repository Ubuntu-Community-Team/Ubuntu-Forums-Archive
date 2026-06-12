---
title: "Undefined resource in OpenGL code help plz D:"
date: 2013-10-08
forum: Programming Talk
---

### Post by josh17 on 2013-10-08
I'm learning OpenGL thrugh a website and the first lessons finished code looks like this:

```
// -- Written in C -- //

#include<stdio.h>
#include<stdlib.h>
#include<X11/X.h>
#include<X11/Xlib.h>
#include<GL/gl.h>
#include<GL/glx.h>
#include<GL/glu.h>

Display                 *dpy;
Window                  root;
GLint                   att[] = { GLX_RGBA, GLX_DEPTH_SIZE, 24, GLX_DOUBLEBUFFER, None };
XVisualInfo             *vi;
Colormap                cmap;
XSetWindowAttributes    swa;
Window                  win;
GLXContext              glc;
XWindowAttributes       gwa;
XEvent                  xev;

void DrawAQuad() {
 glClearColor(1.0, 1.0, 1.0, 1.0);
 glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

 glMatrixMode(GL_PROJECTION);
 glLoadIdentity();
 glOrtho(-1., 1., -1., 1., 1., 20.);

 glMatrixMode(GL_MODELVIEW);
 glLoadIdentity();
 gluLookAt(0., 0., 10., 0., 0., 0., 0., 1., 0.);

 glBegin(GL_QUADS);
  glColor3f(1., 0., 0.); glVertex3f(-.75, -.75, 0.);
  glColor3f(0., 1., 0.); glVertex3f( .75, -.75, 0.);
  glColor3f(0., 0., 1.); glVertex3f( .75,  .75, 0.);
  glColor3f(1., 1., 0.); glVertex3f(-.75,  .75, 0.);
 glEnd();
}

int main(int argc, char *argv[]) {

 dpy = XOpenDisplay(NULL);

 if(dpy == NULL) {
        printf("\n\tcannot connect to X server\n\n");
        exit(0);
 }

 root = DefaultRootWindow(dpy);

 vi = glXChooseVisual(dpy, 0, att);

 if(vi == NULL) {
        printf("\n\tno appropriate visual found\n\n");
        exit(0);
 }
 else {
        printf("\n\tvisual %p selected\n", (void *)vi->visualid); /* %p creates hexadecimal output like in glxinfo */
 }


 cmap = XCreateColormap(dpy, root, vi->visual, AllocNone);

 swa.colormap = cmap;
 swa.event_mask = ExposureMask | KeyPressMask;

 win = XCreateWindow(dpy, root, 0, 0, 600, 600, 0, vi->depth, InputOutput, vi->visual, CWColormap | CWEventMask, &swa);

 XMapWindow(dpy, win);
 XStoreName(dpy, win, "VERY SIMPLE APPLICATION");

 glc = glXCreateContext(dpy, vi, NULL, GL_TRUE);
 glXMakeCurrent(dpy, win, glc);

 glEnable(GL_DEPTH_TEST);

 while(1) {
        XNextEvent(dpy, &xev);

        if(xev.type == Expose) {
                XGetWindowAttributes(dpy, win, &gwa);
                glViewport(0, 0, gwa.width, gwa.height);
                DrawAQuad();
                glXSwapBuffers(dpy, win);
        }

        else if(xev.type == KeyPress) {
                glXMakeCurrent(dpy, None, NULL);
                glXDestroyContext(dpy, glc);
                XDestroyWindow(dpy, win);
                XCloseDisplay(dpy);
                exit(0);
        }
    } /* this closes while(1) { */
} /* this is the } which closes int main(int argc, char *argv[]) { */


```

but when I run it I get this error

undefined reference to `gluLookAt'|

how can I fix this? D:

---

### Post by Erik1984 on 2013-10-08
You might be missing the proper build package for that particular library. That error simply means it can't find the function gluLookAt()

I know nothing about OpenGL but there is a package called **libglu1-mesa-dev** in the repos. You could try to install that and compile again and see if the error disappears. In that case it's likely that you miss more *-dev packages and need to find out their names and install those too. 

edit: forget this answer and try kostkon's first :P

---

### Post by kostkon on 2013-10-08
First of all, make sure that you have the dev pacakge for freeglut, i.e.
```
sudo apt-get install freeglut3-dev
```

---

### Post by josh17 on 2013-10-08
> **kostkon said:**
> First of all, make sure that you have the dev pacakge for freeglut, i.e.
```
sudo apt-get install freeglut3-dev
```

Nope still getting the error :/

---

### Post by Mr.Pytagoras on 2013-10-08
for this you don't need freeglut package, all you need is X and openGL headers and a driver for your graphic card, then you have to tell the linker about the libraries.
Compile the code with this:
```
gcc YOURSOURCEFILE -lGL -lX11 -lGLU
```

and it will work, if you will use glut or freeglut then you will have to add -lglut to tell the linker to link your code with the glut library

---

