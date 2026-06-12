---
title: "Comparing C++ to Python"
date: 2006-12-11
forum: Programming Talk
---

### Post by Wybiral on 2006-12-11
Ok, I am going to stand on this line in this one, I actually use C++ and Python both a lot. I refuse to favor either of them *generally*

However, I've seen a lot of people argue that many interpreted languages can compete with the speed of C++, even with graphical program... And I have to say, particularly when it comes to OpenGL graphical programs like games and such, I disagree. I am not saying that I am right, but I am saying that is my experience. To demonstrate, I would like you to have OpenGL properly installed on your computer (probably via mesa), along with GLUT (probably via freeGLUT). You will also need the python binding to openGL (pyOpenGL). Now, I've written a program that is *almost* identical in each of them. Here is the C++ one...

```

// !# C++ version

#include <GL/gl.h>
#include <GL/glu.h>
#include <GL/glut.h>

#include <stdlib.h>

class particle{public:
 float x, y, z;
 particle(){x=(rand()%200-100)*.01; y=(rand()%200-100)*.01; z=(rand()%200-100)*.01;};
 void draw(){
  glVertex3f(x, y, z);
  }
 };

void scene(){
 particle system[10000];
 float angle = 0.0;
 while(true){
  glLoadIdentity();
  glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT);
  glTranslatef(0.0,0.0,-5.0);
  glRotatef(angle,1.0,1.0,0.0);
  glBegin(GL_POINTS);
  for(int i=0; i< 10000; i++){system[i].draw();}
  glEnd();
  angle += 0.25;
  glutSwapBuffers();
  }
 }

int main(int argc, char** argv) {
 glutInit(&argc, argv);
 glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE | GLUT_DEPTH);
 glutInitWindowSize(640, 480);
 glutCreateWindow("Python & OpenGL Demo");
 glEnable(GL_DEPTH_TEST);
 glViewport(0, 0, 640, 480);
 glMatrixMode(GL_PROJECTION);
 glLoadIdentity();
 gluPerspective(45.0, 1.33, 0.1, 100.0);
 glMatrixMode(GL_MODELVIEW);
 glutDisplayFunc(scene);
 glutMainLoop();
 }

```

And here is the Python one...
```

#!/usr/bin/env python
 
from OpenGL.GL import *
from OpenGL.GLUT import *
from OpenGL.GLU import *
import sys
import random

class particle:
 def __init__(self):
  self.x = random.uniform(-1, 1)
  self.y = random.uniform(-1, 1)
  self.z = random.uniform(-1, 1)
 def draw(self):
  glVertex3f(self.x, self.y, self.z)

def scene():
 system = []
 angle = 0.0
 for i in range(10000):
  system += [particle()] 
 while 1:
  glLoadIdentity()
  glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT)
  glTranslatef(0.0,0.0,-5.0)
  glRotatef(angle,1.0,1.0,0.0)
  glBegin(GL_POINTS)
  for i in range(10000): system[i].draw()
  glEnd()
  angle += 0.25
  glutSwapBuffers()
 
def main():
 glutInit(sys.argv)
 glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE | GLUT_DEPTH)
 glutInitWindowSize(640, 480)
 glutCreateWindow("Python & OpenGL Demo")
 glEnable(GL_DEPTH_TEST)
 glViewport(0, 0, 640, 480)
 glMatrixMode(GL_PROJECTION)
 glLoadIdentity()
 gluPerspective(45.0, 1.33, 0.1, 100.0)
 glMatrixMode(GL_MODELVIEW)
 glutDisplayFunc(scene)
 glutMainLoop()
main()

```

The C++ one can be compiled using "g++ program.cpp -lglut -lGLU -lGL" and executed using "./a.out" from the resulting executable.

The python one is executed using "python program.py"

There is no FPS counter because I didn't want to allow for any more variation in the code, but you can easily count rotations-per-minute with a stopwatch. This may just be my computer, but after running this a few times with each I have noticed that the C++ version is considerably faster than the python one. If I am forgetting something, or doing something wrong here, please let me know.

But, one thing that I also noticed is how similar the code is... Almost identical. Even a non-programmer could look at it and see the same program. The only major differences are the use of lists instead of arrays in the python one, and the use of random is different due to a lack of similarity (this wont affect the speed, the random routine is done BEFORE the rendering loop).

Anyway, thats all. I just though I would share this. Like I said, I am open to corrections if I went about testing this wrong.

EDIT:

btw, this program may be pretty CPU intensive, I creates 10000 particles and then displays them in a loop. You may adjust the number 10000 in each of them to try different speeds. (less=faster, more=slower)

---

### Post by Choad on 2006-12-11
quite cool but alltogether unsuprising. compiled languages are faster than interpreted? colour me intrigued :p

---

### Post by Wybiral on 2006-12-11
That's what I've always thought, but I have seen people argue themselves blue over the subject. Don't get me wrong though... I love python. I use it a lot, and I certainly wont stop anytime soon. But I love it because it is simple and elegant, not because it is fast. But also... It isn't slow or anything either, 10000 particles is a lot of freaking particles, I'm actually impressed it runs as well as it does!

---

### Post by Wybiral on 2006-12-11
I had an idea, I can eliminate the main difference by using display lists instead of an array or a python list! I almost have to eat my words with this example because they run at nearly equal speeds!!!

