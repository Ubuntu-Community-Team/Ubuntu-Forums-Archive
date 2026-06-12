---
title: "Problems with C++ and OpenGL"
date: 2009-03-01
forum: Programming Talk
---

### Post by Gediminas2 on 2009-03-01
Hello everybody, I'm working on a project for my University, 
I found openGL examples in C, all works fine; however I need to do everything in c++.

After trying to convert the code to c++, g++ doesn't compile it. The error I get is:
```
$ g++ PlanetGL.c++
PlanetGL.c++: In member function ‘void PlanetGL::DrawGLScene()’:
PlanetGL.c++:244: warning: deprecated conversion from string constant to ‘char*’
PlanetGL.c++:245: warning: deprecated conversion from string constant to ‘char*’
PlanetGL.c++:247: warning: deprecated conversion from string constant to ‘char*’
PlanetGL.c++:250: warning: deprecated conversion from string constant to ‘char*’
PlanetGL.c++:253: warning: deprecated conversion from string constant to ‘char*’
PlanetGL.c++:256: warning: deprecated conversion from string constant to ‘char*’
PlanetGL.c++:257: warning: deprecated conversion from string constant to ‘char*’
PlanetGL.c++:279: warning: deprecated conversion from string constant to ‘char*’
PlanetGL.c++: In member function ‘int PlanetGL::main(int, char**)’:
PlanetGL.c++:703: error: cannot convert ‘void (PlanetGL::*)()’ to ‘void (*)()’ for argument ‘1’ to ‘void glutDisplayFunc(void (*)())’
PlanetGL.c++:709: error: cannot convert ‘void (PlanetGL::*)()’ to ‘void (*)()’ for argument ‘1’ to ‘void glutIdleFunc(void (*)())’
PlanetGL.c++:712: error: cannot convert ‘void (PlanetGL::*)(GLsizei, GLsizei)’ to ‘void (*)(int, int)’ for argument ‘1’ to ‘void glutReshapeFunc(void (*)(int, int))’
PlanetGL.c++:715: error: cannot convert ‘void (PlanetGL::*)(unsigned char, int, int)’ to ‘void (*)(unsigned char, int, int)’ for argument ‘1’ to ‘void glutKeyboardFunc(void (*)(unsigned char, int, int))’
PlanetGL.c++:718: error: cannot convert ‘void (PlanetGL::*)(int, int, int)’ to ‘void (*)(int, int, int)’ for argument ‘1’ to ‘void glutSpecialFunc(void (*)(int, int, int))’

```

