---
title: "Opengl in linux"
date: 2007-09-10
forum: Programming Talk
---

### Post by AndrewGene on 2007-09-10
I am trying to run the simplest of opengl programs...

#include <gl/libglut.h> 
void mydisplay(){
     glClear(GL_COLOR_BUFFER_BIT); 
	glBegin(GL_POLYGON);        
		glVertex2f(-0.5, -0.5);        
		glVertex2f(-0.5, 0.5);        
		glVertex2f(0.5, 0.5);        
		glVertex2f(0.5, -0.5);    
	glEnd();
	glFlush(); 
}
int main(int argc, char** argv){
	glutInit($argc, argv);
	glutCreateWindow("simple");     
	glutDisplayFunc(mydisplay);    
	glutMainLoop();
}
...
I am typing this into the terminal
cd to the directory of the .cpp file and then type...

sudo gcc SimpleSquare3.cpp -lglut

...it however is giving me these errors...
SimpleSquare3.cpp:1:25: error: gl/libglut.h: No such file or directory
SimpleSquare3.cpp: In function ‘void mydisplay()’:
SimpleSquare3.cpp:3: error: ‘GL_COLOR_BUFFER_BIT’ was not declared in this scope
SimpleSquare3.cpp:3: error: ‘glClear’ was not declared in this scope
SimpleSquare3.cpp:4: error: ‘GL_POLYGON’ was not declared in this scope
SimpleSquare3.cpp:4: error: ‘glBegin’ was not declared in this scope
SimpleSquare3.cpp:5: error: ‘glVertex2f’ was not declared in this scope
SimpleSquare3.cpp:9: error: ‘glEnd’ was not declared in this scope
SimpleSquare3.cpp:10: error: ‘glFlush’ was not declared in this scope
SimpleSquare3.cpp: In function ‘int main(int, char**)’:
SimpleSquare3.cpp:13: error: ‘$argc’ was not declared in this scope
SimpleSquare3.cpp:13: error: ‘glutInit’ was not declared in this scope
SimpleSquare3.cpp:14: error: ‘glutCreateWindow’ was not declared in this scope
SimpleSquare3.cpp:15: error: ‘glutDisplayFunc’ was not declared in this scope
SimpleSquare3.cpp:16: error: ‘glutMainLoop’ was not declared in this scope

any help would be appreciated thanks. I have looked up how to link to a library and read several articles but my system doesn't have the libglut.h anywhere or libglut.a/libglut.so which is what i believe i am looking for.

---

### Post by olejorgen on 2007-09-10
I think that should be #include <gl/glut.h>

---

### Post by AndrewGene on 2007-09-10
I got the same error message.  Anything else?  Maybe we should verify my files again??? What should i have in order to compile this thing?

---

### Post by nrs on 2007-09-10
#include <GL/glut.h> *
&argc *

---

### Post by AndrewGene on 2007-09-10
That worked thank you so much!!! I've been trying for hours to fix this all day.  I can't believe that it was that simple.

Now, not that it matters, but can I have this image of a square show up while i'm running compiz-fusion??  It blips in when running CF but it isn't constant.  I have to turn it off to see it full time (it is really not a big deal but I am just curious).

---

### Post by fct on 2007-09-11
Compiz fusion is still unstable and prone to have errors left. Plus depending on the graphics card and the driver you're using, you could hit some quirks.

For example, with the current driver for intel GPUs it's not quite pleasant to play videos using xv while running compiz at the same time.

So if you want to check your GL program, it's a good idea to turn off compiz-fusion.

---

### Post by Wybiral on 2007-09-11
Yeah, my computer doesn't show any OpenGL surface when I'm running Beryl or Compiz... It's just a solid white window.

---

### Post by AndrewGene on 2007-09-11
Alrighty, thanks guys.  That's what i figured.

---

### Post by genux05 on 2010-03-01
I had a similar problem whilst testing out the glut hello world test program, and encase this helps anyone else.

aptitude install freeglut3-dev 

and then 

gcc -o helloworld helloworld.cpp -lGL -lglut

the -l means the library to include is the GL (graphics library) and also the lowercase glut graphics library.

---

### Post by Drone022 on 2010-03-02
> #include <GL/glut.h> *
&argc *

I've never seen this before, can someone explain how this solved the problem?

Just curious.

---

