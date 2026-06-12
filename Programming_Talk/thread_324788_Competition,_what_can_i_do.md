---
title: "Competition, what can i do ?"
date: 2006-12-24
forum: Programming Talk
---

### Post by originof on 2006-12-24
I[HTML][/HTML]'m participating to a competition (in italy) , where is demanded to create a useful program for the schools, or for the public administration… What I can make? 


sorry, for my english ](*,)

---

### Post by Wybiral on 2006-12-24
I'm not sure what kind of competition it is or how good the programs have to be... But maybe a graphing calculator program? Good graphing calculators are so expensive (almost 100$ over here) and they have terrible resolution and limited colors. A sophisticated graphing calculator program would be very useful for students.

Something that can great a 2d graph of a function, maybe even a 3d graph (OpenGL would come in hand there)

Anyway, just a suggestion.

---

### Post by originof on 2006-12-24
I have 3 months for finish it...however, from the administrative point of view, what can i do ?

---

### Post by Tomosaur on 2006-12-24
Surely the competition is based on individual talent and ability to identify a problem and provide a solution?

---

### Post by originof on 2006-12-24
> **Tomosaur said:**
> Surely the competition is based on individual talent and ability to identify a problem and provide a solution?



yes, the competition is called ' Today i programming ' and can partecipate only guy from 18 to  24 years old...
I can make a program from 0, or modify an open source program that already exist..

---

### Post by Tomosaur on 2006-12-24
I was suggesting that you need to figure out what to create for yourself, unless of course, you want to share the prize with us?

---

### Post by originof on 2006-12-24
> **Tomosaur said:**
> I was suggesting that you need to figure out what to create for yourself, unless of course, you want to share the prize with us?



but i need some suggestionsa bout what can i create....

---

### Post by sailingboarder on 2006-12-24
think about a program u wished u had in school, maybe somehting that would have made a class easier, and make that

---

### Post by M7S on 2006-12-24
Another vote for a 3d graph calculator! (kplot is good enough for me when it comes to 2d graph calculators)

---

### Post by gummibaerchen on 2006-12-24
Yeah, calculators are really smart :)

3D would be very nice.

Qalculator is good for solving equations, but maybe you can extend this for example.

**Wybiral** sounded, as if he would like an alternative for graphical calculators.
This could be pretty hard, but would be also pretty nice :)
(If it would work with the "normal" Data-Loggers or so)
Then you should think about, which devices should run that.
Some calculator of that kind might fit very nice on the Nokia 770 as it has an USB-Port I think.

---

### Post by originof on 2006-12-25
I use python and gtk, because they can run on linux and on winsuck...
But there's some other language that i can use ??


thanks to all, and happy christmas to all

---

### Post by maddog39 on 2006-12-26
C++ is probably really good for all this kind of stuff, especially math related calculations, simply because its a compiled language and therefore optimized for the CPU/architecture when compiled. :)

---

### Post by Wybiral on 2006-12-27
This requires my viper module, and uses pythons exec command, but if it were written in pure python + opengl, or pure C++ and opengl, and had it's own expression parser instead of cheating with pythons... This is an example of what it could do (but preferably more function)...

```

#!/usr/bin/env python

from math import *
from viper import *
from OpenGL.GL import *

def buildGraph():
	XZFunction = raw_input("f(x, z) = ")
	XZFunction = "y=" + XZFunction + "\n"
	print XZFunction
	vInit3d("test", 640, 480)
	glNewList(1, GL_COMPILE)
	glBegin(GL_POINTS)
	for a in range(100):
		for b in range(100):
			x = float(a)
			z = float(b)
			exec(XZFunction)
			glVertex3f(x-50, y, z-50)
	glEnd()
	glEndList()
	renderGraph()

def renderGraph():
	angle = 0.0
	while not(vKeyDown(SDLK_ESCAPE)):
		vProcessEvents()
		glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT)
		glLoadIdentity()
		glTranslatef(0,0,-20)
		glRotatef(angle, 1, 0, 0)
		glRotatef(angle, 1, 1, 0)
		glScalef(.1, .1, .1)
		glCallList(1)
		vSwapBuffers()
		angle+=.25

buildGraph()

```

Just grab my python module, viper (it in my signature, just grab the 2.4 binary package and put the .so in the same folder as the code above^) and try it out... Here are some example functions...

Ripply water: cos(cos(x/10)*10 + cos(z/10)*10)
3d Fractal: (int(x) & int(z)) / 5
Weird pattern: tan(x/10) * tan(z/10) + tan(x+z)
Just waves: cos(x/10)*10 + cos(z/10)*10
Smooth hill:  ((x-50)/10)**2 + ((z-50)/10)**2

Anyway, as I was saying... A good 3d graphing calculator would rock. Perhaps even height color mapping and stuff. There's all kinds of cool features you could add.

---

### Post by pmasiar on 2006-12-27
> **originof said:**
> I[HTML][/HTML]'m participating to a competition ... to create a useful program for the schools, or for the public administration… 

I can make a program from 0, or modify an open source program that already exist.


> **Tomosaur said:**
> Surely the competition is based on individual talent and ability to identify a problem and provide a solution?

Tomosaur is 100% right. You should not ask random people in programming forum what you should do: there are many forums with people who know about school problems. Edubuntu or "Education & Science" forum might be good start. For sure there are Italian-specific forums. 

Or even better, find a school user (teacher or administrator), ask him how you can help him to solve some of his problems, and do it. You need someone willing to work with you through crashing alpha and beta versions to stable code - let them know ahead that code will not be perfect. If you start new project, learn about  [Paper prototyping]("http://en.wikipedia.org/wiki/Paper_prototyping") to get faster to usable design. But everything worth programming was done before: try to find existing project which has 90% of needed functions and add the rest.

---

### Post by originof on 2006-12-28
i've already asked to my teachers... :)

---