Now the code in question is (the part that doesn't compile):
```
int PlanetGL::main(int argc, char **argv) 
{  

  /* Initialize GLUT state - glut will take any command line arguments that pertain to it or 
     X Windows - look at its documentation at http://reality.sgi.com/mjk/spec3/spec3.html */  
   
   getCords(); 
   glutInit(&argc, argv);  

  /* Select type of Display mode:   
     Double buffer 
     RGBA color
     Alpha components supported (use GLUT_ALPHA)
     Depth buffer */  
  glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE |  GLUT_DEPTH );  

  /* get a 640 x 480 window */
  glutInitWindowSize(1024, 786);  

  /* the window starts at the upper left corner of the screen */
  glutInitWindowPosition(0, 0);  

  /* Open a window */  
  window = glutCreateWindow("Planetos (GL)");  

  /* Register the function to do all our OpenGL drawing. */
  glutDisplayFunc(&PlanetGL::DrawGLScene);
  
  /* Go fullscreen.  This is as soon as possible. */
  glutFullScreen();

  /* Even if there are no events, redraw our gl scene. */
  glutIdleFunc(&PlanetGL::DrawGLScene);

  /* Register the function called when our window is resized. */
  glutReshapeFunc(&PlanetGL::ReSizeGLScene);

  /* Register the function called when the keyboard is pressed. */
  glutKeyboardFunc(&PlanetGL::keyPressed);

  /* Register the function called when special keys (arrows, page down, etc) are pressed. */
  glutSpecialFunc(&PlanetGL::specialKeyPressed);

  /* Initialize our window. */
  InitGL(1024, 786);
  
  /* Start Event Processing Engine */  
  glutMainLoop();  

  return 1;
}
```

can anyone help me with this issue?

---

### Post by dwhitney67 on 2009-03-01
Gediminas2

I do not have OpenGL experience, however I have a couple of questions...

1.  Is your PlanetGL a namespace or a class name?

2.  If it is a class name, are the methods declared 'static'?

---

### Post by Gediminas2 on 2009-03-01
I's a class name, the methods are not static. I can't really imagine them being static. They all use global variables

---

### Post by dwhitney67 on 2009-03-01
You will need to make them static, otherwise the OpenGL functions will (probably) not be able to call them.

To call a class method, two things are needed... an instance of the class object, and the address of the function.

If your methods are static, then you do not need the instance of the class object.

When porting from C to C++, the easiest thing to do is to place your C functions in a namespace.

P.S.  Declaring your methods as static will not impact the declarations of your global variables (at least I think so!??).

---

### Post by Taras.M.K on 2009-03-01
Sopposedly, you tried to change "char*" strings to "string", it can be good for your internal data, but to OpenGL they still need to be "char*" (you may use them through str.c_str()). And if you want to pass any class member function it can be necessary to use static members.

Hard to say more, there is no much info about your code.

---

### Post by Gediminas2 on 2009-03-01
The methods simply can't be static.
If I try this:
```

...
PlanetGL Obj;
...
glutDisplayFunc(&Obj.DrawGLScene);
...

```

I get:
```
PlanetGL.c++:703: error: ISO C++ forbids taking the address of a bound member function to form a pointer to member function.  Say &#8216;&PlanetGL::DrawGLScene&#8217;
```

How do I put the functions under a namespace? And what would I gain from it?

Sorry, just a newbie in programming :(

And the char* vs string is not even an error. :) Just nobody codes this way anymore :D

And if you want to see the full code (it's very messy now) : [http://gedas.autoiranga.com/pub/Planetos.bin.6.tar.bz2](http://gedas.autoiranga.com/pub/Planetos.bin.6.tar.bz2)

---

### Post by dwhitney67 on 2009-03-01
> **Gediminas2 said:**
> The methods simply can't be static.
If I try this:
```

...
PlanetGL Obj;
...
glutDisplayFunc(&Obj.DrawGLScene);
...

```
...

If DrawGLScene() were statically declared, then this would obviate the need to instantiate PlanetGL (as Obj).

Your code would be:
```

glutDisplayFunc(&PlanetGL::DrawGLScene);

```

If you insist on having non-static methods in PlanetGL, then you will need to pass to any OpenGL method the address of the instance, and the function name.

For example (and not that this will work with the glutDisplayFunc() API)
```

glutDisplayFunc(&Obj, &PlanetGL::DrawGLScene);

```
Since the code above will not work, you either have to find (or build) an equivalent OpenGL API for C++ applications, or go with the static declaration of your methods.

Btw, there is basically no difference between a static declaration of a class method when comparing it to a free-floating C function.

I.e., the following are the same:

```

void myFunction()
{
}

class MyClass
{
  public:
    static void myFunction()
    {
    }
}

```
Obviously with the class style you will need to preface the function name with the class scope operator; in the case above, "MyClass::".

P.S.  Any member data in the class that are required by myFunction() will also need to be declared static.

---

### Post by Gediminas2 on 2009-03-01
I tried making everything static, since all data I use is needed by those functions:
```
class PlanetGL
{
   public:
   PlanetGL();
   static void BuildFont();
   static void KillFont();
   static void glPrint(char *text);
   static void DrawGLScene();
   static int ImageLoad(char *filename, Image *image);
   static void LoadGLTextures();
   static void InitGL(GLsizei Width, GLsizei Height);
   static void ReSizeGLScene(GLsizei Width, GLsizei Height);
   static void keyPressed(unsigned char key, int x, int y);
   static void specialKeyPressed(int key, int x, int y);
   static int main(int argc, char **argv);
   static int getCords();

   private:
   static int window,light,blend;
   static GLuint filter;		// Which Filter To Use (nearest/linear/mipmapped)
   static GLuint texture[9];		// Storage for 9 textures.
   static GLuint object;
   static int objects;
   static GLfloat xrot;		// X Rotation
   static GLfloat yrot;		// Y Rotation
   static GLfloat xspeed;		// x rotation speed
   static GLfloat yspeed;		// y rotation speed
   static cord cam;			// Camera position
   static int orbita;
   static float orsize;
   static int PlanetName;
   static float *CirKordX, *CirKordY, CirKordZ;
   static float k[9];
   static float kf, kspeed;
   static int ZoomSpeed;
   static double PlanetSpeed[9];
   static GLuint base;        	 	// base display list for the font set.
   static GLfloat cnt1;       	    	// 1st counter used to move text & for coloring.
   static GLfloat cnt2;           	// 2nd counter used to move text & for coloring.
   static GLUquadricObj *quadratic;	// Storage For Our Quadratic Objects
   static GLfloat LightAmbient[4];
   static GLfloat LightDiffuse[4];
   static GLfloat LightPosition[4];
   static CO Plan[9];
   
};
```

Obviously it didn't went well
```
 g++ PlanetGL.c++
In file included from PlanetGL.c++:9:
PlanetGL.h++:21: error: constructor cannot be static member function
PlanetGL.c++: In static member function &#8216;static void PlanetGL::DrawGLScene()&#8217;:
PlanetGL.c++:244: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:245: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:247: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:250: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:253: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:256: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:257: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:279: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++: In static member function &#8216;static int PlanetGL::main(int, char**)&#8217;:
PlanetGL.c++:703: error: cannot convert &#8216;PlanetGL*&#8217; to &#8216;void (*)()&#8217; for argument &#8216;1&#8217; to &#8216;void glutDisplayFunc(void (*)())&#8217;
PlanetGL.c++:709: error: cannot convert &#8216;PlanetGL*&#8217; to &#8216;void (*)()&#8217; for argument &#8216;1&#8217; to &#8216;void glutIdleFunc(void (*)())&#8217;
PlanetGL.c++:712: error: cannot convert &#8216;PlanetGL*&#8217; to &#8216;void (*)(int, int)&#8217; for argument &#8216;1&#8217; to &#8216;void glutReshapeFunc(void (*)(int, int))&#8217;
PlanetGL.c++:715: error: cannot convert &#8216;PlanetGL*&#8217; to &#8216;void (*)(unsigned char, int, int)&#8217; for argument &#8216;1&#8217; to &#8216;void glutKeyboardFunc(void (*)(unsigned char, int, int))&#8217;
PlanetGL.c++:718: error: cannot convert &#8216;PlanetGL*&#8217; to &#8216;void (*)(int, int, int)&#8217; for argument &#8216;1&#8217; to &#8216;void glutSpecialFunc(void (*)(int, int, int))&#8217;
gedas@gedas-desktop:~/OGL/planetos$ g++ PlanetGL.c++
In file included from PlanetGL.c++:9:
PlanetGL.h++:21: error: constructor cannot be static member function
PlanetGL.c++: In static member function &#8216;static void PlanetGL::DrawGLScene()&#8217;:
PlanetGL.c++:244: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:245: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:247: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:250: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:253: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:256: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:257: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:279: warning: deprecated conversion from string constant to &#8216;char*&#8217;
gedas@gedas-desktop:~/OGL/planetos$ g++ PlanetGL.c++ -o planetos.cpp
In file included from PlanetGL.c++:9:
PlanetGL.h++:21: error: constructor cannot be static member function
PlanetGL.c++: In static member function &#8216;static void PlanetGL::DrawGLScene()&#8217;:
PlanetGL.c++:244: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:245: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:247: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:250: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:253: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:256: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:257: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:279: warning: deprecated conversion from string constant to &#8216;char*&#8217;
gedas@gedas-desktop:~/OGL/planetos$ g++ PlanetGL.c++ -o planetos.cpp
PlanetGL.c++: In static member function &#8216;static void PlanetGL::DrawGLScene()&#8217;:
PlanetGL.c++:244: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:245: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:247: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:250: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:253: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:256: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:257: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:279: warning: deprecated conversion from string constant to &#8216;char*&#8217;
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
/tmp/ccfqE9zq.o: In function `PlanetGL::PlanetGL()':
PlanetGL.c++:(.text+0x5): undefined reference to `PlanetGL::light'
PlanetGL.c++:(.text+0xf): undefined reference to `PlanetGL::blend'
PlanetGL.c++:(.text+0x19): undefined reference to `PlanetGL::objects'
PlanetGL.c++:(.text+0x23): undefined reference to `PlanetGL::filter'
PlanetGL.c++:(.text+0x2d): undefined reference to `PlanetGL::object'
PlanetGL.c++:(.text+0x3b): undefined reference to `PlanetGL::xrot'
PlanetGL.c++:(.text+0x45): undefined reference to `PlanetGL::yrot'
PlanetGL.c++:(.text+0x4f): undefined reference to `PlanetGL::xspeed'
PlanetGL.c++:(.text+0x59): undefined reference to `PlanetGL::yspeed'
PlanetGL.c++:(.text+0x63): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x6d): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x77): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x7d): undefined reference to `PlanetGL::orbita'
PlanetGL.c++:(.text+0x8b): undefined reference to `PlanetGL::orsize'
PlanetGL.c++:(.text+0x91): undefined reference to `PlanetGL::PlanetName'
PlanetGL.c++:(.text+0x9f): undefined reference to `PlanetGL::kf'
PlanetGL.c++:(.text+0xa9): undefined reference to `PlanetGL::kspeed'
PlanetGL.c++:(.text+0xaf): undefined reference to `PlanetGL::ZoomSpeed'
/tmp/ccfqE9zq.o: In function `PlanetGL::PlanetGL()':
PlanetGL.c++:(.text+0xbf): undefined reference to `PlanetGL::light'
PlanetGL.c++:(.text+0xc9): undefined reference to `PlanetGL::blend'
PlanetGL.c++:(.text+0xd3): undefined reference to `PlanetGL::objects'
PlanetGL.c++:(.text+0xdd): undefined reference to `PlanetGL::filter'
PlanetGL.c++:(.text+0xe7): undefined reference to `PlanetGL::object'
PlanetGL.c++:(.text+0xf5): undefined reference to `PlanetGL::xrot'
PlanetGL.c++:(.text+0xff): undefined reference to `PlanetGL::yrot'
PlanetGL.c++:(.text+0x109): undefined reference to `PlanetGL::xspeed'
PlanetGL.c++:(.text+0x113): undefined reference to `PlanetGL::yspeed'
PlanetGL.c++:(.text+0x11d): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x127): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x131): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x137): undefined reference to `PlanetGL::orbita'
PlanetGL.c++:(.text+0x145): undefined reference to `PlanetGL::orsize'
PlanetGL.c++:(.text+0x14b): undefined reference to `PlanetGL::PlanetName'
PlanetGL.c++:(.text+0x159): undefined reference to `PlanetGL::kf'
PlanetGL.c++:(.text+0x163): undefined reference to `PlanetGL::kspeed'
PlanetGL.c++:(.text+0x169): undefined reference to `PlanetGL::ZoomSpeed'
/tmp/ccfqE9zq.o: In function `PlanetGL::specialKeyPressed(int, int, int)':
PlanetGL.c++:(.text+0x21d): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x222): undefined reference to `PlanetGL::ZoomSpeed'
PlanetGL.c++:(.text+0x23a): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x242): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x247): undefined reference to `PlanetGL::ZoomSpeed'
PlanetGL.c++:(.text+0x25f): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x267): undefined reference to `PlanetGL::xspeed'
PlanetGL.c++:(.text+0x271): undefined reference to `PlanetGL::xspeed'
PlanetGL.c++:(.text+0x279): undefined reference to `PlanetGL::xspeed'
PlanetGL.c++:(.text+0x283): undefined reference to `PlanetGL::xspeed'
PlanetGL.c++:(.text+0x28b): undefined reference to `PlanetGL::yspeed'
PlanetGL.c++:(.text+0x295): undefined reference to `PlanetGL::yspeed'
PlanetGL.c++:(.text+0x29d): undefined reference to `PlanetGL::yspeed'
PlanetGL.c++:(.text+0x2a7): undefined reference to `PlanetGL::yspeed'
/tmp/ccfqE9zq.o: In function `PlanetGL::keyPressed(unsigned char, int, int)':
PlanetGL.c++:(.text+0x2e7): undefined reference to `PlanetGL::window'
PlanetGL.c++:(.text+0x2ef): undefined reference to `glutDestroyWindow'
PlanetGL.c++:(.text+0x300): undefined reference to `PlanetGL::light'
PlanetGL.c++:(.text+0x315): undefined reference to `PlanetGL::light'
PlanetGL.c++:(.text+0x322): undefined reference to `PlanetGL::light'
PlanetGL.c++:(.text+0x327): undefined reference to `PlanetGL::light'
PlanetGL.c++:(.text+0x33c): undefined reference to `PlanetGL::light'
PlanetGL.c++:(.text+0x34c): undefined reference to `glDisable'
PlanetGL.c++:(.text+0x35d): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x367): undefined reference to `PlanetGL::filter'
PlanetGL.c++:(.text+0x37c): undefined reference to `PlanetGL::filter'
PlanetGL.c++:(.text+0x384): undefined reference to `PlanetGL::filter'
PlanetGL.c++:(.text+0x389): undefined reference to `PlanetGL::filter'
PlanetGL.c++:(.text+0x394): undefined reference to `PlanetGL::filter'
/tmp/ccfqE9zq.o:PlanetGL.c++:(.text+0x39d): more undefined references to `PlanetGL::filter' follow
/tmp/ccfqE9zq.o: In function `PlanetGL::keyPressed(unsigned char, int, int)':
PlanetGL.c++:(.text+0x3b7): undefined reference to `PlanetGL::blend'
PlanetGL.c++:(.text+0x3cc): undefined reference to `PlanetGL::blend'
PlanetGL.c++:(.text+0x3d9): undefined reference to `PlanetGL::blend'
PlanetGL.c++:(.text+0x3de): undefined reference to `PlanetGL::blend'
PlanetGL.c++:(.text+0x3f3): undefined reference to `PlanetGL::blend'
PlanetGL.c++:(.text+0x403): undefined reference to `glDisable'
PlanetGL.c++:(.text+0x40f): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x420): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x42c): undefined reference to `glDisable'
PlanetGL.c++:(.text+0x436): undefined reference to `PlanetGL::object'
PlanetGL.c++:(.text+0x43e): undefined reference to `PlanetGL::object'
PlanetGL.c++:(.text+0x443): undefined reference to `PlanetGL::object'
PlanetGL.c++:(.text+0x452): undefined reference to `PlanetGL::object'
PlanetGL.c++:(.text+0x461): undefined reference to `PlanetGL::kspeed'
PlanetGL.c++:(.text+0x46b): undefined reference to `PlanetGL::kspeed'
PlanetGL.c++:(.text+0x471): undefined reference to `PlanetGL::kspeed'
PlanetGL.c++:(.text+0x4a5): undefined reference to `PlanetGL::kspeed'
PlanetGL.c++:(.text+0x4af): undefined reference to `PlanetGL::kspeed'
/tmp/ccfqE9zq.o:PlanetGL.c++:(.text+0x4b5): more undefined references to `PlanetGL::kspeed' follow
/tmp/ccfqE9zq.o: In function `PlanetGL::keyPressed(unsigned char, int, int)':
PlanetGL.c++:(.text+0x4e8): undefined reference to `PlanetGL::orbita'
PlanetGL.c++:(.text+0x4f3): undefined reference to `PlanetGL::orbita'
PlanetGL.c++:(.text+0x4ff): undefined reference to `PlanetGL::orbita'
PlanetGL.c++:(.text+0x508): undefined reference to `PlanetGL::orbita'
PlanetGL.c++:(.text+0x523): undefined reference to `PlanetGL::ZoomSpeed'
PlanetGL.c++:(.text+0x52c): undefined reference to `PlanetGL::ZoomSpeed'
PlanetGL.c++:(.text+0x547): undefined reference to `PlanetGL::ZoomSpeed'
PlanetGL.c++:(.text+0x550): undefined reference to `PlanetGL::ZoomSpeed'
PlanetGL.c++:(.text+0x56b): undefined reference to `PlanetGL::ZoomSpeed'
/tmp/ccfqE9zq.o:PlanetGL.c++:(.text+0x574): more undefined references to `PlanetGL::ZoomSpeed' follow
/tmp/ccfqE9zq.o: In function `PlanetGL::keyPressed(unsigned char, int, int)':
PlanetGL.c++:(.text+0x667): undefined reference to `PlanetGL::orsize'
PlanetGL.c++:(.text+0x675): undefined reference to `PlanetGL::orsize'
PlanetGL.c++:(.text+0x67b): undefined reference to `PlanetGL::orsize'
PlanetGL.c++:(.text+0x6af): undefined reference to `PlanetGL::orsize'
PlanetGL.c++:(.text+0x6bd): undefined reference to `PlanetGL::orsize'
/tmp/ccfqE9zq.o:PlanetGL.c++:(.text+0x6c3): more undefined references to `PlanetGL::orsize' follow
/tmp/ccfqE9zq.o: In function `PlanetGL::keyPressed(unsigned char, int, int)':
PlanetGL.c++:(.text+0x6f7): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x726): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x755): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x785): undefined reference to `PlanetGL::PlanetName'
PlanetGL.c++:(.text+0x790): undefined reference to `PlanetGL::PlanetName'
PlanetGL.c++:(.text+0x79c): undefined reference to `PlanetGL::PlanetName'
/tmp/ccfqE9zq.o: In function `ReSizeGLScene(int, int)':
PlanetGL.c++:(.text+0x7eb): undefined reference to `glViewport'
PlanetGL.c++:(.text+0x7f7): undefined reference to `glMatrixMode'
PlanetGL.c++:(.text+0x7fc): undefined reference to `glLoadIdentity'
PlanetGL.c++:(.text+0x82a): undefined reference to `gluPerspective'
PlanetGL.c++:(.text+0x836): undefined reference to `glMatrixMode'
/tmp/ccfqE9zq.o: In function `PlanetGL::LoadGLTextures()':
PlanetGL.c++:(.text+0xcc6): undefined reference to `PlanetGL::texture'
PlanetGL.c++:(.text+0xcd2): undefined reference to `glGenTextures'
PlanetGL.c++:(.text+0xcee): undefined reference to `PlanetGL::texture'
PlanetGL.c++:(.text+0xcfe): undefined reference to `glBindTexture'
PlanetGL.c++:(.text+0xd1a): undefined reference to `glTexParameteri'
PlanetGL.c++:(.text+0xd36): undefined reference to `glTexParameteri'
PlanetGL.c++:(.text+0xda7): undefined reference to `glTexImage2D'
PlanetGL.c++:(.text+0xdb3): undefined reference to `PlanetGL::objects'
/tmp/ccfqE9zq.o: In function `PlanetGL::glPrint(char*)':
PlanetGL.c++:(.text+0xe34): undefined reference to `glPushAttrib'
PlanetGL.c++:(.text+0xe39): undefined reference to `PlanetGL::base'
PlanetGL.c++:(.text+0xe44): undefined reference to `glListBase'
PlanetGL.c++:(.text+0xe68): undefined reference to `glCallLists'
PlanetGL.c++:(.text+0xe6d): undefined reference to `glPopAttrib'
/tmp/ccfqE9zq.o: In function `PlanetGL::DrawGLScene()':
PlanetGL.c++:(.text+0xe82): undefined reference to `glClear'
PlanetGL.c++:(.text+0xe87): undefined reference to `glLoadIdentity'
PlanetGL.c++:(.text+0xe8c): undefined reference to `PlanetGL::object'
PlanetGL.c++:(.text+0xeab): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0xeb1): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0xee0): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0xee6): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0xeec): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0xf0e): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0xf19): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0xf1f): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0xf4e): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0xf54): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0xf5a): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0xf7c): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0xf87): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0xf8d): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0xfbc): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0xfc2): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0xfc8): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0xfea): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0xff5): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0xffb): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x102a): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x1030): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0x1036): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x1058): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x1063): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0x1069): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x1098): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x109e): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0x10a4): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x10c6): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x10d1): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0x10d7): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x1106): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x110c): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0x1112): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x1134): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x113f): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0x1145): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x1174): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x117a): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0x1180): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x11a2): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x11aa): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0x11b0): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x11df): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x11e5): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0x11eb): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x120d): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x1219): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x1223): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x1228): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x122e): undefined reference to `PlanetGL::cam'
/tmp/ccfqE9zq.o:PlanetGL.c++:(.text+0x1234): more undefined references to `PlanetGL::cam' follow
/tmp/ccfqE9zq.o: In function `PlanetGL::DrawGLScene()':
PlanetGL.c++:(.text+0x1244): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x1249): undefined reference to `PlanetGL::object'
PlanetGL.c++:(.text+0x1257): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x126b): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x1281): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x1286): undefined reference to `PlanetGL::orbita'
PlanetGL.c++:(.text+0x12ac): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x12c0): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x12d6): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x12e9): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x12fd): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x1313): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x1326): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x133c): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x1352): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x1357): undefined reference to `PlanetGL::orbita'
PlanetGL.c++:(.text+0x136e): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x137c): undefined reference to `PlanetGL::cam'
PlanetGL.c++:(.text+0x1392): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x1397): undefined reference to `PlanetGL::PlanetName'
PlanetGL.c++:(.text+0x13bd): undefined reference to `PlanetGL::yrot'
PlanetGL.c++:(.text+0x13e0): undefined reference to `glRotatef'
PlanetGL.c++:(.text+0x13e6): undefined reference to `PlanetGL::xrot'
PlanetGL.c++:(.text+0x1409): undefined reference to `glRotatef'
PlanetGL.c++:(.text+0x140e): undefined reference to `PlanetGL::texture'
PlanetGL.c++:(.text+0x141e): undefined reference to `glBindTexture'
PlanetGL.c++:(.text+0x1423): undefined reference to `PlanetGL::quadratic'
PlanetGL.c++:(.text+0x1445): undefined reference to `gluSphere'
PlanetGL.c++:(.text+0x144a): undefined reference to `PlanetGL::texture'
PlanetGL.c++:(.text+0x145a): undefined reference to `glBindTexture'
PlanetGL.c++:(.text+0x1460): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0x1466): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x1495): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0x149b): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x14ce): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x14d3): undefined reference to `PlanetGL::quadratic'
PlanetGL.c++:(.text+0x14f5): undefined reference to `gluSphere'
PlanetGL.c++:(.text+0x14fb): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0x1501): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x1530): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0x1536): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x1569): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x156e): undefined reference to `PlanetGL::PlanetName'
PlanetGL.c++:(.text+0x1578): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0x157e): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x15ad): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0x15b3): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x15dd): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x15ef): undefined reference to `PlanetGL::orbita'
PlanetGL.c++:(.text+0x1609): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0x1622): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0x164c): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x1652): undefined reference to `PlanetGL::orsize'
PlanetGL.c++:(.text+0x165a): undefined reference to `PlanetGL::orsize'
PlanetGL.c++:(.text+0x1661): undefined reference to `PlanetGL::quadratic'
PlanetGL.c++:(.text+0x1681): undefined reference to `gluDisk'
PlanetGL.c++:(.text+0x1687): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0x16a0): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0x16ca): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x16f1): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x16f7): undefined reference to `PlanetGL::kspeed'
PlanetGL.c++:(.text+0x1701): undefined reference to `PlanetGL::PlanetSpeed'
PlanetGL.c++:(.text+0x1712): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x171c): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x1734): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x173e): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x175c): undefined reference to `PlanetGL::k'
PlanetGL.c++:(.text+0x176f): undefined reference to `PlanetGL::xspeed'
PlanetGL.c++:(.text+0x1774): undefined reference to `PlanetGL::xrot'
PlanetGL.c++:(.text+0x1779): undefined reference to `PlanetGL::yspeed'
PlanetGL.c++:(.text+0x177e): undefined reference to `PlanetGL::yrot'
PlanetGL.c++:(.text+0x1784): undefined reference to `PlanetGL::yspeed'
PlanetGL.c++:(.text+0x1792): undefined reference to `PlanetGL::xspeed'
PlanetGL.c++:(.text+0x17b1): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x17b6): undefined reference to `glutSwapBuffers'
/tmp/ccfqE9zq.o: In function `PlanetGL::KillFont()':
PlanetGL.c++:(.text+0x17c3): undefined reference to `PlanetGL::base'
PlanetGL.c++:(.text+0x17d3): undefined reference to `glDeleteLists'
/tmp/ccfqE9zq.o: In function `PlanetGL::BuildFont()':
PlanetGL.c++:(.text+0x17e8): undefined reference to `glGenLists'
PlanetGL.c++:(.text+0x17ed): undefined reference to `PlanetGL::base'
PlanetGL.c++:(.text+0x17f9): undefined reference to `XOpenDisplay'
PlanetGL.c++:(.text+0x180f): undefined reference to `XLoadQueryFont'
PlanetGL.c++:(.text+0x182b): undefined reference to `XLoadQueryFont'
PlanetGL.c++:(.text+0x1845): undefined reference to `PlanetGL::base'
PlanetGL.c++:(.text+0x1869): undefined reference to `glXUseXFont'
PlanetGL.c++:(.text+0x187b): undefined reference to `XFreeFont'
PlanetGL.c++:(.text+0x1886): undefined reference to `XCloseDisplay'
/tmp/ccfqE9zq.o: In function `PlanetGL::InitGL(int, int)':
PlanetGL.c++:(.text+0x189f): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x18c7): undefined reference to `glClearColor'
PlanetGL.c++:(.text+0x18d1): undefined reference to `glClearDepth'
PlanetGL.c++:(.text+0x18dd): undefined reference to `glDepthFunc'
PlanetGL.c++:(.text+0x18e9): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x18f5): undefined reference to `glShadeModel'
PlanetGL.c++:(.text+0x1901): undefined reference to `glMatrixMode'
PlanetGL.c++:(.text+0x1906): undefined reference to `glLoadIdentity'
PlanetGL.c++:(.text+0x1934): undefined reference to `gluPerspective'
PlanetGL.c++:(.text+0x1940): undefined reference to `glMatrixMode'
PlanetGL.c++:(.text+0x194d): undefined reference to `PlanetGL::LightAmbient'
PlanetGL.c++:(.text+0x1961): undefined reference to `glLightfv'
PlanetGL.c++:(.text+0x1969): undefined reference to `PlanetGL::LightDiffuse'
PlanetGL.c++:(.text+0x197d): undefined reference to `glLightfv'
PlanetGL.c++:(.text+0x1985): undefined reference to `PlanetGL::LightPosition'
PlanetGL.c++:(.text+0x1999): undefined reference to `glLightfv'
PlanetGL.c++:(.text+0x19a5): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x19b9): undefined reference to `glBlendFunc'
PlanetGL.c++:(.text+0x19e1): undefined reference to `glColor4f'
PlanetGL.c++:(.text+0x19e6): undefined reference to `gluNewQuadric'
PlanetGL.c++:(.text+0x19eb): undefined reference to `PlanetGL::quadratic'
PlanetGL.c++:(.text+0x19f0): undefined reference to `PlanetGL::quadratic'
PlanetGL.c++:(.text+0x1a00): undefined reference to `gluQuadricNormals'
PlanetGL.c++:(.text+0x1a05): undefined reference to `PlanetGL::quadratic'
PlanetGL.c++:(.text+0x1a15): undefined reference to `gluQuadricTexture'
/tmp/ccfqE9zq.o: In function `PlanetGL::getCords()':
PlanetGL.c++:(.text+0x1a40): undefined reference to `PlanetGL::LightAmbient'
PlanetGL.c++:(.text+0x1a4a): undefined reference to `PlanetGL::LightAmbient'
PlanetGL.c++:(.text+0x1a54): undefined reference to `PlanetGL::LightAmbient'
PlanetGL.c++:(.text+0x1a5e): undefined reference to `PlanetGL::LightAmbient'
PlanetGL.c++:(.text+0x1a68): undefined reference to `PlanetGL::LightDiffuse'
PlanetGL.c++:(.text+0x1a72): undefined reference to `PlanetGL::LightDiffuse'
PlanetGL.c++:(.text+0x1a7c): undefined reference to `PlanetGL::LightDiffuse'
PlanetGL.c++:(.text+0x1a86): undefined reference to `PlanetGL::LightDiffuse'
PlanetGL.c++:(.text+0x1a90): undefined reference to `PlanetGL::LightPosition'
PlanetGL.c++:(.text+0x1a9a): undefined reference to `PlanetGL::LightPosition'
PlanetGL.c++:(.text+0x1aa4): undefined reference to `PlanetGL::LightPosition'
PlanetGL.c++:(.text+0x1aae): undefined reference to `PlanetGL::LightPosition'
PlanetGL.c++:(.text+0x1c93): undefined reference to `PlanetGL::Plan'
PlanetGL.c++:(.text+0x1cb0): undefined reference to `PlanetGL::Plan'
PlanetGL.c++:(.text+0x1ce4): undefined reference to `PlanetGL::Plan'
PlanetGL.c++:(.text+0x1d01): undefined reference to `PlanetGL::Plan'
PlanetGL.c++:(.text+0x1d18): undefined reference to `PlanetGL::Plan'
/tmp/ccfqE9zq.o:PlanetGL.c++:(.text+0x1da9): more undefined references to `PlanetGL::Plan' follow
/tmp/ccfqE9zq.o: In function `PlanetGL::getCords()':
PlanetGL.c++:(.text+0x1e2a): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0x1e3c): undefined reference to `PlanetGL::CirKordX'
PlanetGL.c++:(.text+0x1ed7): undefined reference to `PlanetGL::CirKordY'
PlanetGL.c++:(.text+0x1ee9): undefined reference to `PlanetGL::CirKordY'
/tmp/ccfqE9zq.o: In function `PlanetGL::main(int, char**)':
PlanetGL.c++:(.text+0x1fee): undefined reference to `glutInit'
PlanetGL.c++:(.text+0x1ffa): undefined reference to `glutInitDisplayMode'
PlanetGL.c++:(.text+0x200e): undefined reference to `glutInitWindowSize'
PlanetGL.c++:(.text+0x2022): undefined reference to `glutInitWindowPosition'
PlanetGL.c++:(.text+0x202e): undefined reference to `glutCreateWindow'
PlanetGL.c++:(.text+0x2033): undefined reference to `PlanetGL::window'
PlanetGL.c++:(.text+0x203f): undefined reference to `glutDisplayFunc'
PlanetGL.c++:(.text+0x2044): undefined reference to `glutFullScreen'
PlanetGL.c++:(.text+0x2050): undefined reference to `glutIdleFunc'
PlanetGL.c++:(.text+0x2057): undefined reference to `PlanetGL::ReSizeGLScene(int, int)'
PlanetGL.c++:(.text+0x205c): undefined reference to `glutReshapeFunc'
PlanetGL.c++:(.text+0x2068): undefined reference to `glutKeyboardFunc'
PlanetGL.c++:(.text+0x2074): undefined reference to `glutSpecialFunc'
PlanetGL.c++:(.text+0x208d): undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status

```


