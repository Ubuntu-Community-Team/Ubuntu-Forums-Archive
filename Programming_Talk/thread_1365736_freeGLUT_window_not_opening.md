---
title: "freeGLUT window not opening"
date: 2009-12-27
forum: Programming Talk
---

### Post by flummoxed on 2009-12-27
Hey,

I'm trying to get a freeGLUT window to open... and no dice. I'm using the freeGLUT package from the ubuntu repos, (version 2.40). The following C++ code compiles, but when it runs no window actually appears. Something comes up on the taskbar saying there's a window, I don't actually get anything. Any ideas? My graphics card is an nvidia, using the proprietary drivers, and works doing 3D etc, for everything else.

```

#include <iostream>
#include <cstdlib>
#include <GL/freeglut.h>
using namespace std;

// function prototypes
void disp(void);
void keyb(unsigned char key, int x, int y);


// window identifier
static int win;

int main(int argc, char **argv){
  glutInit(&argc, argv);
  glutInitDisplayMode(GLUT_RGBA | GLUT_SINGLE);
  glutInitWindowSize(500,500);
  glutInitWindowPosition(200,100);
  win = glutCreateWindow("glut");
  //glutFullScreen();
  glutDisplayFunc(disp);
  glutKeyboardFunc(keyb);
  glClearColor(0.0,0.0,0.0,0.0);
  glutMainLoop();

  return 0;
}


void disp(void){
  glClear(GL_COLOR_BUFFER_BIT);

  //glutWireTeapot(0.5);
  // glutSolidTeapot(0.5);
  // glutWireSphere(0.5,100,100);
  // glutSolidSphere(0.5,100,100);
  // glutWireTorus(0.3,0.5,100,100);
  // glutSolidTorus(0.3,0.5,100,100);
  // glutWireIcosahedron();
  // glutSolidIcosahedron();
  // glutWireDodecahedron();
  // glutSolidDodecahedron();
  // glutWireCone(0.5,0.5,100,100);
  // glutSolidCone(0.5,0.5,100,100);
  // glutWireCube(0.5);
  // glutSolidCube(0.5);
}

void keyb(unsigned char key, int x, int y){
  cout << "Pressed key " << key << " on coordinates (" << x << "," << y << ")";
  cout << endl;
  if(key == 'q'){
    cout << "Got q,so quitting " << endl;
    glutDestroyWindow(win);
    exit(0);
  }
}

```

---

### Post by Can+~ on 2009-12-27
It does create a window, but since nothing happens in the display function, compiz refrehses after the window executes, and makes it look that there's no window.

1. Disable compiz for a while (off: metacity --replace) (on: compiz --replace)
2. Copy some example into the display function, like a cube or something, so it keeps refreshing.

---

### Post by flummoxed on 2009-12-28
Thanks! Compiz was messing things up.

---

