---
title: "GLUT problem"
date: 2006-11-02
forum: Programming Talk
---

### Post by Zalbor on 2006-11-02
I'm trying to compile this program using gcc:
```
#include <GL/glut.h>

void init(void);
void display(void);

int main(int argc, char **argv)
{	glutInit(&argc,argv);
	glutInitDisplayMode(GLUT_SINGLE|GLUT_RGB);
	glutInitWindowSize(250,250);
	glutInitWindowPosition(100,100);
	glutCreateWindow("hello");
	init();
	glutDisplayFunc(display);
	glutMainLoop();
	return(0);
}

void display(void)
{	glClear(GL_COLOR_BUFFER_BIT);
	glColor3f(1.0,1.0,1.0);
	glBegin(GL_POLYGON);
		glVertex3f(0.25,0.25,0.0);
		glVertex3f(0.75,0.25,0.0);
		glVertex3f(0.75,0.75,0.0);
		glVertex3f(0.25,0.75,0.0);
	glEnd();
	glFlush();
}

void init(void)
{	glClearColor(0.0,0.0,0.0,0.0);
	glMatrixMode(GL_PROJECTION);
	glLoadIdentity();
	glOrtho(0.0,1.0,0.0,1.0,-1.0,1.0);
}
```
Supposedly, it displays a square. I tried it on a computer with windows and it worked.

I have both the gl.h and glut.h files. GCC returns:
```
/tmp/ccu6jNRI.o: In function `main':test1.c:(.text+0x2a): undefined reference to `glutInit'
:test1.c:(.text+0x36): undefined reference to `glutInitDisplayMode'
:test1.c:(.text+0x4a): undefined reference to `glutInitWindowSize'
:test1.c:(.text+0x5e): undefined reference to `glutInitWindowPosition'
:test1.c:(.text+0x6a): undefined reference to `glutCreateWindow'
:test1.c:(.text+0x7b): undefined reference to `glutDisplayFunc'
:test1.c:(.text+0x80): undefined reference to `glutMainLoop'
/tmp/ccu6jNRI.o: In function `display':test1.c:(.text+0x99): undefined reference to `glClear'
:test1.c:(.text+0xb8): undefined reference to `glColor3f'
:test1.c:(.text+0xc4): undefined reference to `glBegin'
:test1.c:(.text+0xe3): undefined reference to `glVertex3f'
:test1.c:(.text+0x102): undefined reference to `glVertex3f'
:test1.c:(.text+0x121): undefined reference to `glVertex3f'
:test1.c:(.text+0x140): undefined reference to `glVertex3f'
:test1.c:(.text+0x145): undefined reference to `glEnd'
:test1.c:(.text+0x14a): undefined reference to `glFlush'
/tmp/ccu6jNRI.o: In function `init':test1.c:(.text+0x17a): undefined reference to `glClearColor'
:test1.c:(.text+0x186): undefined reference to `glMatrixMode'
:test1.c:(.text+0x18b): undefined reference to `glLoadIdentity'
:test1.c:(.text+0x1b7): undefined reference to `glOrtho'
collect2: ld returned 1 exit status
```

Opening the freeglut_std.h file (which glut.h leads to), I saw that the above functions are indeed defined:
```
FGAPI void    FGAPIENTRY glutInit( int* pargc, char** argv );
FGAPI void    FGAPIENTRY glutInitWindowPosition( int x, int y );
FGAPI void    FGAPIENTRY glutInitWindowSize( int width, int height );
FGAPI void    FGAPIENTRY glutInitDisplayMode( unsigned int displayMode );
FGAPI void    FGAPIENTRY glutInitDisplayString( const char* displayMode );
```
I don't know what FGAPI is, but I saw it defined above:
```
/* Non-Windows definition of FGAPI and FGAPIENTRY  */
#        define FGAPI
#        define FGAPIENTRY
```

It seemed strange to me that there's no number to define these as, so I tried to compile this simple program:
```
#define FRFRFR
#include <stdio.h>

int main(void)
{	printf("%d",FRFRFR);
	return(0);
}
```
And just as I thought, it didn't work. When I added a 4 at the end of the first line, it did.

So what's the issue here? Is the freeglut_std.h file invalid? Please shed some light...

---

### Post by Zalbor on 2006-11-02
According to something I read, anything defined in this way should simply be replaced by blank space... Which means that the freeglut_std.h file should work as it is, but it doesn't...

---

### Post by po0f on 2006-11-02
Zalbor,

You're probably not linking to the GLUT libraries during compilation.  Try adding [FONT="Courier New"]-lGL[/FONT] to the end of your compiler command.  You will probably need to link in more libraries, but it might be a start.

---

### Post by Zalbor on 2006-11-02
That was it, thanks a lot!!!
I thought it might be something like this, but I didn't know where to look for the relevant options...

For the record, it needed -lGL and -lglut.

---

### Post by hod139 on 2006-11-02
If you use any of the glu* functions, you will also have to add -lglu

---

