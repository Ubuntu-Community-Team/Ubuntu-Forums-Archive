---
title: "Glut"
date: 2008-12-11
forum: Programming Talk
---

### Post by supernova1 on 2008-12-11
I am trying to start doing some OpenGL programming with glut.  I have tried to compile many examples that I have found online, but get errors when compiling.  I found an example at [http://www.lighthouse3d.com/opengl/glut/index.php?2](http://www.lighthouse3d.com/opengl/glut/index.php?2).

```

#include <GL/glut.h>


void renderScene(void) {
	glClear(GL_COLOR_BUFFER_BIT);
	glBegin(GL_TRIANGLES);
		glVertex3f(-0.5,-0.5,0.0);
		glVertex3f(0.5,0.0,0.0);
		glVertex3f(0.0,0.5,0.0);
	glEnd();
	glFlush();
}

void main(int argc, char **argv) {
	glutInit(&argc, argv);
	glutInitDisplayMode(GLUT_DEPTH | GLUT_SINGLE | GLUT_RGBA);
	glutInitWindowPosition(100,100);
	glutInitWindowSize(320,320);
	glutCreateWindow("3D Tech- GLUT Tutorial");
	glutDisplayFunc(renderScene);
	glutMainLoop();
}

```

When compiling this program, I get the following error:

```

david@david-desktop:~/programs/opengl/glut$ make main main.c
cc     main.c   -o main
main.c: In function ‘main’:
main.c:14: warning: return type of ‘main’ is not ‘int’
/tmp/ccUqtDiX.o: In function `renderScene':
main.c:(.text+0xa): undefined reference to `glClear'
main.c:(.text+0x14): undefined reference to `glBegin'
main.c:(.text+0x2c): undefined reference to `glVertex3f'
main.c:(.text+0x3f): undefined reference to `glVertex3f'
main.c:(.text+0x52): undefined reference to `glVertex3f'
main.c:(.text+0x57): undefined reference to `glEnd'
main.c:(.text+0x5c): undefined reference to `glFlush'
/tmp/ccUqtDiX.o: In function `main':
main.c:(.text+0x7a): undefined reference to `glutInit'
main.c:(.text+0x84): undefined reference to `glutInitDisplayMode'
main.c:(.text+0x93): undefined reference to `glutInitWindowPosition'
main.c:(.text+0xa2): undefined reference to `glutInitWindowSize'
main.c:(.text+0xac): undefined reference to `glutCreateWindow'
main.c:(.text+0xb6): undefined reference to `glutDisplayFunc'
main.c:(.text+0xbb): undefined reference to `glutMainLoop'
collect2: ld returned 1 exit status
make: *** [main] Error 1

```

I get similar errors when trying to compile other examples I find online.  It appears that none of the glut functions are working.  Does anyone have any suggestions?

Thanks,

Supernova

---

### Post by pp. on 2008-12-11
The compiler or interpreter doesn't seem to find the libraries which contain the functions mentioned in the error log.

Have you installed the development packages? Does the language need some library declarations or imports at the beginning of the source?

---

### Post by bobrocks on 2008-12-11
You need to have the glut library installed and link to it at compile time, for example -

[PHP]gcc -lglut main.c -o main [/PHP]

---

### Post by supernova1 on 2008-12-11
This solved my problem.  What does the lglut mean exactly.  Why is the glut.h file not sufficient?

Thanks,

Supernova

---

### Post by PandaGoat on 2008-12-11
glut.h only contains the signatures of the functions.  The code that defines the body of them are in an already compiled static library.  A static library is "linked" into the program at compile time by the (O_O!) linker.  

Passing -l to gcc tells it to link in a certain library specified after the l. Passing -lglut tells it to link in the glut library.  If glut was installed in the proper location (it probably was) the linker will find it.

Just including the header is not sufficient.

---

