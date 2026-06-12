---
title: "Works in terminal, but not in makefile"
date: 2013-01-05
forum: Programming Talk
---

### Post by jabozzo on 2013-01-05
Hi:

I've some experience programming on high-level (C#, java) and I thought it was time to learn some low-level stuff. I'm trying to make a test program using c++, opengl and make.

My .cpp is very simple:

```
#include <iostream>
#include <GL/glew.h>
#include <GL/glut.h>

void render();

int main(int argc, char** args){


	int exitCode = 0;

	
	glutInit(&argc, args);
	glutInitDisplayMode(GLUT_DEPTH | GLUT_DOUBLE | GLUT_RGBA);
	glutInitWindowPosition(100, 100);
	glutInitWindowSize(640,480);
	glutCreateWindow("Hi again");

	glutDisplayFunc(render);

	glutMainLoop();

	return exitCode;
}

void render (void){

}
```

And also I have coded a simple make file:

```
testings:  testings.o
	   g++ testings.o -o testings -lglut

testings.o: testings.cpp
	    g++ -c -Wall testings.cpp
```

I can compile my program from terminal running:

```
g++ -c -Wall testings.cpp
g++ testings.o -o testings -lglut
```

An it runs at expected (creates a window, and doesn't refresh the contents of it). But if when I use:

```
make testings
```

I get:

```
g++     testings.cpp   -o testings
/tmp/ccAjW2UV.o:testings.cpp:function main: error: undefined reference to 'glutInit'
/tmp/ccAjW2UV.o:testings.cpp:function main: error: undefined reference to 'glutInitDisplayMode'
/tmp/ccAjW2UV.o:testings.cpp:function main: error: undefined reference to 'glutInitWindowPosition'
/tmp/ccAjW2UV.o:testings.cpp:function main: error: undefined reference to 'glutInitWindowSize'
/tmp/ccAjW2UV.o:testings.cpp:function main: error: undefined reference to 'glutCreateWindow'
/tmp/ccAjW2UV.o:testings.cpp:function main: error: undefined reference to 'glutDisplayFunc'
/tmp/ccAjW2UV.o:testings.cpp:function main: error: undefined reference to 'glutMainLoop'
collect2: error: ld returned 1 exit status
make: *** [testings] Error 1
```

From the little I know, this means the compiler is missing some links, but the link I've provided are the same for the terminal and the makefile (-lglut). I don't believe it's because it's missing a library, because I've installed:

libglew1.8
glew-utils
libglew-dev
freeglut3
freeglut3-dev.

I've have the feeling that it's probably my mistake in some subtlety the makefile, but hours have passed and I can't find the error (I'ts almost 4 am here).

That's it, thank you for reading this far an let's hope it's just a little thingy ;)

---

### Post by Lux Perpetua on 2013-01-05
Works for me: ```
% cat testings.cpp
#include <iostream>
#include <GL/glew.h>
#include <GL/glut.h>

void render();

int main(int argc, char** args){


        int exitCode = 0;

        
        glutInit(&argc, args);
        glutInitDisplayMode(GLUT_DEPTH | GLUT_DOUBLE | GLUT_RGBA);
        glutInitWindowPosition(100, 100);
        glutInitWindowSize(640,480);
        glutCreateWindow("Hi again");

        glutDisplayFunc(render);

        glutMainLoop();

        return exitCode;
}

void render (void){

}
% cat Makefile
testings:  testings.o
           g++ testings.o -o testings -lglut

testings.o: testings.cpp
            g++ -c -Wall testings.cpp
% make testings
g++ -c -Wall testings.cpp
g++ testings.o -o testings -lglut
%    
```
When you ran **make testings**, make did not use your makefile rule; rather, it used an implicit rule (check the compilation command: it is not what you wrote).  I'm guessing you misspelled the name of your makefile or something similar, and as a result make is not finding your makefile.

A few more tips regarding make:
[list]
[*]You can prevent the use of implicit rules by supplying the "-r" switch (e.g., **make -r testings**).  If your makefile has an explicit rule for every target, then you probably want this.  It can reveal subtle errors that are difficult to spot otherwise. 
[*]If your makefile is not named "Makefile" or "makefile", you can still use it by naming it explicitly via the "-f" option (e.g., **make -f my_makefile testings**).  But makefiles are usually just named "Makefile", in which case you wouldn't need this.
[/list]

---

### Post by jabozzo on 2013-01-05
Awesome! That did the trick. I was missing the file parameter since I named it makeFile.make.

Thank you!

---

### Post by dwhitney67 on 2013-01-05
> **jabozzo said:**
> But if when I use:
```
make testings
```


You can run 'make' to build an executable from an individual source file.  Thus if you had a file named 'foo.cpp' and wanted to build an executable with the name 'foo', simply entering 'make foo' would do the magic.  'Make' would know to reference the current directory for a file named 'foo.cpp' (or 'foo.c' for C development) to attempt to build the executable.

From what you describe, and from the results you posted, it would appear that this is what is transpiring on your system.

Did you create the Makefile *after* your initial attempt to run 'make'?  Is the Makefile in the same directory as your source file?  The results you posted are inconsistent with what I would have expected to see otherwise.

--------

Edit:  Never mind... it seems that the issue has been identified.

---

### Post by jabozzo on 2013-01-05
> **dwhitney67 said:**
> You can run 'make' to build an executable from an individual source file.  Thus if you had a file named 'foo.cpp' and wanted to build an executable with the name 'foo', simply entering 'make foo' would do the magic.  'Make' would know to reference the current directory for a file named 'foo.cpp' (or 'foo.c' for C development) to attempt to build the executable.


I didn't knew that, thanks for the info!

---