Cpp:
```

// !# C++ version

#include <GL/gl.h>
#include <GL/glu.h>
#include <GL/glut.h>

#include <stdlib.h>

void scene(){
 float angle = 0.0;
 glNewList(1, GL_COMPILE);
 glBegin(GL_POINTS);
 for(int i=0; i< 20000; i++)
  glVertex3f((rand()%200-100)*.01, (rand()%200-100)*.01, (rand()%200-100)*.01);
 glEnd();
 glEndList();
 while(true){
  glLoadIdentity();
  glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT);
  glTranslatef(0.0,0.0,-5.0);
  glRotatef(angle,1.0,1.0,0.0);
  glCallList(1);
  angle += 0.25;
  glutSwapBuffers();
  }
 }

int main(int argc, char** argv) {
 glutInit(&argc, argv);
 glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE | GLUT_DEPTH);
 glutInitWindowSize(640, 480);
 glutCreateWindow("Python & OpenGL Demo");
 glEnable(GL_DEPTH_TEST);
 glViewport(0, 0, 640, 480);
 glMatrixMode(GL_PROJECTION);
 glLoadIdentity();
 gluPerspective(45.0, 1.33, 0.1, 100.0);
 glMatrixMode(GL_MODELVIEW);
 glutDisplayFunc(scene);
 glutMainLoop();
 }

```

Python:
```

#!/usr/bin/env python
 
from OpenGL.GL import *
from OpenGL.GLUT import *
from OpenGL.GLU import *
import sys
import random

def scene():
 angle = 0.0
 glNewList(1, GL_COMPILE)
 glBegin(GL_POINTS)
 for i in range(20000):
  glVertex3f(random.uniform(-1, 1), random.uniform(-1, 1), random.uniform(-1, 1))
 glEnd()
 glEndList()
 while 1:
  glLoadIdentity()
  glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT)
  glTranslatef(0.0,0.0,-5.0)
  glRotatef(angle,1.0,1.0,0.0)
  glCallList(1)
  angle += 0.25
  glutSwapBuffers()
 


def main():
 glutInit(sys.argv)
 glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE | GLUT_DEPTH)
 glutInitWindowSize(640, 480)
 glutCreateWindow("Python & OpenGL Demo")
 glEnable(GL_DEPTH_TEST)
 glViewport(0, 0, 640, 480)
 glMatrixMode(GL_PROJECTION)
 glLoadIdentity()
 gluPerspective(45.0, 1.33, 0.1, 100.0)
 glMatrixMode(GL_MODELVIEW)
 glutDisplayFunc(scene)
 glutMainLoop()
main()

```

BTW, I've upped the stakes to displaying 20000 particles instead of 10000 because of the speed increase from using display lists.

The only problem here is that scenes are not alway capable of being precompiled like this. So, while this example may be identical speeds, this does not apply to every program, and considering the use of non-compiled scenes is probably more common (unless you are always planning to use static scenes) I would still have to vote that C++ will be faster most of the time.

But it is very interesting how fast python is able to run an OpenGL program like this.

---

### Post by Choad on 2006-12-11
no matter which way you turn it, identical code in an interpreted language will be at best nearly the same speed as c++

if speed is your game, c++ is your tool. there is a reason why something like 95% of modern commercial games are written in c++

---

### Post by slavik on 2006-12-11
Wybiral, thank you for the testing ...

so, what results did you get? I personally wouldn't mind dropping 5% perfomance for easier editing. Also, try compiling the python code, let's see what that does. :)

---

### Post by engla on 2006-12-11
Now this tells you something more interesting.

Given how equal the code is, it's probably worth it to prototype _everything_ in python, then move finished bits of the OpenGL app to C++

And, did you run this code with Psycho (a Python optimizer/thing)

---

### Post by Wybiral on 2006-12-11
Well, on my computer the example that did NOT use display list's (as in the openGL rendering was all realtime, display lists precompile the scene to increase speed) I had almost TWICE the speed with C++ (I counted about 2 times more rotations than the python script per minute). I am curious how it runs on other computers and with other versions of python if someone would like to test it.

I am using 2.5 for the record. Now... With the display lists added, I had an almost equal count every time (give or take a few) and I would say that with static scenes, using display lists, you will probably not see any speed decrease at all (probably due to the fact that OpenGL will be handling the entire process rather than the language).

While I didn't do any FPS calculating (I didn't want to ruin the purity of the experiment with FPS counting routines) I can say that python is still pretty good at handling OpenGL with pyOpenGL. It ran very smoothly even with the butt-load of particles I was making it render. And with the use of display list's... Forget about it... Very nice frame-rate on my end. But, I still have to say, if you demand maximum speed, C++ is probably the way to go. But, if speed isn't a huge issue, python for sure.

Python is very easy to write things like this in... However, for anyone afraid to use C++ who is overly comfortable with python, this example speaks for itself, the code for each is almost identical! Paste each of them to a file and set them up next to each other... Its really weird to look at in my opinion.

EDIT:

Nope, it was just plain old python. I haven't messed with any optimizers or anything yet. And it was not compiled or anything like that, just "python program.py"

---

### Post by slavik on 2006-12-11
well, why not make a specific number of loop iterations and then use the time function ...

---

### Post by pmasiar on 2006-12-11
> **Choad said:**
> no matter which way you turn it, identical code in an interpreted language will be at best nearly the same speed as c++

if speed is your game, c++ is your tool. there is a reason why something like 95% of modern commercial games are written in c++

I'll bite. Of course raw speed is better in C++. I agree 100%. Let me play the devil's advocate (or the angel's, or the python's :-) ): why you could *still* be better off using "slower" python?

[LIST=1]
[*]**Speed-to-market** might be more important than processing speed. If you are in the startup, having your killer app out on the market 3 months ahead of the competition, and being able match features of your competitors within a week, might be more important. If your application scales well, as you gain users you can dump more cheap servers to run it. Thats what Google does. Google also employs many top-level Python hackers, including [Guido]("http://en.wikipedia.org/wiki/Guido_van_Rossum") and [Alex Martelli]("http://en.wikipedia.org/wiki/Alex_Martelli").

[*]Save speed by **implementing efficent design**, not by optimizing loops and function calls. Agile language like python allows you to try multiple approaches, refactor quickly, and still have functioning code. 

