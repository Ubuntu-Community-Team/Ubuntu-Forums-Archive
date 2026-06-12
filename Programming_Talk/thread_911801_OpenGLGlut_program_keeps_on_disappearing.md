---
title: "OpenGL/Glut program keeps on disappearing"
date: 2008-09-06
forum: Programming Talk
---

### Post by inktri on 2008-09-06
Whenever I try to compile and run any openGL/glut programs under Ubuntu, the animation generated displays for a fraction of a second and then disappears. The tab of the window of the animation remains in the taskbar and reclicking the tab reshows the animation for a fraction of a second again. 

A temporarily solution I'm using is glutIdleFunc() in conjunction with glutPostRedisplay(). However this merely redraws the animation constantly. 

Under my Windows systems, the animation from the code below doesn't disappear without the idle function. What's going on with Ubuntu?

Thanks for the help



```
#include <stdlib.h>
#include <GL/glut.h>

//------------------------------------------------------------	Reshape()
void OnReshape(int w, int h)
{
	// prevent a division by zero when minimising the window
	if (h==0)
		h=1;

	// set the drawable region of the window
	glViewport(0,0,w,h);

	// set up the projection matrix 
	glMatrixMode(GL_PROJECTION);
	glLoadIdentity();

	// just use a perspective projection
	gluPerspective(45,(float)w/h,0.1,100);

	// go back to modelview matrix so we can move the objects about
	glMatrixMode(GL_MODELVIEW);
}

//------------------------------------------------------------	Draw()
//
void OnDraw() {

	// clear the screen & depth buffer
	glClear(GL_DEPTH_BUFFER_BIT|GL_COLOR_BUFFER_BIT);

	// clear the previous transform
	glLoadIdentity();

	// set the camera position
	gluLookAt(	1,1,10,	//	eye pos
				0,0,0,	//	aim point
				0,1,0);	//	up direction

	// draw a simple teapot
	glutWireTeapot(1);

	// currently we've been drawing to the back buffer, we need
	// to swap the back buffer with the front one to make the image visible
	glutSwapBuffers();
}

//------------------------------------------------------------	OnInit()
//
void OnInit() {
	// enable depth testing
	glEnable(GL_DEPTH_TEST);
}

//------------------------------------------------------------	OnExit()
//
void OnExit() {
}

//------------------------------------------------------------	main()
//
int main(int argc,char** argv) {

	// initialise glut
	glutInit(&argc,argv);

	// request a depth buffer, RGBA display mode, and we want double buffering
	glutInitDisplayMode(GLUT_DEPTH|GLUT_RGBA|GLUT_DOUBLE);

	// set the initial window size
	glutInitWindowSize(640,480);

	// create the window
	glutCreateWindow("A basic glut example");

	// set the function to use to draw our scene
	glutDisplayFunc(OnDraw);

	// set the function to handle changes in screen size
	glutReshapeFunc(OnReshape);
	
	// run our custom initialisation
	OnInit();

	// set the function to be called when we exit
	atexit(OnExit);

	// this function runs a while loop to keep the program running.
	glutMainLoop();
	return 0;
}
```

---

### Post by bigb_thedestroyer on 2008-09-08
I too am having that problem.  I am trying to run off my own ubuntu drive at home.  I have a ATI Radeon x1050 and I know the GL_Gears demo works.  

The same application works on Fedora 9; unfortunatly, I don't know what video card that computer has.

---

### Post by bigb_thedestroyer on 2008-09-08
Ok, so I tried at home on my laptop.  My video card is an Intel 945.  I installed the following packages from a fresh Ubuntu 8.04 install.
[LIST]
[*]build_essential
[*]manpages-dev
[*]libgl1-mesa-dev
[*]libglu1-mesa-dev
[*]libxi-dev
[*]libxmu-dev
[*]libglut3-dev
[/LIST]

My application compiles clean, however when I start the application (which is nothing more the a set of white lines), all I see is the drawing.  I dont see the title bar and the app doesn't refresh properly when I click on it in the task bar.  

Am I missing anything?

B_D

P.S: I need to use glut for my school assignments so please dont suggest I code in sdl.

---

### Post by bigb_thedestroyer on 2008-09-09
I was able to fix my problem by disabling the default desktop effects.
To do this go to

System > Preferences > Appearance

Select Visual Effects, select the None radio button.

Your OpenGL app should work now.

---

### Post by hectorg87 on 2009-10-02
Disabling the desktop effects worked for me too on ubuntu 9.04! Thanks!

---

### Post by mathiasbc on 2010-03-26
I was having the same problem too, I disabled Desktop effects, but that only made the border or frame of the application to appear and the content only showed once and then dissapeared.  Well I was able to fix the problem thanks to this Thread, I had to disabled Desktop effects + use this function:

```

void show_window()
{
    glutPostRedisplay();   //  marks the current window as needing to be redisplayed
}

```which was called this way, in the main.

```

glutIdleFunc(show_window);

```Hope that helps some else with this problem.

edit:
By the way, worked for me under 9.10 and Mint Gloria 8

---

### Post by tyrell_turing on 2011-03-17
I was having this exact same problem (simple OpenGL program on Maverick Meerkat, 10.10 where the window disappeared), and turning off the effects also gave me a window frame but without the image. The inclusion of the glutIdle function did not work for me, though.

But, I noticed that it did work when I used GLUT_SINGLE rather than GLUT_DOUBLE in the glutInitDisplayMode. That's when I realized that the problem was that the buffers weren't swapping for me. So, rather than including a glutIdle function like this, all I had to do was include the glutSwapBuffers() function in my Display function, and this allowed the image to be displayed in the double buffer mode.

---

