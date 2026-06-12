---
title: "OpenGL issue"
date: 2011-06-14
forum: Programming Talk
---

### Post by mickeoliver on 2011-06-14
Hi,

I've been trying to use [this tutorial]("http://openglbook.com/the-book/chapter-1-getting-started/") to learn some opengl.

I got it to compile without much problem, but when I try to run it this error is displayed:

```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  34 ()
  Serial number of failed request:  38
  Current serial number in output stream:  39
```

I've spent a couple of hours googling this but I couldn't find a solution.

Does anyone know how to fix this? Thank you.

---

### Post by Petrolea on 2011-06-14
> **mickeoliver said:**
> Hi,

I've been trying to use [this tutorial]("http://openglbook.com/the-book/chapter-1-getting-started/") to learn some opengl.

I got it to compile without much problem, but when I try to run it this error is displayed:

```
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  136 (GLX)
  Minor opcode of failed request:  34 ()
  Serial number of failed request:  38
  Current serial number in output stream:  39
```

I've spent a couple of hours googling this but I couldn't find a solution.

Does anyone know how to fix this? Thank you.

Maybe you're using malloc/calloc/realloc in a way that it grows very fast and takes all the memory up? It is a common error while doing this and it can cause a program to crash. But since it's OpenGL, the error might be something else (I'm not really familiar with it). But you can post the code and we'll see.

---

### Post by mickeoliver on 2011-06-14
Here's the code:

```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <GL/glew.h>
#include <GL/freeglut.h>
#define WINDOW_TITLE_PREFIX "Chapter 1"

int CurrentWidth = 800,
	CurrentHeight = 600,
	WindowHandle = 0;

void Initialize(int, char*[]);
void InitWindow(int, char*[]);
void ResizeFunction(int, int);
void RenderFunction(void);

int main(int argc, char* argv[])
{
	Initialize(argc, argv);

	glutMainLoop();

	exit(EXIT_SUCCESS);
}

void Initialize(int argc, char* argv[])
{
	InitWindow(argc, argv);

	fprintf(
		stdout,
		"INFO: OpenGL Version: %s\n",
		glGetString(GL_VERSION)
	);

	glClearColor(0.0f, 0.0f, 0.0f, 0.0f);
}

void InitWindow(int argc, char* argv[])
{
	glutInit(&argc, argv);

	glutInitContextVersion(4, 0);
	glutInitContextFlags(GLUT_FORWARD_COMPATIBLE);
	glutInitContextProfile(GLUT_CORE_PROFILE);

	glutSetOption(
		GLUT_ACTION_ON_WINDOW_CLOSE,
		GLUT_ACTION_GLUTMAINLOOP_RETURNS
	);

	glutInitWindowSize(CurrentWidth, CurrentHeight);

	glutInitDisplayMode(GLUT_DEPTH | GLUT_DOUBLE | GLUT_RGBA);

	WindowHandle = glutCreateWindow(WINDOW_TITLE_PREFIX);

	if(WindowHandle < 1) {
		fprintf(
			stderr,
			"ERROR: Could not create a new rendering window.\n"
		);
		exit(EXIT_FAILURE);
	}

	glutReshapeFunc(ResizeFunction);
	glutDisplayFunc(RenderFunction);
}

void ResizeFunction(int Width, int Height)
{
	CurrentWidth = Width;
	CurrentHeight = Height;
	glViewport(0, 0, CurrentWidth, CurrentHeight);
}

void RenderFunction(void)
{
	glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

	glutSwapBuffers();
	glutPostRedisplay();
}

```

I've only really programmed in c++ before, but I did this in C because the tutorial was in C too. I might have forgotten something because of that ;)

---

### Post by Petrolea on 2011-06-14
> **mickeoliver said:**
> Here's the code:

```
#include <stdlib.h>
#include <stdio.h>
#include <string.h>
#include <GL/glew.h>
#include <GL/freeglut.h>
#define WINDOW_TITLE_PREFIX "Chapter 1"

int CurrentWidth = 800,
	CurrentHeight = 600,
	WindowHandle = 0;

void Initialize(int, char*[]);
void InitWindow(int, char*[]);
void ResizeFunction(int, int);
void RenderFunction(void);

int main(int argc, char* argv[])
{
	Initialize(argc, argv);

	glutMainLoop();

	exit(EXIT_SUCCESS);
}

void Initialize(int argc, char* argv[])
{
	InitWindow(argc, argv);

	fprintf(
		stdout,
		"INFO: OpenGL Version: %s\n",
		glGetString(GL_VERSION)
	);

	glClearColor(0.0f, 0.0f, 0.0f, 0.0f);
}

void InitWindow(int argc, char* argv[])
{
	glutInit(&argc, argv);

	glutInitContextVersion(4, 0);
	glutInitContextFlags(GLUT_FORWARD_COMPATIBLE);
	glutInitContextProfile(GLUT_CORE_PROFILE);

	glutSetOption(
		GLUT_ACTION_ON_WINDOW_CLOSE,
		GLUT_ACTION_GLUTMAINLOOP_RETURNS
	);

	glutInitWindowSize(CurrentWidth, CurrentHeight);

	glutInitDisplayMode(GLUT_DEPTH | GLUT_DOUBLE | GLUT_RGBA);

	WindowHandle = glutCreateWindow(WINDOW_TITLE_PREFIX);

	if(WindowHandle < 1) {
		fprintf(
			stderr,
			"ERROR: Could not create a new rendering window.\n"
		);
		exit(EXIT_FAILURE);
	}

	glutReshapeFunc(ResizeFunction);
	glutDisplayFunc(RenderFunction);
}

void ResizeFunction(int Width, int Height)
{
	CurrentWidth = Width;
	CurrentHeight = Height;
	glViewport(0, 0, CurrentWidth, CurrentHeight);
}

void RenderFunction(void)
{
	glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT);

	glutSwapBuffers();
	glutPostRedisplay();
}

```

I've only really programmed in c++ before, but I did this in C because the tutorial was in C too. I might have forgotten something because of that ;)

I don't think you googled enough. 

[http://ubuntuforums.org/showthread.php?t=1762103](http://ubuntuforums.org/showthread.php?t=1762103)

This is the exact same problem, same tutorial, same example, same error, (hopefully the same fix).

Took me 2 minutes.

---

### Post by mickeoliver on 2011-06-14
Thanks, but if you actually read the post I think that he makes it pretty clear that those fixes did not help. And it seems like there is still no fix.

---

### Post by Petrolea on 2011-06-15
> **mickeoliver said:**
> Thanks, but if you actually read the post I think that he makes it pretty clear that those fixes did not help. And it seems like there is still no fix.

I'm pretty sure that's the fix. I don't think there are any others.

---

### Post by mickeoliver on 2011-06-15
Well then that's a bummer because it didn't work for me either.

---

### Post by mickeoliver on 2011-06-15
I found the solution, I'll post it here for anyone who might have the same problem: my NVIDIA driver seemed to have some issues with opengl 4.0, so I just changed the version in the code to 3.3. Worked perfectly.

---

### Post by t1497f35 on 2011-06-15
Nvidia released recently the 275 driver series, which [fixes important OpenGL 4.x issues]("http://g-truc.net/post-0402.html#menu") which might also solve your issue if you wanna use GL 4.x.

---

### Post by mickeoliver on 2011-06-16
Thanks,  I'll give that a try!

---

### Post by wezside on 2012-01-03
Thanks I had the same issue and changing to 3.3 worked. [http://developer.nvidia.com/opengl-driver](http://developer.nvidia.com/opengl-driver) indicates my card doesn't support OpenGL 4.

---