[*]**Find bottlenecks and optimize only those** - maybe even reimplement them in C. You may find out that 90% of the time is spent in 5% of the code. If python allows you to develop code 10 times faster, it would be waste of time to implement 95% of non-critical code in C/C++, and premature optimization. [Speed is not a problem until it is a problem]("http://en.wikipedia.org/wiki/Python_%28programming_language%29#Eschew_premature_optimization"). And we know that premature optimization is root of all evil.
[*]**use [NumPy module]("http://en.wikipedia.org/wiki/Numpy")** for fast calculations on big matrices, implemented in C (runs with speed of C).
[*]Maintenance cost and cost of adding new functions. I read recently that with operating environment changing quickly, companies might need to change internal process every 2 years. Having flexible IT infrastucture allowing that is crucial.
[/LIST]

I actually like C. I coded in assembler before and with C, I really love the feeling what it generates efficient binary for me. It is doing what I would do  in assembler. But in python I am just so much more productive... :-)

---

### Post by Wybiral on 2006-12-11
While I agree with you on most of that, and like I said, I am just posting my results... I am not supporting either language. This experiment actually surprised the hell out of me when I added the display lists and got a good framerate in python with 20000 (and even above that it was pretty decent, on my not-so-decent computer).

I will, however, disagree with this statement "premature optimization is root of all evil"

My opinion is "optimize now, rest easy later" because after you implement everything, it becomes more and more difficult to find those bottlenecks and find the right way to change and re-implement things to work around them. I prefer to take the headache now and optimize it to it's fullest, as opposed to just writing it and then having to go back and slave over fixing it all.

That's just my opinion, maybe you're one of those people who likes to get something done and then perfect it. I mostly like to do everything the best I can to start with and then relax.

EDIT:

I always ate the alphabets in my cereal first and then enjoyed the marshmallowy goodness.

---

### Post by pmasiar on 2006-12-11
Just found on [http://www.planetpython.org/:](http://www.planetpython.org/:) a game in crossplatform python: [Galcon - risk with spaceships]("http://renesd.blogspot.com/2006/12/galcon-released.html") So at least *some* games are made in python! :-)

---

### Post by engla on 2006-12-11
Well wasn't Civilization IV made with Python?

Wikipedia seems to suggest that a large part of the front end was written in Python (and can actually be customized). It's unclear if "Major parts of the interface" means that they actually use pyopengl

---

### Post by Choad on 2006-12-11
yeah im sure plenty of games do the lighter stuff in python. maybe even the ai because its a good language for that kind of stuff. its just not as fast. thats all there is to it. thats why openGL is compiled in c, its why SDL is compiled in c, in fact the only reason the second example runs so much faster than the first, is because it uses the openGL data structure instead of the python one.

but of course its down to the right tool for the job, and for the user interface of civ 4 its obviously a perfectly suitable tool for the job because the UI is not going to be doing masses of computing. especially compared to the game engine (and if that is made in python i will eat my own face)

---

### Post by daniminas on 2006-12-11
c++ games are much faster...
script based games are cool to make game-tests ;) .. not to develop a complex games

C++!! 8)

---

### Post by pmasiar on 2006-12-11
> **daniminas said:**
> c++ games are much faster...

<joke>Games written in assembler are even faster. C++ is for weaklings who cannot handle real complexity.</joke>

As I said before, you can always recode 5% of time-critical code in C - but only *after* you found what that code is!

---

