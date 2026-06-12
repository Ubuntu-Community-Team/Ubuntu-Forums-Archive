---
title: "&lt;GL/glut.h&gt; not included included.............."
date: 2009-03-28
forum: Programming Talk
---

### Post by abhilashm86 on 2009-03-28
while doing OpenGL programming in Qt 4.5, it is not recognising basic OPenGL functions(built in),i included <GL/glut.h> library in the program, whats actually wrong happening?

here is my main program
[PHP]
int main(int argc,char **argv)
{
        printf("enter number of divisions");
        scanf("%d",&n);

        glutInit(&argc,argv);
        glutInitDisplayMode(GLUT_SINGLE|GLUT_DEPTH|GLUT_RGB);
        glutInitWindowSize(500,500);
        glutCreateWindow("3D GASKET");
        glutReshapeFunc(myReshape);
        glutDisplayFunc(display);
        glEnable(GL_DEPTH_TEST);
        glClearColor(1.0,1.0,1.0,1.0);
        glutMainLoop();
}


[/PHP]

it is giving errors shown below, 

```
/home/abhilash/abhi9/main.cpp:78: undefined reference to `glutInit'
/home/abhilash/abhi9/main.cpp:79: undefined reference to `glutInitDisplayMode'
/home/abhilash/abhi9/main.cpp:80: undefined reference to `glutInitWindowSize'

```

---

### Post by Peasantoid on 2009-03-28
If you were using gcc/g++, I'd tell you to do this:
```
g++ some_code.cpp -o an_executable -l opengl # Or whatever the linker thing for OpenGL is
```
Dunno what the deal with QT is, though.

---

### Post by abhilashm86 on 2009-03-28
> **Peasantoid said:**
> If you were using gcc/g++, I'd tell you to do this:
```
g++ some_code.cpp -o an_executable -l opengl # Or whatever the linker thing for OpenGL is
```


actually i follow this to execute opengl programs,
```
 
g++ open4.cpp -lm -lGL -L/usr/X11R6/lib -lGLU -lglut -o gasket

```
how do u link with -l opengl? compiler returns this error,
```

abhilash@abhi:~$ g++ open4.cpp -o gasket -l opengl
/usr/bin/ld: cannot find -lopengl

```

---

### Post by moma on 2009-03-28
Hello,

0) Install first freeglut-dev package.
(it contains the library and required header files).
$ [COLOR="Green"]sudo apt-get install freeglut3 freeglut3-dev[/COLOR]

1) Create a test.
```
#include <stdio.h>

#include <GL/glut.h>
#include <GL/gl.h>

void reshape_func()
{
...
}

void display_func()
{
...
}

int main(int argc,char **argv)
{
        printf("enter number of divisions");
	int n;
        scanf("%d",&n);

        glutInit(&argc,argv);
        glutInitDisplayMode(GLUT_SINGLE|GLUT_DEPTH|GLUT_RGB);
        glutInitWindowSize(500,500);
        glutCreateWindow("3D GASKET");
        glutReshapeFunc(reshape_func);
        glutDisplayFunc(display_func);
        glEnable(GL_DEPTH_TEST);
        glClearColor(1.0,1.0,1.0,1.0);
        glutMainLoop();
} 
```

2) Then compile and link it. Link to libGl.so and libglut.so dynamic libraries.
$ [COLOR="Green"]gcc -lGL -lglut test1.c -o test1[/COLOR]

3) Run it.
$ [COLOR="Green"]./test1[/COLOR]
----------------------

As another example, download and compile this OpenGL/GLUT program  (from [http://nehe.gamedev.net](http://nehe.gamedev.net))
[http://nehe.gamedev.net/data/lessons/linux/lesson02.tar.gz](http://nehe.gamedev.net/data/lessons/linux/lesson02.tar.gz)

Compile it 
$ [COLOR="Green"]gcc -lGL -lglut lesson2.c -o lesson2[/COLOR]

Run it.
$ [COLOR="Green"]./lesson2[/COLOR]

----------------------
Note: All lessons from the nehe.gamedev.net contain a **[Makefile]("http://linuxgazette.net/issue83/heriyanto.html")**. So you can compile the lesson by typing 
$ [COLOR="SeaGreen"]make [/COLOR]
make will read the rules in Makefile and compile the project accordingly.
----------------------

Note: You could also compile and link it in two steps.
First compile it. It produces an object file test1.o. Rrepeat this for each source file you have.
$ [COLOR="Green"]gcc -c test1.c [/COLOR]

Then link all object files (*.o) and libraries to an executable test1.
$ [COLOR="Green"]gcc -lGL -lglut test1.o -o test1[/COLOR]
----------------------

Read also **Note 5)** of [this document...]("http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html")

---

