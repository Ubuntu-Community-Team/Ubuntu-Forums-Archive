---
title: "ANSI C - Compile &amp; link Problem."
date: 2009-01-26
forum: Programming Talk
---

### Post by prasath_amd on 2009-01-26
I have a Simple-OpenGLUT program written in ANSI C that will display a window with a red-triangle inside it. ( Given in the first chapter of my CG book )

**_Here is the Code:-_**

```
#include <stdio.h>
#include <stdlib.h>
#include <GL/glut.h>

void init(void); 		
void Display(void);

int main(int argc,char *argv[])
{
	glutInitDisplayMode(GLUT_SINGLE|GLUT_RGB);
	glutInitWindowSize(320,240);
	init();
	glutDisplayFunc(Display);
	glutMainLoop();
	return 0;
}

void init(void)
{
	glClearColor(1.0,0.0,0.0,1.0);
	glViewPort(0,0,320,240);
	gluOrtho2D(0.0,160.0,0.0,120.0);
}

void Display(void)
{
	glClear(GL_COLOR_BUFFER_BIT);
	glFlush();
}
```

The **ANSI C** & **GL** & **GLU** & **GLUT** include files are @ the **"/usr/include"** & **"/usr/include/GL"** dirs.

The **libGL.so**, **libGLU.so**, **libglut.so** shared libraries are @ the **"/usr/lib"** dir.

_**My Compile-Command @ the terminal:-**_

gcc Test.c -o Test

_**Output Of The Compiler:-**_

[HTML]/tmp/cczZm8vp.o: In function `main':
Test.c:(.text+0x19): undefined reference to `glutInitDisplayMode'
Test.c:(.text+0x2d): undefined reference to `glutInitWindowSize'
Test.c:(.text+0x3e): undefined reference to `glutDisplayFunc'
Test.c:(.text+0x43): undefined reference to `glutMainLoop'
/tmp/cczZm8vp.o: In function `init':
Test.c:(.text+0x7f): undefined reference to `glClearColor'
Test.c:(.text+0xa3): undefined reference to `glViewPort'
Test.c:(.text+0xc7): undefined reference to `gluOrtho2D'
/tmp/cczZm8vp.o: In function `Display':
Test.c:(.text+0xdb): undefined reference to `glClear'
Test.c:(.text+0xe0): undefined reference to `glFlush'
collect2: ld returned 1 exit status[/HTML]

the **"/usr/lib"** & **"/usr/include"** dirs where in the default search path for GCC right?

**Then what could be the problem? Plz help.**

---

### Post by johnl on 2009-01-26
Yes, the files are in the right place, but you need to tell gcc to link to them. With -l<name minus 'lib' prefix>

In this case (not sure exactly which libraries you need to link to)

```

gcc Test.c -o Test -lglut

```

Hope this helps.

---

### Post by prasath_amd on 2009-01-26
**_Nope tried it:_**

gcc Test.c -o Test -lglut

**_output:-_**

/usr/bin/ld: cannot find -lglut
collect2: ld returned 1 exit status

Anyway, is it '-l' or '-I'?

---

### Post by bruce89 on 2009-01-26
-IGL -IGLU -Iglut -lGL -lGLU -lglut are the flags. Why they don't provide a pkg-config file, I don't know.

Also, all your functions should be static unless you need to call them from other modules (in this case, init and Display). I find having main at the bottom easier, as it means you don't need to bother with forward declarations.

---

### Post by prasath_amd on 2009-01-26
gcc Test.c -o Test -lGL -lGLU -lglut

output:-

/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status

Something is wrong, i don't know what is plz help me...... :cry:

---

### Post by bruce89 on 2009-01-26
> **prasath_amd said:**
> gcc Test.c -o Test -lGL -lGLU -lglut

output:-

/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status

Something is wrong, i don't know what is plz help me...... :cry:

I assume you have freeglut3-dev installed.

---

### Post by prasath_amd on 2009-01-26
Yes, the package manager shows it as installed, so what? how can i use it?. Man I just need to run some OpenGL programs... :x

---

### Post by slavik on 2009-01-27
try running:

```
sudo ldconfig
``` then try the linking again

---

### Post by prasath_amd on 2009-01-27
Nope still the error persists...

gcc Test.c -o Test

[HTML]/tmp/ccMQqZ3n.o: In function `main':
Test.c:(.text+0x19): undefined reference to `glutInitDisplayMode'
Test.c:(.text+0x2d): undefined reference to `glutInitWindowSize'
Test.c:(.text+0x3e): undefined reference to `glutDisplayFunc'
Test.c:(.text+0x43): undefined reference to `glutMainLoop'
/tmp/ccMQqZ3n.o: In function `init':
Test.c:(.text+0x7f): undefined reference to `glClearColor'
Test.c:(.text+0xa3): undefined reference to `glViewPort'
Test.c:(.text+0xc7): undefined reference to `gluOrtho2D'
/tmp/ccMQqZ3n.o: In function `Display':
Test.c:(.text+0xdb): undefined reference to `glClear'
Test.c:(.text+0xe0): undefined reference to `glFlush'
collect2: ld returned 1 exit status[/HTML]

---

### Post by slavik on 2009-01-27
can you add -lglut to your compile line?

---

### Post by prasath_amd on 2009-01-27
Yes,

gcc Test.c -o Test -lglut

still the error persists

PS: the "sudo apt-get install build-essential" command is also not working.

---

### Post by Zugzwang on 2009-01-27
> **prasath_amd said:**
> 
PS: the "sudo apt-get install build-essential" command is also not working.

That might be severe. What is the error message you get (please copy and paste)?

---

### Post by prasath_amd on 2009-01-27
[HTML]$ sudo apt-get install build-essential

[sudo] password for prasath: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential[/HTML]

this is what i get... for ** "sudo apt-get install build-essential"**

PS:I don't see any package named "build-essential" in the Synaptic package Manager also

---

### Post by prasath_amd on 2009-01-28
Hey guys somebody help me plz, as i said,

even the **"sudo apt-get install build-essential"** command is not working. :(

---

### Post by slavik on 2009-01-28
What repositories do you have enabled?

---