### Post by MadMan2k on 2006-12-11
here you go:
[http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=gpp&lang2=python](http://shootout.alioth.debian.org/debian/benchmark.php?test=all&lang=gpp&lang2=python)

c++ is usually about 50 times faster than python.

---

### Post by hod139 on 2006-12-11
> **pmasiar said:**
> <joke>Games written in assembler are even faster. C++ is for weaklings who cannot handle real complexity.</joke>

I know it is labeled as a joke, but I wonder how true that statement is with modern compilers.  I'm willing to bet that the optimizations a modern compiler can do can produce just as fast or even faster assembly than hand-tuning by an assembly programmer.

As long as python is interpreted it simply cannot be as fast as a compiled language.  However, as others have noted, there are other factors such as development time etc that you can count as speed.  

Here's a question though as a non-python programmer, I always hear the argument that it is so much faster to develop in python than in other languages.  Is this true for only novice programmers or do you Python programmers make this claim even for advanced C/C++ programmers?  I tend to advocate right tool for the right job, not one language to rule them all, but that's just me.

---

### Post by Wybiral on 2006-12-11
I use C++, Python, and occasionally ASM (but only as a hobby, you are correct about C++ compilers, you would have to be an ASM god to keep up with todays c++ compilers) and I think they must each be put in a separate view box...

ASM is VERY difficult to develop with, but produces VERY slim and fast code (you don't need a bunch of extra just and op-codes used in generalized compiler functions). But, a program in ASM is usually 50 (or much more) times the number of lines an equivalent program written in C++ could be. However, since you can write only the needed routines specialized for your program, executable sizes are tiny... Sometimes in the 100's bytes range.

C++'s compilers optimize code very well, for both speed and size. And C++ compiles to machine code that often closely resembled that of an optimized ASM program.

Python is very nice for developing... It takes half the time to crank out programs in python than in C++ and it looks pretty too... But, it doesn't compile to machine code and the result is a notable lag from equivalent c++ code. I also feel that large python project become somewhat difficult to manage (thats just my opinion).

So yeah, you do want small executables, speed, or simple developing. It really depends what you are working on.

---

### Post by neoflight on 2006-12-11
i agree that development time for python is really small....but once it gets to the customer.... one cannot justify that  

"its slow in execution i agree, but hey you know what, it didn't take that long to make ! "...

what will the  customers/users look for:

1. that took less time to make..... OR
2. that executes really fast...

I think, with a decent skill level, 50% faster execution is worth spending 50% more time developing.

i like python though...

just thinking aloud...:-k

---

### Post by Wybiral on 2006-12-11
Here's an example I wrote of pythons ability to create 3d graphics. It's a 3d terrain walkdemo. There's no texture on the terrain so it looks like crap, but the arrow keys control and page up/down looks up/down. This should clear up the question of whether python is ABLE to make decent 3d games. It most certainly is. But I am still of the opinion that C++ is a faster and better suited for theme.

(btw, this didn't take much time to write in python at all, python code comes together very elegantly, but it could probably be optimized a lot more)

```

#!/usr/bin/env python
 
from OpenGL.GL import *
from OpenGL.GLUT import *
from OpenGL.GLU import *
from math import *
import sys
import random

# Initialize key states to 0
KEY_PUP = 0
KEY_PDOWN = 0
KEY_UP = 0
KEY_DOWN = 0
KEY_LEFT = 0
KEY_RIGHT = 0

# Initialize camera variables
camX  = 0.0
camZ  = 0.0
camXA = 0.0
camYA = 0.0

# List used to store heighmap
terrain = []

def buildTerrain(width, height):
 global camX, camZ, terrain
 # Place camera in center of terrain
 camX = width/2.0
 camZ = height/2.0
 # Generate random points
 for x in range(width):
  terrain += [[]]
  for y in range(height):
   terrain[x] += [random.uniform(0, 10)]
 # Smooth randome points
 for i in range(2):
  for x in range(width):
   for y in range(height):
    hSum = 0.0
    for a in range(-1,2):
     for b in range(-1,2):
      if(x+a>0 and x+a<width):
       if(y+b>0 and y+b<height):
        hSum += terrain[x+a][y+b]
    terrain[x][y] = hSum/9
 # Build display list
 glNewList(1, GL_COMPILE)
 glBegin(GL_TRIANGLES)
 for x in range(len(terrain) - 1):
  for y in range(len(terrain[0]) - 1):
   glColor3f(random.uniform(0, .4)+.6,random.uniform(0, .2)+.5,0)
   glVertex3f(x,   terrain[x  ][y+1], y+1)
   glVertex3f(x+1, terrain[x+1][y+1], y+1)
   glVertex3f(x+1, terrain[x+1][y  ], y  )
   glVertex3f(x+1, terrain[x+1][y  ], y  )
   glVertex3f(x,   terrain[x  ][y  ], y  )
   glVertex3f(x,   terrain[x  ][y+1], y+1)
 glEnd()
 glEndList()
 
# Check constrained values and return elevation
def doCheck():
 global terrain, camX, camZ, camXA
 if camX < 0:
  camX = 0
 elif camX > len(terrain)-2:
  camX = len(terrain)-2
 if camZ < 0:
  camZ = 0
 elif camZ > len(terrain[0])-2:
  camZ = len(terrain[0])-2
 if camXA < -20:
  camXA = -20
 elif camXA >  40:
  camXA =  40
 iX = int(camX)
 iZ = int(camZ)
 fX = camX - iX
 fZ = camZ - iZ
 temp1 = terrain[iX][iZ]  *(1.0-fX) + terrain[iX+1][iZ]  *fX
 temp2 = terrain[iX][iZ+1]*(1.0-fX) + terrain[iX+1][iZ+1]*fX
 return temp1*(1.0-fZ) + temp2*fZ

# Manage scene, main loop
def scene():
 glClear(GL_DEPTH_BUFFER_BIT | GL_COLOR_BUFFER_BIT)
 glLoadIdentity()
 glRotatef(camXA   , 1, 0, 0)
 glRotatef(camYA+90, 0, 1, 0)
 glTranslatef(-camX,-doCheck()-2,-camZ)
 glCallList(1)
 glutSwapBuffers()
 Event()

# Manage key events
def Event():
 global camX, camZ, camYA, camXA
 if KEY_UP:
  camX += cos(camYA*0.0174) * .075
  camZ += sin(camYA*0.0174) * .075
 if KEY_DOWN:
  camX -= cos(camYA*0.0174) * .075
  camZ -= sin(camYA*0.0174) * .075
 if KEY_LEFT:
  camYA -= 1.0
 if KEY_RIGHT:
  camYA += 1.0
 if KEY_PUP:
  camXA -= 1.0
 if KEY_PDOWN:
  camXA += 1.0

# Toggle key booleans
def flipKey(key, state):
 global KEY_UP, KEY_DOWN
 global KEY_LEFT, KEY_RIGHT
 global KEY_PUP, KEY_PDOWN
 if key == GLUT_KEY_UP:
  KEY_UP = state
 elif key == GLUT_KEY_DOWN:
  KEY_DOWN = state
 elif key == GLUT_KEY_LEFT:
  KEY_LEFT = state
 elif key == GLUT_KEY_RIGHT:
  KEY_RIGHT = state
 elif key == GLUT_KEY_PAGE_UP:
  KEY_PUP = state
 elif key == GLUT_KEY_PAGE_DOWN:
  KEY_PDOWN = state

# Call key state toggle function
def KeyDown(key, x, y):
 flipKey(key, 1)
def KeyUp(key, x, y):
 flipKey(key, 0)

# Init everything
def main():
 glutInit(sys.argv)
 glutInitDisplayMode(GLUT_RGB | GLUT_DOUBLE | GLUT_DEPTH)
 glutInitWindowSize(640, 480)
 glutCreateWindow("Python & OpenGL Demo")
 glutSetKeyRepeat(GLUT_KEY_REPEAT_ON)
 glEnable(GL_DEPTH_TEST)
 glViewport(0, 0, 640, 480)
 glMatrixMode(GL_PROJECTION)
 glLoadIdentity()
 gluPerspective(45.0, 1.33, 0.1, 100.0)
 glMatrixMode(GL_MODELVIEW)
 glEnable(GL_CULL_FACE)
 glEnable(GL_FOG)
 glFogi(GL_FOG_MODE, GL_EXP)
 glFogf(GL_FOG_DENSITY, .07)
 glFogfv(GL_FOG_COLOR, [0, 0, 0, 0])
 glutSpecialUpFunc(KeyUp)
 glutSpecialFunc(KeyDown)
 glutDisplayFunc(scene)
 glutIdleFunc(scene)
 buildTerrain(70, 70)
 glutMainLoop()
main()

```

EDIT: Requires pyOpenGL and GLUT btw.

---

### Post by engla on 2006-12-11
I have to say this is very instructive. I wrote some old OpenGL code some years ago (that plotted parameterized surfaces) in Obj-C that I've been looking to port. Porting it to python should be fine. So thanks!

---

### Post by pmasiar on 2006-12-11
> **hod139 said:**
> As long as python is interpreted it simply cannot be as fast as a compiled language.

This is common misunderstanding. Strictly speaking, Python is compiled on the fly into bytecode, and bytecode is "interpreted" - same approach as java. But for some reason java is not considered "interpreted" language, because you have manual step of compiling. Python also compiles for you, creates bytecode (.pyc) and you can distribute .pyc files instead of .py sources.

Bytecode is optimized to be run fast.

Let me compare with java. Java is improved simplified C++ with better memory management. Java is popular for a reason - it was big improvement over C++.

Comparing with java, difference is *not* the compilation (both java and python compile bytecode for virtual machine), but python's [dynamic (duck) typing]("http://en.wikipedia.org/wiki/Duck_typing"): variable can change type, and it is OK as long as type has all the methods code wants to use. It means that first time method is used, it needs to be found in the class tree (and is promptly cached for speed). Java also needs to search class tree for type methods, same as python, just less convenient. :-) Python is more flexible, it also has multiple inheritance and operator overloading (which java lacks). 

Overloading is very important for Object Oriented languages. It adds readability, you can design your own types which look like system types (you can use + - * etc on them, iterator and stuff). With java, there is big difference: system can have String class with + overloaded, but you cannot do that, and have to define methods with long string names. C++ has overloading (and it was removed in java because it was confusing cause for errors).

Another big difference is exception handling. Java (and C++ too, I believe) has static. It means, if you add to your code new library call, which throws different exception, you need to handle it right away. If you want to handle errors 2 layers up, you need to edit all layers of procedure calls in between. Nightmare in big projects. I was told standard practice is to catch the exception and recast it in wrapper as single type of custom exception. Python does not force you anything. Errors just transparently bubble up until someone deals with them - or program crashes with error trace if not handled properly. For quick and dirty code, it is all you need - you can add error handling afterwards, when algorithms and datatypes are stabilized.

> is it so much faster to develop in python than in other languages?   

Both novice programmers and experts are more productive. :-) Novice programmers are able to write code with very little experience. Python does *not* force everything to be object like java - you can perfectly fine write old-fashioned procedural code, sharing modules, using existing objects as needed, but never defining custom classes. In Java or C++ they would be still struggling with class hierarchy and collecting data into proper collections, and then recasting them back to proper type. In java, Int and int are slightly different integer-like types, are initialized into different values, and other differences. Experts can create sophisticated code using method decorators and object introspection (when object looks on the fly what type/methods it has, and modifies behavior accordingly). According to experts, it allows to avoid writing pages and pages of boilerplate code  (I didn't tried it yet).

Python is first language **designed and optimized for easy reading and understanding by humans**. And it shows, and it succeeded. :-)

---

### Post by hod139 on 2006-12-11
> **pmasiar said:**
> This is common misunderstanding. Strictly speaking, Python is compiled on the fly into bytecode, and bytecode is "interpreted" - same approach as java. But for some reason java is not considered "interpreted" language, because you have manual step of compiling. Python also compiles for you, creates bytecode (.pyc) and you can distribute .pyc files instead of .py sources.

Didn't know that thanks.  The rest of your post was also very informative, thanks again.

---

### Post by pmasiar on 2006-12-11
> **neoflight said:**
> 
what will the  customers/users look for:

1. that took less time to make..... OR
2. that executes really fast...


Ask your customer: if she is willing to wait half a second for program to run, she will get it 6 months earlier. :-)

There is so much more involved in running a program before and after of execution which is the same for both C++ and python program. And python program after first use is compiled into bytecode and saved, no compilation needed anymore.


> 50% faster execution is worth spending 50% more time developing.

If it is something like Linux kernel, possibly. But you may not gain 50% speed over python: optimizing compilers are really smart now - it is 40 years old technology. 20% increase may mean saving 0.2 - 0.5 sec off, hard to notice. Buy faster processor.

Actually, by the time you will finish your C++ application, processors will be 20% faster for same price... :-) And my python program was making money all that time, and I made yet another program, and added 2 new features (which your C++ program is missing) after users changed specifications after months of using my python program. :-)

