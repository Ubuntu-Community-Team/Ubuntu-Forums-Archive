---
title: "new to open GL"
date: 2009-02-21
forum: Programming Talk
---

### Post by Shady3D on 2009-02-21
```

#include <windows.h>
 
#include <gl/Glu.h>

#include <gl/glut.h>



void myInit(){

	glPointSize(4.0);  //a dot is 4*4 pixels
	glColor3f(0.0,0.0,0.0);  //set the drawing color
	glClearColor(1.0,1.0,1.0,0.0); //set white background

	glMatrixMode(GL_PROJECTION);
	glLoadIdentity();
	gluOrtho2D(0.0, 300.0, 0.0, 300.0);
}





void myDisplay(){

	glClear(GL_COLOR_BUFFER_BIT); //clear the screen
	glFlush();  //send all output to display
}

void myKeyboard(unsigned char theKey, int mouseX, int mouseY){

	if(theKey == 'd'){

		glBegin(GL_POINTS);
			glVertex2i(mouseX,300-mouseY);
		glEnd();
	}
	else if (theKey == 'r')
		glColor3f(1,0,0);

	else if (theKey == 'g')
		glColor3f(0,1,0);

	else if (theKey == 'b')
		glColor3f(0,0,1);

	else
		glClear(GL_COLOR_BUFFER_BIT);

	glFlush();	
}

void myMouse(int button, int state, int x, int y){

	if(button == GLUT_LEFT_BUTTON && state == GLUT_DOWN){

		glBegin(GL_POINTS);
			glVertex2i(x,300-y);
		glEnd();		
	}
	else if (button == GLUT_RIGHT_BUTTON && state == GLUT_DOWN)

		myDisplay();

	glFlush();	

}

void myMotion(int x, int y) { }


void myPassiveMotion(int x, int y) {

	glBegin(GL_POINTS);
		glVertex2i(x,300-y);
	glEnd();

	glFlush();
}

void main(int args, char** argv) {

	glutInit(&args, argv);

	glutInitDisplayMode(GLUT_SINGLE | GLUT_RGB); //set the display mode

	glutInitWindowSize(300,300);  //set the window size

	glutInitWindowPosition(100, 150);  //set the window position on screen

	glutCreateWindow("my first attempt");  //open the screen window

	// register the callback functions

	glutDisplayFunc(myDisplay);

	glutMouseFunc(myMouse);

	glutKeyboardFunc(myKeyboard);

	glutMotionFunc(myMotion);

    glutPassiveMotionFunc(myPassiveMotion);



	myInit();   //additional init

	glutMainLoop();  

}


```

ok so this is the code that they gave us in the section of openGL and i want to run it under Linux (it worked under windows), i searched about openGL and i downloaded some packages for openGL and also tried a code from the Internet that makes a 3d box a u can rotate using mouse and it worked smoothly, and BTW i am on ubuntu 64, so if any body can help me, and thx in advance
 
and here is the output from the compilation

