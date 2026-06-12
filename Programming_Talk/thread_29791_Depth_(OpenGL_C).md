---
title: "Depth (OpenGL C)"
date: 2005-04-25
forum: Programming Talk
---

### Post by aratar on 2005-04-25
i'm trying to get some gl stuff to work, but i'm not able to work with the depth.
basically if i draw something far away after drawing something close, the further away object is still allways in front of the closer one.

i'm not sure if i can fix this with proper initialisation, or if i have to write a depth sort algorithm.

heres the code:

```
#include <stdio.h>
#include <GL/glut.h>
#include <GL/glu.h>
#include <GL/gl.h>

int g_mainWindow;		/* global identifier for the main window */

void initGL(int, int, int*, char**);
int createMainWindow(int, int, char*);
void RenderScene();

int main(int argc, char **argv)
{
	initGL(800, 600, &argc, argv);
	
	g_mainWindow = createMainWindow(800, 600, "Final Doom: The Connect4 Saga...");
	printf("Window created, g_mainWindow = %d\n", g_mainWindow);

	glutShowWindow();
	
	while(1)
		RenderScene();

	printf("Render scene called\n");
	
	getchar();

	glutDestroyWindow(g_mainWindow);
	return 0;
}

void initGL(int width, int height, int *argc, char **argv)
{
	glutInitWindowSize(width, height);
	glutInitWindowPosition(0, 0);

	glutInit(argc, argv);
	glutInitDisplayMode(GLUT_RGBA | GLUT_DOUBLE | GLUT_DEPTH);
	glEnable(GL_DEPTH_TEST);
	glDepthMask(GL_TRUE);
	/* init with double buffer and rgba flags for animation */

	return;
}

int createMainWindow(int width, int height, char *windowName)
{
	int win;

	win = glutCreateWindow(windowName);
	glutSetWindow(win);

	glViewport(0, 0, width, height);
	glMatrixMode(GL_PROJECTION);
	glLoadIdentity();

	gluPerspective(45.0f,(GLfloat)width/(GLfloat)height, 1 ,150.0f);

	glMatrixMode(GL_MODELVIEW);
	glLoadIdentity();

	return win;
}


void drawToken(GLUquadricObj *pToken)
{

	glPushMatrix();
		glTranslatef(0,0,0.1f);
		glColor3ub(0, 255, 0);
		gluDisk(pToken, 0, 1, 40, 4);
		glPopMatrix();

	glColor3ub(255, 255, 0);
	gluDisk(pToken, 0, 1, 40, 4);
	
	gluCylinder(pToken, 1, 1, 0.1f, 40, 2);

	return;
}


void RenderScene()
{
	static float theta = 0.0f;

	glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

	glLoadIdentity();

	gluLookAt(	0,0,6,		/* position */
			0,0,0,		/* view */
			0,1,0);		/* up vector */

	
	GLUquadricObj *pToken = gluNewQuadric();
	gluQuadricTexture(pToken, GL_FALSE);

	gluQuadricDrawStyle(pToken, GLU_FILL);


	glPushMatrix();
		glTranslatef(-1.5f, 0, 0);
		glRotatef(theta, 0.0f, 1.0f, 0.0f);
		drawToken(pToken);
		glPopMatrix();

	glPushMatrix();
		glTranslatef(1.5f, 0, 0);
		glRotatef(theta, 0.0f, 1.0f, 0.0f);
		drawToken(pToken);
		glPopMatrix();

	glutSwapBuffers();

	gluDeleteQuadric(pToken);

	theta += 1.0f;
	return;
}

```

basically it draws two spinning tokens, which should have a yellow side and a green side.
but, because the yellow disc is drawn last, it is allways in front of the green one, even though it should be behind.

any help would be greatly appreciated

-------------------------------------------------------------
Cheers,

Aratar

---

### Post by james waples on 2009-10-17
Instead of using 

```
while(1)
RenderScene();
```

try using 

```
glutDisplayFunc(openglRenderFunc);

glutIdleFunc(openglIdleFunc);
```

instead.

Let me know how you get on. I'd be more than happy to offer what I know :)

---