---

### Post by neoflight on 2006-12-12
> **pmasiar said:**
> There is so much more involved in running a program before and after of execution which is the same for both C++ and python program. 


would you please explain that in detail? 

i was mentioning about the speed of execution. I guess now a days people use python as a glue language for big projects...

in my case i am trying to get my research done using fortran, coz it involves lots of math. my plan for GUI is with python. 
I tried using python and numpy and its slow...even compared with matlab....i confess that i didn't test python+numpy that extensively. i completely agree that getting something done in C++ is time consuming....very time consuming....

if the compilers for C++ OR fortran such as intel, g**, etc is smart,  why dont they just recognize the variable as integer, float, double or whatever without user declaration- when its compiling? just look at the other side of the assignment and check if its a float or integer (atleast) and assign appropriate memory for it....whats the big deal? it **can** do coercion !!! i dont understand....:-k

---

### Post by pmasiar on 2006-12-12
> There is so much more involved in running a program before and after of execution which is the same for both C++ and python program.

Well I am in no way kernel hacker, but my naive understanding is:

[LIST]
[*]process needs be started, memory and other resources (input/output files) allocated
[*]shell needs to find file name and load it into memory
[*]shared libraries needs be detected, if any, and page mapping magic needs to happen
[*]Now program is ready to run, and it runs (here you get 20% speed increase from being C++)
[*]program finished, resources to be freed
[/LIST]

