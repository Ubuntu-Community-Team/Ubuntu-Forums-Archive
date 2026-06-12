---
title: "Programming 3d for linux. poor performance"
date: 2008-01-27
forum: Programming Talk
---

### Post by chisleu on 2008-01-27
I have a 8800gts (640meg) card on a Intel 805@4.0ghz and 2 gigs of ddr2/DC Crucial Balistix.

My 3d performance in windows is pretty fantastic. In Ubuntu (7.10 I think), I used Envy to install the latest nvidia opengl driver. I'm writing opengl. It's easy to tell that it is doing 3d accelleration in my 3d screensaver (the one with the fireworks especially).

The problem comes when linking my opengl tutorial programs. It is a little choppy when I do a simple "bounce" program to bounce a square around the X,Y of the screen. If I make it move swiftly (not insanely fast, like 2 pixel per 10ms) it gets very choppy almost as if it's not 3d accellerated.

Maybe I'm linking the wrong library when I compile? I believe I'm using -lgl -lglut -lglu (IIRC, I'm on a different machine atm.)

Also, when I enable the high end window manager eye candy, the "window wiggle" when you move a window has visible blockiness. It's almost like v-sync isn't enabled and it's skipping frames. Weird.

I do have vsync and double buffering on in my tutorial. =)

What am I doing stupid?
-Chisleu

---

### Post by Lster on 2008-01-27
If you post the code I would be happy to see how it performs on my computer.

---

### Post by chisleu on 2008-01-27
bounce.cpp:

#include "../../shared/gltools.h"	// OpenGL toolkit


// Initial square position and size
GLfloat x = 0.0f;
GLfloat y = 0.0f;
GLfloat rsize = 25;

// Step size in x and y directions
// (number of pixels to move each time)
GLfloat xstep = 1.0f;
GLfloat ystep = 1.0f;

// Keep track of windows changing width and height
GLfloat windowWidth;
GLfloat windowHeight;

///////////////////////////////////////////////////////////
// Called to draw scene
void RenderScene(void)
	{
	// Clear the window with current clearing color
	glClear(GL_COLOR_BUFFER_BIT);

   	// Set current drawing color to red
	//		   R	 G	   B
	glColor3f(.6f, 0.3f, 0.4f);

	// Draw a filled rectangle with current color
	glRectf(x, y, x + rsize, y - rsize);

    // Flush drawing commands and swap
    glutSwapBuffers();
	}

///////////////////////////////////////////////////////////
// Called by GLUT library when idle (window not being
// resized or moved)
void TimerFunction(int value)
    {
    // Reverse direction when you reach left or right edge
    if(x > windowWidth-rsize || x < -windowWidth)
        xstep = -xstep;

    // Reverse direction when you reach top or bottom edge
    if(y > windowHeight || y < -windowHeight + rsize)
        ystep = -ystep;

	// Actually move the square
    x += xstep;
    y += ystep;

    // Check bounds. This is in case the window is made
    // smaller while the rectangle is bouncing and the 
	// rectangle suddenly finds itself outside the new
    // clipping volume
    if(x > (windowWidth-rsize + xstep))
        x = windowWidth-rsize-1;
	else if(x < -(windowWidth + xstep))
		x = -windowWidth -1;

    if(y > (windowHeight + ystep))
        y = windowHeight-1; 
	else if(y < -(windowHeight - rsize + ystep))
		y = -windowHeight + rsize - 1;



     // Redraw the scene with new coordinates
    glutPostRedisplay();
    glutTimerFunc(10,TimerFunction, 1);
    }


///////////////////////////////////////////////////////////
// Setup the rendering state
void SetupRC(void)
    {
    // Set clear color to blue
    glClearColor(0.0f, 0.0f, 0.0f, 1.0f);
    }


///////////////////////////////////////////////////////////
// Called by GLUT library when the window has chanaged size
void ChangeSize(int w, int h)
    {
    GLfloat aspectRatio;

    // Prevent a divide by zero
    if(h == 0)
        h = 1;
		
    // Set Viewport to window dimensions
    glViewport(0, 0, w, h);

    // Reset coordinate system
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();

    // Establish clipping volume (left, right, bottom, top, near, far)
    aspectRatio = (GLfloat)w / (GLfloat)h;
    if (w <= h) 
        {
        windowWidth = 100;
        windowHeight = 100 / aspectRatio;
        glOrtho (-100.0, 100.0, -windowHeight, windowHeight, 1.0, -1.0);
        }
    else 
        {
        windowWidth = 100 * aspectRatio;
        windowHeight = 100;
        glOrtho (-windowWidth, windowWidth, -100.0, 100.0, 1.0, -1.0);
        }

    glMatrixMode(GL_MODELVIEW);
    glLoadIdentity();
    }