And with
```
glutDisplayFunc(&Obj, &PlanetGL::DrawGLScene);
```
I get this:
```
PlanetGL.c++:703: error: cannot convert &#8216;PlanetGL*&#8217; to &#8216;void (*)()&#8217; for argument &#8216;1&#8217; to &#8216;void glutDisplayFunc(void (*)())&#8217;

```
Well, it was expected. It wants only the adress of the function, not my object

It is obvious that I'm not good at all with programming. It even took me 2 days to realize that I was working with C instead of C++ :D (But everything worked)

---

### Post by dwhitney67 on 2009-03-01
Can you please post the API for glutDisplayFunc()?

I can create something similar to experiment on my system without having to install the OpenGL development library.

---

### Post by Gediminas2 on 2009-03-01
> **dwhitney67 said:**
> Can you please post the API for glutDisplayFunc()?

I can create something similar to experiment on my system without having to install the OpenGL development library.

[http://www-etud.iro.umontreal.ca/~clavetsi/api/glut/glutDisplayFunc.html](http://www-etud.iro.umontreal.ca/~clavetsi/api/glut/glutDisplayFunc.html)

Is this ok?

---

### Post by dwhitney67 on 2009-03-01
Yep, this works for me:
```

#include <iostream>

void glutDisplayFunc(void (*func)(void))
{
  func();
}

class Foo
{
  public:
    static void function(void) { std::cout << "Foo::function() called." << std::endl; }
};

int main()
{
  glutDisplayFunc(Foo::function);
}

```

It appears that you need to remove the '&' from the parameter that you are passing glutDisplayFunc() and other OpenGL functions.

---

### Post by Gediminas2 on 2009-03-01
So in the end it seems I have to make the functions static.

Any advise for using global variables in static functions?

making variables static will prevent changing their values, right?

And i cannot change the function arguments. I simply hit a roadblock.

I tried using a simple test with static for global variables (Used your code):
```
#include <iostream>

void glutDisplayFunc(void (*func)(void))
{
  func();
}

class Foo
{
  public:
    Foo();
    static char *a;
    static void function(void) { std::cout << "Foo::function() called." << Foo::a << std::endl; }
};

Foo::Foo(){a = "word";}

int main()
{
  glutDisplayFunc(&Foo::function);
}
```

And what the compiler says, I can't even understand
```
$ g++ test.c++ -o t
test.c++: In constructor &#8216;Foo::Foo()&#8217;:
test.c++:16: warning: deprecated conversion from string constant to &#8216;char*&#8217;
/tmp/ccG7WunV.o: In function `Foo::Foo()':
test.c++:(.text+0x17): undefined reference to `Foo::a'
/tmp/ccG7WunV.o: In function `Foo::Foo()':
test.c++:(.text+0x27): undefined reference to `Foo::a'
/tmp/ccG7WunV.o: In function `Foo::function()':
test.c++:(.text._ZN3Foo8functionEv[Foo::function()]+0x9): undefined reference to `Foo::a'
collect2: ld returned 1 exit status

```

Now if i figure this out, I might do my project in c++. And I will also have to make the same thing on java. :|

---

### Post by dwhitney67 on 2009-03-01
A variable that is declared 'static' can have its value changed; now if it is also declared 'const', then you are out of luck because it is read-only.  But with plain-ol' 'static', your variable is read-writable.

Now to your augmented example, and in the interest of brevity...  The class is fine, however you do not require a constructor because there is nothing to construct.  All of your function (err, methods) are static, as will be the data contain within the class.

So something like:
```

class Foo
{
  public:
    static void function() { ... }

  private:
    // declaration only
    static char* a;
};

// definition and initialization of static variable(s)
char* Foo::a = 0;

int main()
{
  glutDisplayFunc(Foo::function);   // Note, the '&' is NOT required.
}

```


P.S.  Earlier you asked about namespaces; here's an example:
```

namespace Foo
{
  char* a = 0;

  void function()
  {
    // If implementing function in namespace, declaration of 'a' must
    // precede this function if it is to be used.
    std::cout << "value of a is "
              << (a ? "non-zero" : "null")
              << std::endl;
  }
}

```
Here, the data must be declared before the function uses it.  There is no stead-fast rule that implies that one must implement their function within a class declaration or within a namespace.  You can implement the function pretty much anywhere as long as the declaration has been made available.

So,
```

namespace Foo
{
  void function();
  char* a;
}

void Foo::function()
{
  // access to 'a' is alright, even though it is declared after the
  // function in the namespace definition.
  ...
}

```

---

### Post by Gediminas2 on 2009-03-05
It took me quite long to figure out that after i make my functions static, the errors I get are not because of MY code, the references to OpenGL functions and variables are undefined within my static functions (But I included the OpenGL headers).

How do I fix it? (If it's even fixable)

Thanks in advance,
Gedas

---

### Post by dwhitney67 on 2009-03-05
> **Gediminas2 said:**
> It took me quite long to figure out that after i make my functions static, the errors I get are not because of MY code, the references to OpenGL functions and variables are undefined within my static functions (But I included the OpenGL headers).

How do I fix it? (If it's even fixable)

Thanks in advance,
Gedas
Are these runtime errors or compiler errors?  If the former, I have a hard time believing OpenGL would have a problem with static methods and/or variables.

Either way, I cannot comment too much because you have not been explicit in what errors you are getting, and furthermore you have not posted any code since your earlier postings.

---

### Post by Gediminas2 on 2009-03-05
> **dwhitney67 said:**
> Are these runtime errors or compiler errors?  If the former, I have a hard time believing OpenGL would have a problem with static methods and/or variables.

Either way, I cannot comment too much because you have not been explicit in what errors you are getting, and furthermore you have not posted any code since your earlier postings.

I can't really say what kind of error this is, but this is the g++ output
```
gedas@gedas-desktop:~/OGL/planetos$ g++ PlanetGL.c++
PlanetGL.c++: In function &#8216;void PlanetGL::DrawGLScene()&#8217;:
PlanetGL.c++:241: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:242: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:244: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:247: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:250: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:253: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:254: warning: deprecated conversion from string constant to &#8216;char*&#8217;
PlanetGL.c++:276: warning: deprecated conversion from string constant to &#8216;char*&#8217;
/usr/lib/gcc/i486-linux-gnu/4.3.2/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
/tmp/ccizofFG.o: In function `PlanetGL::keyPressed(unsigned char, int, int)':
PlanetGL.c++:(.text+0x18b): undefined reference to `glutDestroyWindow'
PlanetGL.c++:(.text+0x1e8): undefined reference to `glDisable'
PlanetGL.c++:(.text+0x1f9): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x29f): undefined reference to `glDisable'
PlanetGL.c++:(.text+0x2ab): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x2bc): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x2c8): undefined reference to `glDisable'
/tmp/ccizofFG.o: In function `ReSizeGLScene(int, int)':
PlanetGL.c++:(.text+0x687): undefined reference to `glViewport'
PlanetGL.c++:(.text+0x693): undefined reference to `glMatrixMode'
PlanetGL.c++:(.text+0x698): undefined reference to `glLoadIdentity'
PlanetGL.c++:(.text+0x6c6): undefined reference to `gluPerspective'
PlanetGL.c++:(.text+0x6d2): undefined reference to `glMatrixMode'
/tmp/ccizofFG.o: In function `PlanetGL::LoadGLTextures()':
PlanetGL.c++:(.text+0xb6d): undefined reference to `glGenTextures'
PlanetGL.c++:(.text+0xb99): undefined reference to `glBindTexture'
PlanetGL.c++:(.text+0xbb5): undefined reference to `glTexParameteri'
PlanetGL.c++:(.text+0xbd1): undefined reference to `glTexParameteri'
PlanetGL.c++:(.text+0xc42): undefined reference to `glTexImage2D'
/tmp/ccizofFG.o: In function `PlanetGL::glPrint(char*)':
PlanetGL.c++:(.text+0xccf): undefined reference to `glPushAttrib'
PlanetGL.c++:(.text+0xcdf): undefined reference to `glListBase'
PlanetGL.c++:(.text+0xd03): undefined reference to `glCallLists'
PlanetGL.c++:(.text+0xd08): undefined reference to `glPopAttrib'
/tmp/ccizofFG.o: In function `PlanetGL::DrawGLScene()':
PlanetGL.c++:(.text+0xd1c): undefined reference to `glClear'
PlanetGL.c++:(.text+0xd21): undefined reference to `glLoadIdentity'
PlanetGL.c++:(.text+0x1121): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x115e): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x11b3): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x11f0): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x122f): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x126f): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x12bd): undefined reference to `glRotatef'
PlanetGL.c++:(.text+0x12e6): undefined reference to `glRotatef'
PlanetGL.c++:(.text+0x12fb): undefined reference to `glBindTexture'
PlanetGL.c++:(.text+0x1322): undefined reference to `gluSphere'
PlanetGL.c++:(.text+0x1337): undefined reference to `glBindTexture'
PlanetGL.c++:(.text+0x13b3): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x13da): undefined reference to `gluSphere'
PlanetGL.c++:(.text+0x1456): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x14d6): undefined reference to `glRasterPos2f'
PlanetGL.c++:(.text+0x1545): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x157a): undefined reference to `gluDisk'
PlanetGL.c++:(.text+0x15c3): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x16dc): undefined reference to `glTranslatef'
PlanetGL.c++:(.text+0x16e1): undefined reference to `glutSwapBuffers'
/tmp/ccizofFG.o: In function `PlanetGL::KillFont()':
PlanetGL.c++:(.text+0x16fe): undefined reference to `glDeleteLists'
/tmp/ccizofFG.o: In function `PlanetGL::BuildFont()':
PlanetGL.c++:(.text+0x1712): undefined reference to `glGenLists'
PlanetGL.c++:(.text+0x1723): undefined reference to `XOpenDisplay'
PlanetGL.c++:(.text+0x1739): undefined reference to `XLoadQueryFont'
PlanetGL.c++:(.text+0x1755): undefined reference to `XLoadQueryFont'
PlanetGL.c++:(.text+0x1793): undefined reference to `glXUseXFont'
PlanetGL.c++:(.text+0x17a5): undefined reference to `XFreeFont'
PlanetGL.c++:(.text+0x17b0): undefined reference to `XCloseDisplay'
/tmp/ccizofFG.o: In function `PlanetGL::InitGL(int, int)':
PlanetGL.c++:(.text+0x17c9): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x17f1): undefined reference to `glClearColor'
PlanetGL.c++:(.text+0x17fb): undefined reference to `glClearDepth'
PlanetGL.c++:(.text+0x1807): undefined reference to `glDepthFunc'
PlanetGL.c++:(.text+0x1813): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x181f): undefined reference to `glShadeModel'
PlanetGL.c++:(.text+0x182b): undefined reference to `glMatrixMode'
PlanetGL.c++:(.text+0x1830): undefined reference to `glLoadIdentity'
PlanetGL.c++:(.text+0x185e): undefined reference to `gluPerspective'
PlanetGL.c++:(.text+0x186a): undefined reference to `glMatrixMode'
PlanetGL.c++:(.text+0x188c): undefined reference to `glLightfv'
PlanetGL.c++:(.text+0x18a9): undefined reference to `glLightfv'
PlanetGL.c++:(.text+0x18c6): undefined reference to `glLightfv'
PlanetGL.c++:(.text+0x18d2): undefined reference to `glEnable'
PlanetGL.c++:(.text+0x18e6): undefined reference to `glBlendFunc'
PlanetGL.c++:(.text+0x190e): undefined reference to `glColor4f'
PlanetGL.c++:(.text+0x1913): undefined reference to `gluNewQuadric'
PlanetGL.c++:(.text+0x192d): undefined reference to `gluQuadricNormals'
PlanetGL.c++:(.text+0x1942): undefined reference to `gluQuadricTexture'
/tmp/ccizofFG.o: In function `Main::main(int, char**)':
PlanetGL.c++:(.text+0x2007): undefined reference to `glutInit'
PlanetGL.c++:(.text+0x2013): undefined reference to `glutInitDisplayMode'
PlanetGL.c++:(.text+0x2027): undefined reference to `glutInitWindowSize'
PlanetGL.c++:(.text+0x203b): undefined reference to `glutInitWindowPosition'
PlanetGL.c++:(.text+0x2047): undefined reference to `glutCreateWindow'
PlanetGL.c++:(.text+0x2058): undefined reference to `glutDisplayFunc'
PlanetGL.c++:(.text+0x205d): undefined reference to `glutFullScreen'
PlanetGL.c++:(.text+0x2069): undefined reference to `glutIdleFunc'
PlanetGL.c++:(.text+0x2070): undefined reference to `PlanetGL::ReSizeGLScene(int, int)'
PlanetGL.c++:(.text+0x2075): undefined reference to `glutReshapeFunc'
PlanetGL.c++:(.text+0x2081): undefined reference to `glutKeyboardFunc'
PlanetGL.c++:(.text+0x208d): undefined reference to `glutSpecialFunc'
PlanetGL.c++:(.text+0x20a6): undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status

```

