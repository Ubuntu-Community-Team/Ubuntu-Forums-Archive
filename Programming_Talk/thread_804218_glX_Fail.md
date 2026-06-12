---
title: "glX Fail"
date: 2008-05-22
forum: Programming Talk
---

### Post by marc.andrysco on 2008-05-22
I wrote a program that uses glX for the (obvious) purpose of rendering via OpenGL.  This was all good and dandy until I got Ubuntu 8.04 up and running (7.10 was atrocious) and I put on the nice Visual Effects (which is Compiz, no?).  When I ran the program, what I wanted to be displayed worked perfectly, however I lost the window's borders and title bar and all other decorations.  It also causes a very annoying, occasional flicker of the screen.  I've scoured the interwebs and decided to make a post about it.

The original source code is rather long and complicated, so I found a nice simplified example that I took from somewhere on the internet that displays the problem nicely without the complexity of my program.  Below is that entire source file:

```
#include <stdio.h>
#include <stdlib.h>
#include <X11/Xlib.h>
#include <GL/gl.h>
#include <GL/glx.h>


static int attributeListSgl[] = { 
	GLX_RGBA,
	GLX_RED_SIZE, 1, /*get the deepest buffer with 1 red bit*/
	GLX_GREEN_SIZE, 1,
	GLX_BLUE_SIZE, 1,
	None };

static int attributeListDbl[] = {
	GLX_RGBA,
	GLX_DOUBLEBUFFER, /*In case single buffering is not supported*/
	GLX_RED_SIZE, 1,
	GLX_GREEN_SIZE, 1,
	GLX_BLUE_SIZE, 1,
	None };


static Bool WaitForNotify(Display *d, XEvent *e, char *arg) { 
	return (e->type == MapNotify) && (e->xmap.window == (Window)arg);
} 

int main(int argc, char **argv) {
	Display *dpy;
	XVisualInfo *vi;
	Colormap cmap;
	XSetWindowAttributes swa;
	Window win;
	GLXContext cx;
	XEvent event;
	
	int swap_flag = 0;
	
	/* get a connection */ 
	dpy = XOpenDisplay(0);
	
	/* get an appropriate visual */
	vi = glXChooseVisual(dpy, DefaultScreen(dpy), attributeListSgl);
	if (vi == NULL) {
		vi = glXChooseVisual(dpy, DefaultScreen(dpy), attributeListDbl);
		swap_flag = 1;
	}
	
	/* create a GLX context */
	cx = glXCreateContext(dpy, vi, 0, GL_TRUE);
	
	/* create a color map */
	cmap = XCreateColormap(dpy, RootWindow(dpy, vi->screen), vi->visual, AllocNone);
	
	/* create a window */
	swa.colormap = cmap;
	swa.border_pixel = 0;
	swa.event_mask = StructureNotifyMask;
	win = XCreateWindow(dpy, RootWindow(dpy, vi->screen), 0, 0, 100, 100,
		0, vi->depth, InputOutput, vi->visual,
		CWBorderPixel|CWColormap|CWEventMask, &swa);
	XMapWindow(dpy, win);
	XIfEvent(dpy, &event, WaitForNotify, (char*)win);
	
	/* connect the context to the window */
	glXMakeCurrent(dpy, win, cx);
	
	/* clear the buffer */
	glClearColor(1,1,0,1);
	glClear(GL_COLOR_BUFFER_BIT);
	glFlush();
	
	if(swap_flag)
		glXSwapBuffers(dpy,win);
	
	/* wait a while */
	sleep(10);
			
	return 0;
}
```

Now, I went looking for examples of other ways that people have done it, and I came across the example on the OpenGL's SDK.  It compiles all fine, but fails to execute.  The following is both its code and the error message:

```
#include <stdio.h>
#include <stdlib.h>
#include <GL/gl.h>
#include <GL/glx.h>

int singleBufferAttributess[] = {
    GLX_DRAWABLE_TYPE, GLX_WINDOW_BIT,
    GLX_RENDER_TYPE,   GLX_RGBA_BIT,
    GLX_RED_SIZE,      1,   /* Request a single buffered color buffer */
    GLX_GREEN_SIZE,    1,   /* with the maximum number of color bits  */
    GLX_BLUE_SIZE,     1,   /* for each component                     */
    None
};

int doubleBufferAttributes[] = {
    GLX_DRAWABLE_TYPE, GLX_WINDOW_BIT,
    GLX_RENDER_TYPE,   GLX_RGBA_BIT,
    GLX_DOUBLEBUFFER,  True,  /* Request a double-buffered color buffer with */
    GLX_RED_SIZE,      1,     /* the maximum number of bits per component    */
    GLX_GREEN_SIZE,    1, 
    GLX_BLUE_SIZE,     1,
    None
};


static Bool WaitForNotify( Display *dpy, XEvent *event, XPointer arg ) {
    return (event->type == MapNotify) && (event->xmap.window == (Window) arg);
}
int main( int argc, char *argv[] )
{
    Display              *dpy;
    Window                xWin;
    XEvent                event;
    XVisualInfo          *vInfo;
    XSetWindowAttributes  swa;
    GLXFBConfig          *fbConfigs;
    GLXContext            context;
    GLXWindow             glxWin;
    int                   swaMask;
    int                   numReturned;
    int                   swapFlag = True;

    /* Open a connection to the X server */
    dpy = XOpenDisplay( NULL );
    if ( dpy == NULL ) {
        printf( "Unable to open a connection to the X server\n" );
        exit( EXIT_FAILURE );
    }

    /* Request a suitable framebuffer configuration - try for a double 
    ** buffered configuration first */
    fbConfigs = glXChooseFBConfig( dpy, DefaultScreen(dpy),
                                   doubleBufferAttributes, &numReturned );

    if ( fbConfigs == NULL ) {  /* no double buffered configs available */
      fbConfigs = glXChooseFBConfig( dpy, DefaultScreen(dpy),
                                     singleBufferAttributess, &numReturned );
      swapFlag = False;
    }

    /* Create an X colormap and window with a visual matching the first
    ** returned framebuffer config */
    vInfo = glXGetVisualFromFBConfig( dpy, fbConfigs[0] );

    swa.border_pixel = 0;
    swa.event_mask = StructureNotifyMask;
    swa.colormap = XCreateColormap( dpy, RootWindow(dpy, vInfo->screen),
                                    vInfo->visual, AllocNone );

    swaMask = CWBorderPixel | CWColormap | CWEventMask;

    xWin = XCreateWindow( dpy, RootWindow(dpy, vInfo->screen), 0, 0, 256, 256,
                          0, vInfo->depth, InputOutput, vInfo->visual,
                          swaMask, &swa );

    /* Create a GLX context for OpenGL rendering */
    context = glXCreateNewContext( dpy, fbConfigs[0], GLX_RGBA_TYPE,
				 NULL, True );

    /* Create a GLX window to associate the frame buffer configuration
    ** with the created X window */
    glxWin = glXCreateWindow( dpy, fbConfigs[0], xWin, NULL );
    
    /* Map the window to the screen, and wait for it to appear */
    XMapWindow( dpy, xWin );
    XIfEvent( dpy, &event, WaitForNotify, (XPointer) xWin );

    /* Bind the GLX context to the Window */
    glXMakeContextCurrent( dpy, glxWin, glxWin, context );

    /* OpenGL rendering ... */
    glClearColor( 1.0, 1.0, 0.0, 1.0 );
    glClear( GL_COLOR_BUFFER_BIT );

    glFlush();
    
    if ( swapFlag )
        glXSwapBuffers( dpy, glxWin );

    sleep( 10 );
    exit( EXIT_SUCCESS );
}

```

```
X Error of failed request:  GLXBadContext
Major opcode of failed request:  162 (GLX)
Minor opcode of failed request:  5 (X_GLXMakeCurrent)
Serial number of failed request:  18
Current serial number in output stream:  18
```

I was wondering if anyone has any clue what is causing this problem and how to fix it without disabling Visual Effects.

~ Marc

---

### Post by skullmunky on 2008-05-29
obvious question, but how do other glx apps behave? 

does using glut work any better?

---