If your program is relatively simple and not running for long (minutes), substantial part of running time might be system overhead. Even if it runs for a minute, is it a problem for the user? Or if not running your code, it will be doing nothing else? 

If waiting for full results takes too long, can you output partial results, quickly, so user has something to look at while you process rest?

> I guess now a days people use python as a glue language for big projects...

Indeed. I was impressed on PyCon2005 when I heard about "glue python code which will deploy new compiled C query code on 1% of Google servers on test base". Google has about 200K servers or so in couple of server farms, so deploying on 1% means putting your code on at least couple hundreds of servers - with one command. I was humbled. :-)

> in my case i am trying to get my research done using fortran, coz it involves lots of math.  

If even fortran is not fast enough, try (using python) split your input data and run parts of computations in paralel on couple machines, then (again with python) merge resulting data. Does it make sense?

---

### Post by neoflight on 2006-12-12
> **pmasiar said:**
> If even fortran is not fast enough, try (using python) split your input data and run parts of computations in paralel on couple machines, then (again with python) merge resulting data. Does it make sense?

interesting suggestion. never thought of that... i have yet to implement UI part to my code. still working to tweak fortran output. 

Initially started with C++ but decided not to go with it. then took up fortran_python idea... profs do not care at all and they cant give time simply because of the development time... will try it out...Computational fluid dyn guys here use fortran extensively and  some of them, i was told, use tcl-tk interfacing rather than python. but some suggested me to go with python...

thanks

---

### Post by winch on 2006-12-12
> **pmasiar said:**
> This is common misunderstanding. Strictly speaking, Python is compiled on the fly into bytecode, and bytecode is "interpreted" - same approach as java. But for some reason java is not considered "interpreted" language, because you have manual step of compiling. Python also compiles for you, creates bytecode (.pyc) and you can distribute .pyc files instead of .py sources.

Python does not use the same approach as java. Java bytecode is translated into machine code before it is run. The bytecode is not interpreted as with python.
See [http://en.wikipedia.org/wiki/Just-in-time_compilation](http://en.wikipedia.org/wiki/Just-in-time_compilation)

---

### Post by pmasiar on 2006-12-12
> **winch said:**
> Python does not use the same approach as java. Java bytecode is translated into machine code before it is run. The bytecode is not interpreted as with python.
See [http://en.wikipedia.org/wiki/Just-in-time_compilation](http://en.wikipedia.org/wiki/Just-in-time_compilation)

I stay corrected. So java code is faster because is compiled twice, while python only once? Well, python also can compile bytecode to binary code if you desire so. You are free to compile it with tools like [psyco]("http://www.python.org/pypi/psyco/1.2") - but only if you need it.

Bottom line is, speed is not a problem until it is a problem.

---

### Post by cgrebeld on 2006-12-12
Of course besides raw speed, in C++ you also have the advantage of compile time type checking, which proves that at least some aspects of your program are correct, which reduces the number of unit tests you have to write.. this might be a big problem for a large python project.

---

### Post by pmasiar on 2006-12-12
> **cgrebeld said:**
> Of course besides raw speed, in C++ you also have the advantage of compile time type checking, which proves that at least some aspects of your program are correct, which reduces the number of unit tests you have to write.. this might be a big problem for a large python project.

Opposite approach is possible in python: to get started with unit testing, write tests for your  types first, those are the easy ones. :-)  After your types are checked, you have agility of python and big part of type safety of C++, right? So basically you trade 30% penalty in execution speed for 1000% bonus with speed-to market and flexibility. Not bad, right?

---

### Post by Wybiral on 2006-12-12
In my opinion, they are nearly equal separate languages. I use them both almost daily. But when you combine them... Whole different story. You get the optimized, precompiled power of C++, but you can use the beautiful, elegant syntax of python to orchestrate the program by calling your C++ functions.

---

### Post by Eric_T on 2006-12-15
> **neoflight said:**
> interesting suggestion. never thought of that... i have yet to implement UI part to my code. still working to tweak fortran output. 

Initially started with C++ but decided not to go with it. then took up fortran_python idea... profs do not care at all and they cant give time simply because of the development time... will try it out...Computational fluid dyn guys here use fortran extensively and  some of them, i was told, use tcl-tk interfacing rather than python. but some suggested me to go with python...

thanks

Regarding parallel programming, it's fairly complicated, so unless you're dealing with "industrial size" grids(typically around a million cells or more), it's not really necessary.

Regarding development time, for smaller CFD applications, I find that using Python doesn't give you that much of an advantage. FORTRAN was built for that purpose, translating math into a computer program, so it's not that hard to develop in. It's mainly just reading boundary conditions, initial fields etc, setting up the equation system, solve it and then output the data to a text file. 
For fast prototyping of discretization methods or other algorithms, Matlab is excellent because of the extensive built in libraries for mathematics and plotting

Python is great for programming the GUI, but are you sure you even need a GUI? I often find using just a fortran namelist file sufficient for input data, and use something like Matlab or Tecplot to visualize the output data.

---

### Post by slavik on 2006-12-15
> **pmasiar said:**
> I'll bite. Of course raw speed is better in C++. I agree 100%. Let me play the devil's advocate (or the angel's, or the python's :-) ): why you could *still* be better off using "slower" python?

[LIST=1]
[*]**Speed-to-market** might be more important than processing speed. If you are in the startup, having your killer app out on the market 3 months ahead of the competition, and being able match features of your competitors within a week, might be more important. If your application scales well, as you gain users you can dump more cheap servers to run it. Thats what Google does. Google also employs many top-level Python hackers, including [Guido]("http://en.wikipedia.org/wiki/Guido_van_Rossum") and [Alex Martelli]("http://en.wikipedia.org/wiki/Alex_Martelli").