Don't mind the char vs strings warning.

EDIT: I forgot to mention: I put all the functions under a namespace, as just using a class with everything static was leading to nowhere.

```
namespace PlanetGL
{
  // public:
   //PlanetGL();
   void BuildFont();
   void KillFont();
   void glPrint(char *text);
   void DrawGLScene();
   int ImageLoad(char *filename, Image *image);
   void LoadGLTextures();
   void InitGL(GLsizei Width, GLsizei Height);
   void ReSizeGLScene(GLsizei Width, GLsizei Height);
   void keyPressed(unsigned char key, int x, int y);
   void specialKeyPressed(int key, int x, int y);
  // int main(int argc, char **argv);
   int getCords();
    int window,light,blend;
   //private:
  
   GLuint filter;		// Which Filter To Use (nearest/linear/mipmapped)
   GLuint texture[9];		// Storage for 9 textures.
   GLuint object;
   int objects;
   GLfloat xrot;		// X Rotation
   GLfloat yrot;		// Y Rotation
   GLfloat xspeed;		// x rotation speed
   GLfloat yspeed;		// y rotation speed
   cord cam;			// Camera position
   int orbita;
   float orsize;
   int PlanetName;
   float *CirKordX, *CirKordY, CirKordZ;
   float *k;
   float kf, kspeed;
   int ZoomSpeed;
   double *PlanetSpeed;
   GLuint base;        	 	// base display list for the font set.
   GLfloat cnt1;       	    	// 1st counter used to move text & for coloring.
   GLfloat cnt2;           	// 2nd counter used to move text & for coloring.
   GLUquadricObj *quadratic;	// Storage For Our Quadratic Objects
   GLfloat *LightAmbient;
   GLfloat *LightDiffuse;
   GLfloat *LightPosition;
   CO *Plan;
};
```