```

$ g++ use_keyboard_v1.cpp -o out
use_keyboard_v1.cpp:1:21: error: windows.h: No such file or directory
use_keyboard_v1.cpp:2:20: error: gl/Glu.h: No such file or directory
use_keyboard_v1.cpp:3:21: error: gl/glut.h: No such file or directory
use_keyboard_v1.cpp: In function ‘void myInit()’:
use_keyboard_v1.cpp:7: error: ‘glPointSize’ was not declared in this scope
use_keyboard_v1.cpp:8: error: ‘glColor3f’ was not declared in this scope
use_keyboard_v1.cpp:9: error: ‘glClearColor’ was not declared in this scope
use_keyboard_v1.cpp:11: error: ‘GL_PROJECTION’ was not declared in this scope
use_keyboard_v1.cpp:11: error: ‘glMatrixMode’ was not declared in this scope
use_keyboard_v1.cpp:12: error: ‘glLoadIdentity’ was not declared in this scope
use_keyboard_v1.cpp:13: error: ‘gluOrtho2D’ was not declared in this scope
use_keyboard_v1.cpp: In function ‘void myDisplay()’:
use_keyboard_v1.cpp:19: error: ‘GL_COLOR_BUFFER_BIT’ was not declared in this scope
use_keyboard_v1.cpp:19: error: ‘glClear’ was not declared in this scope
use_keyboard_v1.cpp:21: error: ‘glFlush’ was not declared in this scope
use_keyboard_v1.cpp: In function ‘void myKeyboard(unsigned char, int, int)’:
use_keyboard_v1.cpp:29: error: ‘GL_POINTS’ was not declared in this scope
use_keyboard_v1.cpp:29: error: ‘glBegin’ was not declared in this scope
use_keyboard_v1.cpp:30: error: ‘glVertex2i’ was not declared in this scope
use_keyboard_v1.cpp:31: error: ‘glEnd’ was not declared in this scope
use_keyboard_v1.cpp:34: error: ‘glColor3f’ was not declared in this scope
use_keyboard_v1.cpp:36: error: ‘glColor3f’ was not declared in this scope
use_keyboard_v1.cpp:38: error: ‘glColor3f’ was not declared in this scope
use_keyboard_v1.cpp:41: error: ‘GL_COLOR_BUFFER_BIT’ was not declared in this scope
use_keyboard_v1.cpp:41: error: ‘glClear’ was not declared in this scope
use_keyboard_v1.cpp:42: error: ‘glFlush’ was not declared in this scope
use_keyboard_v1.cpp: In function ‘void myMouse(int, int, int, int)’:
use_keyboard_v1.cpp:47: error: ‘GLUT_LEFT_BUTTON’ was not declared in this scope
use_keyboard_v1.cpp:47: error: ‘GLUT_DOWN’ was not declared in this scope
use_keyboard_v1.cpp:49: error: ‘GL_POINTS’ was not declared in this scope
use_keyboard_v1.cpp:49: error: ‘glBegin’ was not declared in this scope
use_keyboard_v1.cpp:50: error: ‘glVertex2i’ was not declared in this scope
use_keyboard_v1.cpp:51: error: ‘glEnd’ was not declared in this scope
use_keyboard_v1.cpp:53: error: ‘GLUT_RIGHT_BUTTON’ was not declared in this scope
use_keyboard_v1.cpp:55: error: ‘glFlush’ was not declared in this scope
use_keyboard_v1.cpp: In function ‘void myPassiveMotion(int, int)’:
use_keyboard_v1.cpp:64: error: ‘GL_POINTS’ was not declared in this scope
use_keyboard_v1.cpp:64: error: ‘glBegin’ was not declared in this scope
use_keyboard_v1.cpp:65: error: ‘glVertex2i’ was not declared in this scope
use_keyboard_v1.cpp:66: error: ‘glEnd’ was not declared in this scope
use_keyboard_v1.cpp:67: error: ‘glFlush’ was not declared in this scope
use_keyboard_v1.cpp: At global scope:
use_keyboard_v1.cpp:71: error: ‘::main’ must return ‘int’
use_keyboard_v1.cpp: In function ‘int main(int, char**)’:
use_keyboard_v1.cpp:73: error: ‘glutInit’ was not declared in this scope
use_keyboard_v1.cpp:74: error: ‘GLUT_SINGLE’ was not declared in this scope
use_keyboard_v1.cpp:74: error: ‘GLUT_RGB’ was not declared in this scope
use_keyboard_v1.cpp:74: error: ‘glutInitDisplayMode’ was not declared in this scope
use_keyboard_v1.cpp:75: error: ‘glutInitWindowSize’ was not declared in this scope
use_keyboard_v1.cpp:76: error: ‘glutInitWindowPosition’ was not declared in this scope
use_keyboard_v1.cpp:77: error: ‘glutCreateWindow’ was not declared in this scope
use_keyboard_v1.cpp:80: error: ‘glutDisplayFunc’ was not declared in this scope
use_keyboard_v1.cpp:81: error: ‘glutMouseFunc’ was not declared in this scope
use_keyboard_v1.cpp:82: error: ‘glutKeyboardFunc’ was not declared in this scope
use_keyboard_v1.cpp:83: error: ‘glutMotionFunc’ was not declared in this scope
use_keyboard_v1.cpp:84: error: ‘glutPassiveMotionFunc’ was not declared in this scope
use_keyboard_v1.cpp:87: error: ‘glutMainLoop’ was not declared in this scope

```

---

### Post by Simian Man on 2009-02-21
Your includes are wrong because this code was meant for Windows.  First of all, you should not be including windows.h because Linux obviously doesn't have it.  Not to worry though, you aren't using any features there.

Secondly it should be:
```

#inlcude <GL/glu.h>
#include <GL/glut.h>

```

Windows is case-insensitive, so programmers there don't bother getting the case right on their header files.  On unix, of course, case matters so only the above includes will be found.

Any other troubles, let us know.

---

### Post by Shady3D on 2009-02-21
i made those modifications and thats the output

