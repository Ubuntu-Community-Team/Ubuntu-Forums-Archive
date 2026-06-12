---
title: "glx calls to FBConfig API's seg faults"
date: 2011-02-18
forum: Programming Talk
---

### Post by boustro on 2011-02-18
Hi all,

I've tried this on three different setups (fedora core 14), so I'm kind of wondering what's going on.  I have the latest 10.10 ubuntu install with latest patches/updates to everything.  I installed eclipse and most of the OpenGL programming package requirements installed as well.

At any rate, I'm trying to create a simple OpenGL 3.1 context which requires opening a 2.0 context, then making appropriate calls to the 3.1 context.

I have the following code, and it creates the 2.0 context just fine:
```

Display* dpy = XOpenDisplay(NULL);
GLint att[5] = { GLX_RGBA, GLX_DEPTH_SIZE, 24, GLX_DOUBLEBUFFER, None };

XVisualInfo* vi = glXChooseVisual(dpy, 0, att);
Colormap cmap = XCreateColormap(dpy, root, vi->visual, AllocNone);

XSetWindowAttributes    swa;
swa.border_pixel = 0;
swa.colormap = cmap;
swa.event_mask = ExposureMask | KeyPressMask;

    // create the window
Window win = XCreateWindow(dpy, root, 0, 0, 600, 600, 0, vi->depth, InputOutput, vi->visual, CWColormap | CWEventMask, &swa);

```With that code, I can go on an use GLEW to init and draw OpenGL things just fine.

However, when I change the first part of the code to use glx FBConfigs I get crashes:
```

Display*  dpy = XOpenDisplay(NULL);
    int numConfigs=0;

GLXFBConfig * configs = glXGetFBConfigs( dpy, DefaultScreen(dsp), &numConfigs);
printf( "Getting matching framebuffer configs - done\n" );


```I get a segfault from the glxGetFBConfigs() call.  Further, if I try to make a call to glXChooseFBConfig() with an appropriate set of attributes (glxinfo), i also get an immediate segfault.  

Seems like any call to glxFBConfigs() causes an immediate segfault.  This is driving me bonkers.  

Anybody got some tips?

---

