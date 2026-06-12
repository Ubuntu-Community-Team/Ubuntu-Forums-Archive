---
title: "Newbie needs help compiling QT - on Ubuntu 11.10 - weird error"
date: 2011-10-15
forum: Programming Talk
---

### Post by newsboost on 2011-10-15
Hi,

I want to plot 2D (maybe later 3D) graphs. I'm trying to use the mathgl-library and successfully compiled using a FLTK-window (method 1) below. Now, I have problems getting GLUT and QT-variants to work (methods 2 and 3 below). Code:

------------------------------------------------------------
#include <mgl/mgl_zb.h>

//#define method 1 // fltk
//#define method 2 // glut
#define method 3 // qt

#if method==1
#include <mgl/mgl_fltk.h> // method 1
#elif method==2
#include <mgl/mgl_glut.h> // method 2
#elif method==3
#include <mgl/mgl_qt.h> // method 3
#endif

int sample(mglGraph *gr, void *)
{
  gr->Rotate(60,40);
  gr->Box();
  return 0;
}
//-----------------------------------------------------
int main(int argc,char **argv)
{

#if method==1
  mglGraphFLTK gr; // method 1
#elif method==2
  mglGraphGLUT gr; // method 2
#elif method==3
  mglGraphQT gr; // method 3
#endif

  gr.Window(argc,argv,sample,"MathGL examples");

  return mglFlRun();
}
------------------------------------------------------------

If you want to compile using method 1, you can type (remember to change preprocessor directive by uncommenting method 2 + commenting out method 1):
g++ mathgl_test_FLTK.cpp -lmgl -lmgl-fltk  && ./a.out 

If cannot get method 2 or method 3 to work (although you should be able to make method 1 work too!)... For method 2 (GLUT) I tried:
g++ mathgl_test_FLTK.cpp -lmgl -lmgl-glut && ./a.out

Gives:
mathgl_test_FLTK.cpp: In function ‘int main(int, char**)’:
mathgl_test_FLTK.cpp:50:19: error: ‘mglFlRun’ was not declared in this scope

Hmmm.... DAMN IT! So I try method=3 (QT)

g++ mathgl_test_FLTK.cpp -lmgl -lmgl-qt -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 && ./a.out

Gives:
In file included from /usr/include/qt4/QtGui/qwindowdefs.h:45:0,
                 from /usr/include/qt4/QtGui/qwidget.h:45,
                 from /usr/include/qt4/QtGui/QWidget:1,
                 from /usr/include/mgl/mgl_qt.h:27,
                 from mathgl_test_FLTK.cpp:26:
/usr/include/qt4/QtCore/qobjectdefs.h:214:53: error: expected ‘,’ or ‘...’ before numeric constant
/usr/include/qt4/QtCore/qobjectdefs.h:324:35: error: expected ‘,’ or ‘...’ before numeric constant
/usr/include/qt4/QtCore/qobjectdefs.h:332:17: error: expected unqualified-id before numeric constant
/usr/include/qt4/QtCore/qobjectdefs.h:338:66: error: expected ‘,’ or ‘...’ before numeric constant
/usr/include/qt4/QtCore/qobjectdefs.h:339:55: error: expected ‘,’ or ‘...’ before numeric constant
mathgl_test_FLTK.cpp: In function ‘int main(int, char**)’:
mathgl_test_FLTK.cpp:50:19: error: ‘mglFlRun’ was not declared in this scope

------------------------------------------------------------


 Hmmm.... DAMN IT! I've struggled with it for too long now... I hope somebody can help me get methods 2 and 3 to work... Please try it and tell me if it works for you (it is relatively simple code)!

Thanks...

---