```

$ g++ use_keyboard_v1.cpp -o out
/tmp/ccgNemR2.o: In function `myPassiveMotion(int, int)':
use_keyboard_v1.cpp:(.text+0x20): undefined reference to `glBegin'
use_keyboard_v1.cpp:(.text+0x32): undefined reference to `glVertex2i'
use_keyboard_v1.cpp:(.text+0x37): undefined reference to `glEnd'
use_keyboard_v1.cpp:(.text+0x3c): undefined reference to `glFlush'
/tmp/ccgNemR2.o: In function `myKeyboard(unsigned char, int, int)':
use_keyboard_v1.cpp:(.text+0x60): undefined reference to `glBegin'
use_keyboard_v1.cpp:(.text+0x72): undefined reference to `glVertex2i'
use_keyboard_v1.cpp:(.text+0x77): undefined reference to `glEnd'
use_keyboard_v1.cpp:(.text+0x92): undefined reference to `glColor3f'
use_keyboard_v1.cpp:(.text+0xad): undefined reference to `glColor3f'
use_keyboard_v1.cpp:(.text+0xc8): undefined reference to `glColor3f'
use_keyboard_v1.cpp:(.text+0xd4): undefined reference to `glClear'
use_keyboard_v1.cpp:(.text+0xd9): undefined reference to `glFlush'
/tmp/ccgNemR2.o: In function `myDisplay()':
use_keyboard_v1.cpp:(.text+0xe9): undefined reference to `glClear'
use_keyboard_v1.cpp:(.text+0xee): undefined reference to `glFlush'
/tmp/ccgNemR2.o: In function `myMouse(int, int, int, int)':
use_keyboard_v1.cpp:(.text+0x11a): undefined reference to `glBegin'
use_keyboard_v1.cpp:(.text+0x12c): undefined reference to `glVertex2i'
use_keyboard_v1.cpp:(.text+0x131): undefined reference to `glEnd'
use_keyboard_v1.cpp:(.text+0x149): undefined reference to `glFlush'
/tmp/ccgNemR2.o: In function `myInit()':
use_keyboard_v1.cpp:(.text+0x15c): undefined reference to `glPointSize'
use_keyboard_v1.cpp:(.text+0x16a): undefined reference to `glColor3f'
use_keyboard_v1.cpp:(.text+0x18a): undefined reference to `glClearColor'
use_keyboard_v1.cpp:(.text+0x194): undefined reference to `glMatrixMode'
use_keyboard_v1.cpp:(.text+0x199): undefined reference to `glLoadIdentity'
use_keyboard_v1.cpp:(.text+0x1ba): undefined reference to `gluOrtho2D'
/tmp/ccgNemR2.o: In function `main':
use_keyboard_v1.cpp:(.text+0x1d8): undefined reference to `glutInit'
use_keyboard_v1.cpp:(.text+0x1e2): undefined reference to `glutInitDisplayMode'
use_keyboard_v1.cpp:(.text+0x1f1): undefined reference to `glutInitWindowSize'
use_keyboard_v1.cpp:(.text+0x200): undefined reference to `glutInitWindowPosition'
use_keyboard_v1.cpp:(.text+0x20a): undefined reference to `glutCreateWindow'
use_keyboard_v1.cpp:(.text+0x214): undefined reference to `glutDisplayFunc'
use_keyboard_v1.cpp:(.text+0x21e): undefined reference to `glutMouseFunc'
use_keyboard_v1.cpp:(.text+0x228): undefined reference to `glutKeyboardFunc'
use_keyboard_v1.cpp:(.text+0x232): undefined reference to `glutMotionFunc'
use_keyboard_v1.cpp:(.text+0x23c): undefined reference to `glutPassiveMotionFunc'
use_keyboard_v1.cpp:(.text+0x246): undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status


```

---

### Post by snova on 2009-02-21
Link with the GL and GLUT libraries.

```
g++ use_keyboard_v1.cpp -o out -lGL -lglut
```

---

### Post by Simian Man on 2009-02-21
OK now you got past the compiler errors!  The errors you have now are from our friend the linker.  Basically it can't find any of the OpenGL functions because you haven't told it to look for them.  To tell gcc to link to OpenGL, the utility library, and Glut, you'd compile with the following command:

```

g++ use_keyboard_v1.cpp -lGL -lGLU -lglut -o out

```

Then GCC will be able to find the definitions and link your program.

---

### Post by Shady3D on 2009-02-21
so every time when i use openGL i should put those flags

---

### Post by snova on 2009-02-21
> **Shady3D said:**
> so every time when i use openGL i should put those flags

Yes. If you aren't using GLUT, however, you can leave off **-lglut**.

This isn't specific to OpenGL, linking is necessary for pretty much every library you'll ever use. Otherwise, the functions you use simply aren't present- the compiler sees that they are used, and knows their signature, but until you link in the library they aren't part of the program.

---

### Post by Shady3D on 2009-02-21
its very annoing to have errors, but it's very good to have people answer, thx alot

---