///////////////////////////////////////////////////////////
// Main program entry point
int main(int argc, char* argv[])
	{
	glutInit(&argc, argv);
	glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGBA);
	glutInitWindowSize(800,600);
    glutCreateWindow("Bounce");
	glutDisplayFunc(RenderScene);
    glutReshapeFunc(ChangeSize);
	glutTimerFunc(10, TimerFunction, 1);

	SetupRC();

	glutMainLoop();
        
    return 0;
    }


=====CUT=====
gltools.h:

#ifdef linux
#include "GLee.h"
#include <GL/gl.h>
#include <GL/glu.h>
#include <glut.h>
#include <stdlib.h>

// Just ignore sleep in linux too
#define Sleep(x)
#endif


#ifdef linux
typedef GLvoid (*CallBack)();
#else

#ifndef WIN32
typedef GLvoid (*CallBack)(...);            //  XCode (GNU) style
#else
typedef GLvoid (_stdcall *CallBack)();      // Visual C++ style
#endif

#endif

// Needed for NURBS callbacks... VC++ vs. GNU
/*#ifndef WIN32
#define CALLBACK (GLvoid (*)(...))
#else
#define CALLBACK (GLvoid (__stdcall*)())
#endif
*/

// Universal includes
#include <math.h>



// There is a static block allocated for loading shaders to prevent heap fragmentation
#define MAX_SHADER_LENGTH   8192

    
///////////////////////////////////////////////////////
// Macros for big/little endian happiness
// These are intentionally written to be easy to understand what they 
// are doing... no flames please on the inefficiency of these.
#ifdef __BIG_ENDIAN__
///////////////////////////////////////////////////////////
// This function says, "this pointer is a little endian value"
// If the value must be changed it is... otherwise, this
// function is defined away below (on Intel systems for example)
inline void LITTLE_ENDIAN_WORD(void *pWord)
	{
    unsigned char *pBytes = (unsigned char *)pWord;
    unsigned char temp;
    
    temp = pBytes[0];
    pBytes[0] = pBytes[1];
    pBytes[1] = temp;
	}

///////////////////////////////////////////////////////////
// This function says, "this pointer is a little endian value"
// If the value must be changed it is... otherwise, this
// function is defined away below (on Intel systems for example)
inline void LITTLE_ENDIAN_DWORD(void *pWord)
	{
    unsigned char *pBytes = (unsigned char *)pWord;
    unsigned char temp;
    
    // Swap outer bytes
    temp = pBytes[3];
    pBytes[3] = pBytes[0];
    pBytes[0] = temp;
    
    // Swap inner bytes
    temp = pBytes[1];
    pBytes[1] = pBytes[2];
    pBytes[2] = temp;
	}
#else

// Define them away on little endian systems
#define LITTLE_ENDIAN_WORD 
#define LITTLE_ENDIAN_DWORD 
#endif


///////////////////////////////////////////////////////////////////////////////
//         THE LIBRARY....
///////////////////////////////////////////////////////////////////////////////

/////////////////////////////////////////////////////////////////////////////////////
// Load a .TGA file
GLbyte *gltLoadTGA(const char *szFileName, GLint *iWidth, GLint *iHeight, GLint *iComponents, GLenum *eFormat);

// Capute the frame buffer and write it as a .tga
GLint gltWriteTGA(const char *szFileName);

// Draw a Torus
void gltDrawTorus(GLfloat majorRadius, GLfloat minorRadius, GLint numMajor, GLint numMinor);

// Just draw a simple sphere with normals and texture coordinates
void gltDrawSphere(GLfloat fRadius, GLint iSlices, GLint iStacks);

// Draw a 3D unit Axis set
void gltDrawUnitAxes(void);

// Shader loading support
bool bLoadShaderFile(const char *szFile, GLhandleARB shader);
GLhandleARB gltLoadShaderPair(const char *szVertexProg, const char *szFragmentProg);

// Get the OpenGL version, returns fals on error
bool gltGetOpenGLVersion(int &nMajor, int &nMinor);

// Check to see if an exension is supported
int gltIsExtSupported(const char *szExtension);

// Get the function pointer for an extension
void *gltGetExtensionPointer(const char *szFunctionName);

---

### Post by lnostdal on 2008-01-28
```

lars@ibmr52:~$ glxinfo | grep direct
direct rendering: Yes

```

or -- no?

---

### Post by chisleu on 2008-01-29
Yes

---