[*]Save speed by **implementing efficent design**, not by optimizing loops and function calls. Agile language like python allows you to try multiple approaches, refactor quickly, and still have functioning code. 

[*]**Find bottlenecks and optimize only those** - maybe even reimplement them in C. You may find out that 90% of the time is spent in 5% of the code. If python allows you to develop code 10 times faster, it would be waste of time to implement 95% of non-critical code in C/C++, and premature optimization. [Speed is not a problem until it is a problem]("http://en.wikipedia.org/wiki/Python_%28programming_language%29#Eschew_premature_optimization"). And we know that premature optimization is root of all evil.
[*]**use [NumPy module]("http://en.wikipedia.org/wiki/Numpy")** for fast calculations on big matrices, implemented in C (runs with speed of C).
[*]Maintenance cost and cost of adding new functions. I read recently that with operating environment changing quickly, companies might need to change internal process every 2 years. Having flexible IT infrastucture allowing that is crucial.
[/LIST]

I actually like C. I coded in assembler before and with C, I really love the feeling what it generates efficient binary for me. It is doing what I would do  in assembler. But in python I am just so much more productive... :-)

I am a gov't looking for software to run air traffic towers ...

PS: They all use Ada.

---

### Post by Wybiral on 2006-12-15
Oh... I have a good point to bring up about C++ vs Python... Globals and constants!!! Python just doesn't allow either... Sure you can do stuff like accept a global in every function, but when you are dealing with a lot of them, this gets VERY time consuming to write, thus negating pythons ability to develop quickly in! And sometimes you just need globals and constants, with python you are stuck having to either add a global definition to every function that uses them (which can be a lot of extra code) or you can pass them as parameters (even more extra code).

This is exactly why I have remained neutral in this discussion, I like them both. They each have week points and strong points, neither is "superior"

---

### Post by Eric_T on 2006-12-15
> **Wybiral said:**
> Oh... I have a good point to bring up about C++ vs Python... Globals and constants!!! Python just doesn't allow either... Sure you can do stuff like accept a global in every function, but when you are dealing with a lot of them, this gets VERY time consuming to write, thus negating pythons ability to develop quickly in! And sometimes you just need globals and constants, with python you are stuck having to either add a global definition to every function that uses them (which can be a lot of extra code) or you can pass them as parameters (even more extra code).

This is exactly why I have remained neutral in this discussion, I like them both. They each have week points and strong points, neither is "superior"

I think most people would consider that a strength. Having a lot of global variables can really mess up a large program, and by removing them, Python forces you to create a better design for your program.

---

### Post by Wybiral on 2006-12-15
If you want to call it "better" but sometimes you just flat out need them. For instance... I often write graphical stuff in python, games and demos, and I deal with an awful lot of key booleans. This means that I have a lot of key variables that need passed to other parts of the program, AND, they need to retain their value between multiple functions.

I could use a list and then only have to pass one object from function to function, but then I am left with a very cryptic key setup because I'm not going to remember the number for each key. So, in cases like the terrain walk demo I posted... I need to maintain the terrain list, all of the key booleans, and the camera attributes (x, z, xangle, yangle)...

Then, when you have more data that can't be forgotten and you can't afford to pass it down a large number of function calls through parameters... You can see how this becomes a problem. Especially when speed is of the essence (such is the case of 3d games). So, pythons inability to create global and constant object's may be helpful in some situations, it's downright disgusting in others (and that example was just the tip of the ice burg, games will often require much larger and more numerous amounts of data to remain throughout function calls).

---

### Post by pmasiar on 2006-12-15
> **Wybiral said:**
> Oh... I have a good point to bring up about C++ vs Python... Globals and constants!!! Python just doesn't allow either... 

LOL. Neither is true. Each one is *so* easy to implement it is not even part of the language.

**Constants** f-- as ound in [ASPN cookbook]("http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/65207"):
```
# Put in const.py...:
class _const:
    class ConstError(TypeError): pass
    def __setattr__(self,name,value):
        if self.__dict__.has_key(name):
            raise self.ConstError, "Can't rebind const(%s)"%name
        self.__dict__[name]=value
import sys
sys.modules[__name__]=_const()
```

that's all -- now any client-code can bind an attribute ONCE, but  but NOT rebind it second time: ```
import const
const.magic = 23      # binds first time - OK
const.magic = 88      # raises const.ConstError
# you may also want to add the obvious __delattr__
```

**Globals**: 

You can have (file-scoped) package globals (using keyword 'global'), or create a module say shared.py, and put all variables you vant to share there, and access them like shared.variable1 (after you 'import shared' )

The only difference is that descriptive part 'const.' or 'shared.' will be part of the variable name. I believe that is good, especially in big projects: My experience suggests me that  having descriptive name helps a lot. When first faced with such a strict naming convention, I was outraged. Five years and couple of MB of source code later in the project, I was convert :-). YMMV.

---

### Post by Wybiral on 2006-12-15
> 
# Put in const.py...:
class _const:
    class ConstError(TypeError): pass
    def __setattr__(self,name,value):
        if self.__dict__.has_key(name):
            raise self.ConstError, "Can't rebind const(%s)"%name
        self.__dict__[name]=value
import sys
sys.modules[__name__]=_const()


I've seen this technique before... But, you're telling me I have to do all of that just for constant when in C++ I can say:
```

const int magic = 23