---

### Post by tneva82 on 2009-03-05
> **Gediminas2 said:**
> [code]gedas@gedas-desktop:~/OGL/planetos$ g++ PlanetGL.c++

no openGL/Glut library linked to project. Pretty sure that's the reason for this.

Try this:

g++ planetGL.c++ -o planetGL -lGL -lGLU

---

### Post by dwhitney67 on 2009-03-05
I will mind the string warnings... fix these by declaring your strings to be constant.  In lieu of:
```

char* someStr = "foo";

// use

const char* someStr = "foo";

```

The rest of the errors, and there is quite a few (so forgive me if I missed one), are due to link problems... not C syntax errors; hence it is not the compiler.  An "unresolved reference" is a link error.

If your application is defined in multiple modules, say Mod1.c, Mod2.c, and Mod3.c, then you need to build your application in one of two ways:

One way:
```

g++ Mod1.cpp Mod2.cpp Mod3.cpp -o myapp

```

Another way:
```

g++ -c Mod1.cpp
g++ -c Mod2.cpp
g++ -c Mod3.cpp
g++ Mod1.o Mod2.o Mod3.o -o myapp

```
In the examples above, I did not specify "CFLAGS" or "LDFLAGS".  Typically for CFLAGS, options are -Wall -ansi -pedantic.  So for compiling:
```

g++ -Wall -ansi -pedantic -c Mod1.cpp
...

```
For LDFLAGS, these are your -L and -l (lowercase ell) options.  For example:
```

g++ Mod1.o Mod2.o Mod3.o -L/path/to/library -lopenGL -o myapp

```

So essentially the format is:
```

g++ CFLAGS Mod1.cpp Mod2.cpp ... ModN.cpp LFLAGS -o myapp

```

------------

Edit... I forgot... use g++, not gcc.

---

### Post by Gediminas2 on 2009-03-05
> **tneva82 said:**
> no openGL/Glut library linked to project. Pretty sure that's the reason for this.

Try this:

g++ planetGL.c++ -o planetGL -lGL -lGLU

Thanks a million friend :D
It now compiles. I forgot about linking :)

---

