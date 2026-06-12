---
title: "Xlib.h is missing"
date: 2008-03-02
forum: Packaging and Compiling Programs
---

### Post by bloodhound23 on 2008-03-02
whenever I try to use xlib gl.h x11 the compiler says they are missing

---

### Post by bloodhound23 on 2008-03-02
ok I fixed that but now the code
```
#define AM_PROG_LIBTOOL
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
 glEnd(); } 
 
int main(int argc, char *argv[]) {

 dpy = XOpenDisplay(NULL);
 
 if(dpy == NULL) {
 	printf("\n\tcannot connect to X server\n\n");
        exit(0); }
        
 root = DefaultRootWindow(dpy);

 vi = glXChooseVisual(dpy, 0, att);

 if(vi == NULL) {
	printf("\n\tno appropriate visual found\n\n");
        exit(0); } 
 else {
	printf("\n\tvisual %p selected\n", vi->visualid); }/* %p creates hexadecimal output like in glxinfo */


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
                glXSwapBuffers(dpy, win); }
                
	else if(xev.type == KeyPress) {
        	glXMakeCurrent(dpy, None, NULL);
 		glXDestroyContext(dpy, glc);
 		XDestroyWindow(dpy, win);
 		XCloseDisplay(dpy);
 		exit(0); }
	} /* this closes while(1) { */
} /* this is the } which closes int main(int argc, char *argv[]) { */ 
```

gives me this output in kdevelop with gcc it is from ld.

```
cd '/home/kristian/krenderd/debug' && WANT_AUTOCONF_2_5="1" WANT_AUTOMAKE_1_6="1" make -k 
make all-recursive
Making all in src
compiling krenderd.c (gcc)
mv -f .deps/krenderd.Tpo .deps/krenderd.Po
linking krenderd (gcc)
krenderd.o: In function `DrawAQuad':
/home/kristian/krenderd/src/krenderd.c:42: undefined reference to `glClearColor'
/home/kristian/krenderd/src/krenderd.c:43: undefined reference to `glClear'
/home/kristian/krenderd/src/krenderd.c:45: undefined reference to `glMatrixMode'
/home/kristian/krenderd/src/krenderd.c:46: undefined reference to `glLoadIdentity'
/home/kristian/krenderd/src/krenderd.c:47: undefined reference to `glOrtho'
/home/kristian/krenderd/src/krenderd.c:49: undefined reference to `glMatrixMode'
/home/kristian/krenderd/src/krenderd.c:50: undefined reference to `glLoadIdentity'
/home/kristian/krenderd/src/krenderd.c:51: undefined reference to `gluLookAt'
/home/kristian/krenderd/src/krenderd.c:53: undefined reference to `glBegin'
/home/kristian/krenderd/src/krenderd.c:54: undefined reference to `glColor3f'
/home/kristian/krenderd/src/krenderd.c:54: undefined reference to `glVertex3f'
/home/kristian/krenderd/src/krenderd.c:55: undefined reference to `glColor3f'
/home/kristian/krenderd/src/krenderd.c:55: undefined reference to `glVertex3f'
/home/kristian/krenderd/src/krenderd.c:56: undefined reference to `glColor3f'
/home/kristian/krenderd/src/krenderd.c:56: undefined reference to `glVertex3f'
/home/kristian/krenderd/src/krenderd.c:57: undefined reference to `glColor3f'
/home/kristian/krenderd/src/krenderd.c:57: undefined reference to `glVertex3f'
/home/kristian/krenderd/src/krenderd.c:58: undefined reference to `glEnd'
krenderd.o: In function `main':
/home/kristian/krenderd/src/krenderd.c:62: undefined reference to `XOpenDisplay'
/home/kristian/krenderd/src/krenderd.c:70: undefined reference to `glXChooseVisual'
/home/kristian/krenderd/src/krenderd.c:79: undefined reference to `XCreateColormap'
/home/kristian/krenderd/src/krenderd.c:84: undefined reference to `XCreateWindow'
/home/kristian/krenderd/src/krenderd.c:86: undefined reference to `XMapWindow'
/home/kristian/krenderd/src/krenderd.c:87: undefined reference to `XStoreName'
/home/kristian/krenderd/src/krenderd.c:89: undefined reference to `glXCreateContext'
/home/kristian/krenderd/src/krenderd.c:90: undefined reference to `glXMakeCurrent'
/home/kristian/krenderd/src/krenderd.c:92: undefined reference to `glEnable'
/home/kristian/krenderd/src/krenderd.c:95: undefined reference to `XNextEvent'
/home/kristian/krenderd/src/krenderd.c:98: undefined reference to `XGetWindowAttributes'
/home/kristian/krenderd/src/krenderd.c:99: undefined reference to `glViewport'
/home/kristian/krenderd/src/krenderd.c:101: undefined reference to `glXSwapBuffers'
/home/kristian/krenderd/src/krenderd.c:104: undefined reference to `glXMakeCurrent'
/home/kristian/krenderd/src/krenderd.c:105: undefined reference to `glXDestroyContext'
/home/kristian/krenderd/src/krenderd.c:106: undefined reference to `XDestroyWindow'
/home/kristian/krenderd/src/krenderd.c:107: undefined reference to `XCloseDisplay'
collect2: ld returned 1 exit status
make[2]: *** [krenderd] Error 1
make[2]: Target `all' not remade because of errors.
make[2]: Nothing to be done for `all-am'.
make[1]: *** [all-recursive] Error 1
make: *** [all] Error 2
*** Exited with status: 2 ***

```

---

### Post by bloodhound23 on 2008-03-02
Ok, I run that and now it says no appropriate visual found?

---

### Post by seeprogrammer on 2008-04-01
Where did you find xlib.h?

---

### Post by Zugzwang on 2008-04-01
You can use [http://packages.ubuntu.com]("http://packages.ubuntu.com") to search for packages containing the file you need. For example your file is contained in the package "libx11-dev" so you might have to execute:
```
sudo apt-get install libx11-dev
```

When linking the program, do not forget to add the "-lX11" parameter in order to link to the library.

---