```
So, that is one area that would take longer to develop in python than c++... And it's really a work around and not one of pythons abilities.

And I have to create an entire module just for globals... 

The two way's you showed do *sort of* accomplish the task... But they are work arounds and they still require more work than in C++. So, in short... Python doesn't support globals or constants.

And yeah, I've worked on large projects myself, I'm working on one right now in C++. But you can create your own naming convention without being forced to.

I still like python, but I am saying... There ARE plenty of areas where C++ wins over python. (There are also plenty of areas where python wins)

---

### Post by po0f on 2006-12-15
Why is this thread still alive?

What's the point of comparing language X to language Y?  They are different languages, with different goals in mind.  People will use them if they're good (and sometimes if they're not).

Programmers will use whatever language they are most comfortable with, regardless if it's the "best language for the job", which, IMO, is subjective anyway.

Final thought: these threads, though well-intentioned, turn into language flame wars.  Please let the thread die in peace.  Thank you.

---

### Post by Wybiral on 2006-12-15
You're right... (although I personally don't seen anything wrong with a friendly dispute about our languages of choice)

I've been saying it from the beginning neither is *BETTER* but the point of this thread was to show a visual example of the difference in speed between C++ and python... Not through arguing, but I posted two identical programs.

Then the point came up that python was faster to develop in.. And in a lot of cases I agree, but not when it comes to 3d games. You can make small ones quicker in python, but due to some of pythons restrictions, larger 3d games are faster and easier to develop in C++.

But, I remain neutral, I use them both and I see a need to use them both.

For me, there's C++, python, and javascript.

Sure, I know other languages, but I need nothing more than those languages to accomplish what I want to. If I had a server, I might learn some PHP (which I hear is really easy) and when I am bored I write assembly programs (which is an incredible waste of time).

But for almost everything... C++, python, and javascript! And I need all three of them.

---

### Post by Klipt on 2006-12-15
> **Wybiral said:**
> I still like python, but I am saying... There ARE plenty of areas where C++ wins over python. (There are also plenty of areas where python wins)

What about the STL? Ok, so duck typing means it doesn't need templates. And it already has sorting routines and hash tables. But does it have (dun dun dun) red-black trees and heaps built in? :p (You can [download them](http://newcenturycomputers.net/projects/rbtree.html), of course...)

---

### Post by Wybiral on 2006-12-15
I think they are powerful enough to say that each of them can theoretically make anything the other can. But another point is... Python was written in C. And most of it's modules... In C. So there is really nothing python can do that C can't.

---

### Post by pmasiar on 2006-12-16
> **Wybiral said:**
> I think they are powerful enough to say that each of them can theoretically make anything the other can. But another point is... Python was written in C. And most of it's modules... In C. So there is really nothing python can do that C can't.

Both languages are Turing-complete - but it does not buy you much. Do you know about PyPy project - Python written in a (subset of) Python? And why EU decided to support that: because python is an agile language, you can try different implementations, and refactor much easier than in C. But you already knew that. :-)

---

### Post by Wybiral on 2006-12-16
It's really a matter of opinion. I think C++ is just as easy as python. And my dev time in python is only slightly shorter than in C++ (except when it comes to large projects, in that case C++ usually wins).

BTW, C and C++ compilers have been written on C and C++ too. I've seen C compilers written in BASIC. In fact, you could write a C++ compiler in python if you wanted to. The difference is that python is not "compiled" to machine code. So, it will always have to run off of another program's to interpret it. Bytecode is not executable, it has to be interpreted by a program (which was written in C).

I believe the PyPy project is still going to run off of a virtual machine, and considering the nature of interpreted and VM'd program... I just can't see it being faster than C++. I'm actually working on a project right now that has a virtual machine and a "compiler" that translates the source code to VM opcode, which is essentially similar to bytecode. The bytecode get's fed into the virtual machine where it is kindof like an emulated assembler. But, the fact that it's emulated TO the real processor instead of being compiled to processor machine code means that it just will not be as fast.

Thats all a compiler does. And pythons dynamicness comes from it's virtual machine style interpreting. It is able to handle all of the memory management itself. So, unless it's opcodes get toppled onto a lightning-fast virtual machine to act as an executable... Or someone finds a way to manage the memory so that it CAN be compiled to machinecode... It's still going to be an interpreted language.

Python may allow for more agility than C, but I wouldn't say much, if any, more than C++. Python is much more similar to C++ than C (while it isn't really that similar at all). But, it's true... C++ is more agile than C too since it's basically an object oriented C.

C is a pretty low level language, while python and C++ are often very high up there. They are equal in terms of usefulness, but C++ does compile to MACHINE code.

---

### Post by neoflight on 2006-12-19
how about plotting capability in both? which is better off with using gnuplot?

---

### Post by Wybiral on 2006-12-19
Probably python because c++ might be overkill to interface with something like that. I've never used it though, so I can't say for sure, I'm just going by what I've seen from stumbling across it. Python is very easy to interface with small interactive libraries like that, in my opinion.

EDIT:

I do all of my plotting and graphics, be-it 2d or 3d, in OpenGL which is compatible with both C++ and Python.

---

### Post by Jessehk on 2006-12-19
I program as a hobby. While I do know C++ (better then most hobbyists, but not fully), I prefer C for lower level stuff.

My favourite languages at this point are C, python, and I'm deciding between Haskell or O'Caml.

---

### Post by uglycoyote on 2012-12-09
> btw, this program may be pretty CPU intensive, I creates 10000 particles and then displays them in a loop. You may adjust the number 10000 in each of them to try different speeds. (less=faster, more=slower)

I think that's the key here.  If you have an application where the GPU is doing most of the heavy lifting, you can get away with using a higher-level language for doing the CPU-side stuff.  

I work at a game company and I develop a 3D world editor application in C#.  The difference in speed between C++ and C# is not really a factor because game worlds tend to be made up of a small number of highly detailed models.   So on the C# side, it's just a small number of calls "draw this model at this location".  In games, often the number of "draw calls" is the limiting factor, so you keep those low by drawing large pieces of static geometry as a single element (this requires that the entire model use the same texture, as changing textures requires a separate draw call)

I think the same logic would apply to the Python vs C++ comparison;  if you have a small number of very complex display lists in OpenGL, the difference in performance between using Python vs C++ will not be much of a factor.  On the other hand, if every frame you are completely recomputing a new geometry using glVertex calls, C++ will win out.

---

### Post by The Cog on 2012-12-09
That conversation finished 6 years ago.
Thread closed.

---

