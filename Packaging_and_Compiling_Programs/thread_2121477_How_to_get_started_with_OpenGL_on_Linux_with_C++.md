---
title: "How to get started with OpenGL on Linux with C++?"
date: 2013-03-02
forum: Packaging and Compiling Programs
---

### Post by eiger3970 on 2013-03-02
Hi,
I have tried running a 1st OpenGL program and receive the error: Permission denied.


1. To setup OpenGL with Linux Mint Mate I:
Linux > Terminal > (go to folder to store new file. E.g.: /media/All files) > touch BasicGLUT.cpp > nano BasicGLUT.cpp > (enter code and save file) > g++ BasicGLUT.cpp -o BasicGlut -lglut -lGL > ./BasicGlut > Permission denied.
I also tried g++ BasicGLUT.cpp -lGL -lGLU -lglut -lm -o BasicGlut > Permission denied.




2. To setup OpenGL with Linux Mint Mate with NetBeans 7.3 with C++ I:
Install OpenGL to Linux: url
Linux > Terminal > sudo apt-get update
Linux > Terminal > sudo apt-get install libgl1-mesa-dev
Linux > Terminal > sudo apt-get update
Linux > Terminal > sudo apt-get install build-essential
Linux > Terminal > sudo apt-get install libglew1.5-dev freeglut3-dev libglm-dev
glxinfo | grep OpenGL


Install NetBeans: url
Download NetBeans: url
Download > Terminal > go to Downloads folder with the downloaded Netbeans file > chmod +x netbeans-7.3-linux.sh > ./netbeans-7.3-linux.sh > netbeans.


NetBeans has problems like:
Mouse click doesn't hold submenu's from ribbon menu like File etc...
Compile gives errors:
make[2]: *** [dist/Debug/GNU-Linux-x86/text_book_page_46] Error 1 
make[2]: Leaving directory `/media/All files/Text book page 46' 
make[1]: *** [.build-conf] Error 2 
make[1]: Leaving directory `/media/All files/Text book page 46' 
make: *** [.build-impl] Error 2 
BUILD FAILED (exit value 2, total time: 375ms) 




Here is my code I'm using:
// #include <GL/GLUT.h> // Might need to change this for Linux, as this example is for a Mac.
#include <GL/gl.h>
#include <GL/glut.h>


void render(void);


int main(int argc, char** argv)
{
	glutInit(&argc, argv);
	glutInitDisplayMode(GLUT_DEPTH | GLUT_DOUBLE | GLUT_RGBA);
	glutInitWindowPosition(100, 100);
	glutInitWindowSize(640, 480);
	glutCreateWindow("Simple GLUT application");


	glutDisplayFunc(render);


	glutMainLoop(); // Says process has finished and can start rendering.
}


void render(void)
{


}

---

### Post by Mr. Shannon on 2013-03-02
Do a:
```
ls -l BasicGLUT.cpp
```
and
```
ls -l BasicGlut
```
inside the directory containing BasicGLUT.cpp and post the result.  It sounds like a permissions issue.

---

### Post by eiger3970 on 2013-03-02
> **Mr. Shannon said:**
> Do a:
```
ls -l BasicGLUT.cpp
```
and
```
ls -l BasicGlut
```
inside the directory containing BasicGLUT.cpp and post the result.  It sounds like a permissions issue.

Thanks for the reply.
ls -l BasicGLUT.cpp, outputs the result:
-rw------- 1 ken ken 510 Mar  2 16:41 BasicGLUT.cpp

ls -l BasicGlut, outputs the result:
-rw------- 1 ken ken 8709 Mar  3 12:24 BasicGlut

---

### Post by melfnt on 2013-03-03
try to give exec permission to the output file:
```

chmod +x BasicGlut

```

and then, again
```

./BasicGlut

```

Btw it's very strange, because the output files of g++ should have execution permissions by default.

Bye
;)

---

