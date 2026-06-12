---
title: "3D Python Example (vectors, quaternions, model loading, etc.)"
date: 2009-01-11
forum: Programming Talk
---

### Post by curvedinfinity on 2009-01-11
Hey all,
I was experimenting with Python over the last week, and I made this example app for various 3D stuff. I titled it PolarisGP, and I was making it with lax intentions of making a flight racing game. However, in case I lose interest, I'd like to put it out there for posterity.

It includes some examples of pretty cool techniques:
[LIST]
[*]Basic linear algebra
[*]Quaternion rotation
[*]Axis/magnitude angular velocity
[*]Display lists
[*].obj file loading
[*]Efficiently extracting "up,left,forward" vectors from a matrix
[*]Using an inverse matrix (in this case, from a quaternion) to create a camera system
[/LIST]

Perhaps people can dig up some other useful techniques too...

A description of what this app does: In third-person, you fly your spaceship around a cloud of 1728 (12 to the third power) other spaceships. Controls are WADSQE for rotation and IJKLUM for thrust.

It requires python-opengl

Pics:
[IMG]http://i39.tinypic.com/258cr9u.png[/IMG]
[IMG]http://i40.tinypic.com/fdfvxc.png[/IMG]

main.py - the main application. To run, call "python main.py"
```

#!/usr/bin/python

from OpenGL.GL import *
from OpenGL.GLU import *
from OpenGL.GLUT import *

from Drawable import *
from Actor import *

import time

print "== Controls ===================="
print "Heading: w,a,d,s,q,e"
print "Thrust: i,j,l,k,u,m"
print "================================"

window = 0
screenSize = [640,480]

previousTime = time.time()

frameCounter = 0
frameCounterTimer = time.time()

def display():
	global previousTime,frameCounter,frameCounterTimer,envlist
	
	currentTime = time.time()
	deltaTime = (currentTime-previousTime)
	glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT)
	glPushMatrix()
	glMultMatrixf(toMatrixQ(inverseQ(actor.drawable.rotation)))
	camera = inverse3(actor.drawable.position)
	camera = add3(camera,scale3(actor.drawable.forward,-3))
	camera = add3(camera,scale3(actor.drawable.up,-0.6))
	glTranslatef(camera[0],camera[1],camera[2])
	glLightfv(GL_LIGHT0, GL_POSITION,[-2.0, 3.0, 3.0, 0.0])
	glCallList(envlist)
	#for flora in scenery:
	#	flora.draw()
	actor.update(deltaTime)
	glPopMatrix()
	glutSwapBuffers()
	previousTime = currentTime
	
	frameCounter += 1
	if currentTime-frameCounterTimer > 1:
		print "FPS:",frameCounter
		frameCounter = 0
		frameCounterTimer = currentTime

def resize(width, height):
	if(height==0): height = 1
	screenSize = [width, height]
	glViewport(0, 0, width, height)
	glMatrixMode(GL_PROJECTION)
	glLoadIdentity()
	gluPerspective(90.0, float(width)/float(height), 0.1, 1000.0)
	glMatrixMode(GL_MODELVIEW)

def key(*args):
	if args[0] == 's': # rotation
		actor.spin(1.5,actor.drawable.left)
	elif args[0] == 'w':
		actor.spin(-1.5,actor.drawable.left)
	elif args[0] == 'a':
		actor.spin(2.5,actor.drawable.forward)
	elif args[0] == 'd':
		actor.spin(-2.5,actor.drawable.forward)
	elif args[0] == 'e':
		actor.spin(1.5,actor.drawable.up)
	elif args[0] == 'q': 
		actor.spin(-1.5,actor.drawable.up)
	elif args[0] == 'k': # movement
		actor.push(scale3(actor.drawable.forward,10.0))
	elif args[0] == 'i':
		actor.push(scale3(actor.drawable.forward,-10.0))
	elif args[0] == 'l':
		actor.push(scale3(actor.drawable.left,3.0))
	elif args[0] == 'j':
		actor.push(scale3(actor.drawable.left,-3.0))
	elif args[0] == 'u':
		actor.push(scale3(actor.drawable.up,3.0))
	elif args[0] == 'm':
		actor.push(scale3(actor.drawable.up,-3.0))
	elif args[0] == '\033': #escape
		glutDestroyWindow(window)
		sys.exit()

glutInit('')
glutInitDisplayMode(GLUT_DOUBLE | GLUT_RGBA | GLUT_DEPTH)
glutInitWindowSize(640,480)
window = glutCreateWindow('PolarisGP')
resize(640,480)
glutDisplayFunc(display)
glutIdleFunc(display)
glutReshapeFunc(resize)
glutIgnoreKeyRepeat(1)
glutKeyboardFunc(key)

glClearColor(1,1,1,1)
glClearDepth(1)

glEnable(GL_LIGHTING)
glEnable(GL_LIGHT0)
glLightfv(GL_LIGHT0, GL_AMBIENT,[0.2, 0.1, 0.1, 1.0])
glLightfv(GL_LIGHT0, GL_DIFFUSE,[1.0, 1.0, 1.0, 1.0])
glLightModelfv(GL_LIGHT_MODEL_AMBIENT,[0.2, 0.2, 0.2, 1.0])

glEnable(GL_DEPTH_TEST)
glDepthFunc(GL_LESS)

glShadeModel(GL_FLAT)

glCullFace(GL_BACK);
glEnable(GL_CULL_FACE);

actor = Actor()

b = -6
r = 12

scenery = []
for x in range(b,b+r):
	for y in range(b,b+r):
		for z in range(b,b+r):
			flora = Drawable()
			flora.position = (x*20,y*20,z*20)
			scenery.append(flora)

envlist = glGenLists(1)
glNewList(envlist,GL_COMPILE)
for flora in scenery:
		flora.draw()
glEndList()

glutMainLoop()

```

Actor.py - This represents a 3D object with some simple newtonian physics
```

from math3D import *
from Drawable import *

class Actor:
	drawable = None
	velocity = (0,0,0)
	rvAxis = (1,0,0)
	rvMagnitude = 0
	friction = 3
	rFriction = 3
	
	def __init__(self):
		self.drawable = Drawable()
	
	def push(self,v):
		self.velocity = add3(self.velocity,v)
	
	def spin(self,mag,axis):
		newRV = add3(scale3(self.rvAxis,self.rvMagnitude),scale3(axis,mag))
		self.rvMagnitude = length3(newRV)
		self.rvAxis = normalize3(newRV)
	
	def update(self,t):
		self.drawable.draw()
		self.drawable.move(scale3(self.velocity,t))
		if lengthSq3(self.rvAxis)==0:
			self.rvAxis = (1,0,0)
		rvInstant = fromAngleAxisQ(self.rvMagnitude*t,self.rvAxis[0],self.rvAxis[1],self.rvAxis[2])
		self.drawable.rotate(rvInstant)
		self.velocity = scale3(self.velocity,1.0-t*self.friction)
		self.rvMagnitude = self.rvMagnitude*(1.0-t*self.rFriction)

```

Drawable.py - this represents a 3D object with position and rotation properties
```

from OpenGL.GL import *
from Model import *

class Drawable:
	position = (0,0,-3)
	rotation = zeroQ()
	matrix = (1,0,0,0,0,1,0,0,0,0,1,0,0,0,0,1)
	forward = (0,0,1)
	up = (0,1,0)
	left = (1,0,0)
	color = (0.5,0.4,1,1)
	model = None
	changed = True
	
	def __init__(self):
		self.model = Model("LMP1.obj")
	
	def move(self,v):
		self.position = add3(self.position,v)
	
	def rotate(self,q):
		self.rotation = multiplyQ(self.rotation,q)
		self.changed = True
	
	def draw(self):
		glPushMatrix()
		glTranslatef(self.position[0],self.position[1],self.position[2])
		if self.changed:
			self.matrix = toMatrixQ(self.rotation)
			self.left = (self.matrix[0],self.matrix[1],self.matrix[2])
			self.up = (self.matrix[4],self.matrix[5],self.matrix[6])
			self.forward = (self.matrix[8],self.matrix[9],self.matrix[10])
			self.changed = False
		glMultMatrixf(self.matrix)
		glMaterialfv(GL_FRONT, GL_AMBIENT,[0.2,0.2,0.2,0])
		glMaterialfv(GL_FRONT, GL_DIFFUSE,self.color)
		glMaterialfv(GL_FRONT, GL_SPECULAR,[0.7,0.7,0.7,0])
		glMaterialf(GL_FRONT, GL_SHININESS, 20)
		self.model.draw()
		glPopMatrix()

```

Model.py - this represents a collection of triangles to be drawn
```

from OpenGL.GL import *
from math3D import *

class Model:
	triangles = []
	normals = []
	listname = 0
	def __init__(self,filepath):
		self.loadObj(filepath)
		self.makeNormals()
		self.createList()
		
	def createList(self):
		self.listname = glGenLists(1)
		glNewList(self.listname,GL_COMPILE)
		self.rawDraw()
		glEndList()
	
	def loadObj(self,filepath):
		modelFile = open(filepath,"r")
		triangles = []
		vertices = []
		for line in modelFile.readlines():
			line = line.strip()
			if len(line)==0 or line.startswith("#"):
				continue
			data = line.split(" ")
			if data[0]=="v":
				vertices.append((float(data[1]),float(data[2]),float(data[3])))
			if data[0]=="f":
				vertex1 = vertices[int(data[1].split("/")[0])-1]
				vertex2 = vertices[int(data[2].split("/")[0])-1]
				vertex3 = vertices[int(data[3].split("/")[0])-1]
				triangles.append((vertex1,vertex2,vertex3))
		self.triangles = triangles
	
	def makeNormals(self):
		normals = []
		for triangle in self.triangles:
			arm1 = sub3(triangle[1],triangle[0])
			arm2 = sub3(triangle[2],triangle[0])
			normals.append(normalize3(cross3(arm1,arm2)))
		self.normals = normals
	
	def draw(self):
		glCallList(self.listname)
	
	def rawDraw(self):
		glBegin(GL_TRIANGLES)
		i = 0
		for triangle in self.triangles:
			glNormal3f(self.normals[i][0],self.normals[i][1],self.normals[i][2])
			glVertex3f(triangle[0][0],triangle[0][1],triangle[0][2])
			glVertex3f(triangle[1][0],triangle[1][1],triangle[1][2])
			glVertex3f(triangle[2][0],triangle[2][1],triangle[2][2])
			i+=1
		glEnd()

```

math3D.py - 3-vector and quaternion math functions
```

from math import *

def zero3():
	return (0.0,0.0,0.0)

def copy3(v):
	return (v[0],v[1],v[2])
	
def inverse3(v):
	return (-v[0],-v[1],-v[2])

def add3(v1,v2):
	return (v1[0]+v2[0],v1[1]+v2[1],v1[2]+v2[2])

def sub3(v1,v2):
	return (v1[0]-v2[0],v1[1]-v2[1],v1[2]-v2[2])

def scale3(v,s):
	return (v[0]*s,v[1]*s,v[2]*s)

def lengthSq3(v):
	return v[0]*v[0]+v[1]*v[1]+v[2]*v[2]

def length3(v):
	return sqrt(v[0]*v[0]+v[1]*v[1]+v[2]*v[2])

def normalize3(v):
	l = length3(v)
	if l == 0:
		return (0.0,0.0,0.0)
	return (v[0]/l,v[1]/l,v[2]/l)

def dot3(v1,v2):
	return v1[0]*v2[0]+v1[1]*v2[1]+v1[2]*v2[2]
	
def cross3(v1,v2):
	return (v1[1]*v2[2]-v1[2]*v2[1],v1[2]*v2[0]-v1[0]*v2[2],v1[0]*v2[1]-v1[1]*v2[0])

def perpendicular3(v):
	if v[1]==0 and v[2]==0:
		return cross3(v,add3(v,(0,1,0)))
	return cross3(v,add3(v,(1,0,0)))


def zeroQ():
	return (1.0,0.0,0.0,0.0)

def copyQ(q):
	return (q[0],q[1],q[2],q[3])

def addQ(q1,q2):
	return (q1[0]+q2[0],q1[1]+q2[1],q1[2]+q2[2],q1[3]+q2[3])

def subQ(q1,q2):
	return (q1[0]-q2[0],q1[1]-q2[1],q1[2]-q2[2],q1[3]-q2[3])

def scaleQ(q,s):
	return (q[0]*s,q[1]*s,q[2]*s,q[3]*s)

def magnitudeSqQ(q):
	return q[0]*q[0]+q[1]*q[1]+q[2]*q[2]+q[3]*q[3]

def magnitudeQ(q):
	return sqrt(q[0]*q[0]+q[1]*q[1]+q[2]*q[2]+q[3]*q[3])

def conjugateQ(q):
	return (q[0],-q[1],-q[2],-q[3])

def multiplyQ(q1,q2):
	w1,x1,y1,z1 = q1[0],q1[1],q1[2],q1[3]
	w2,x2,y2,z2 = q2[0],q2[1],q2[2],q2[3]
	return (w1*w2 - x1*x2 - y1*y2 - z1*z2,
			w1*x2 + x1*w2 + y1*z2 - z1*y2,
			w1*y2 + y1*w2 + z1*x2 - x1*z2,
			w1*z2 + z1*w2 + x1*y2 - y1*x2)

def normalizeQ(q):
	m = magnitudeQ(q)
	if m==0:
		return (1.0,0.0,0.0,0.0)
	return (q[0]/m,q[1]/m,q[2]/m,q[3]/m)

def inverseQ(q):
	m2 = magnitudeSqQ(q)
	return (q[0]/m2,-q[1]/m2,-q[2]/m2,-q[3]/m2)

def dotQ(q1,q2):
	return q1[0]*q2[0] + q1[1]*q2[1] + q1[2]*q2[2] + q1[3]*q2[3]

def fromAngleAxisQ(radians,x,y,z):
	radians/=2.0
	s = sin(radians)/sqrt(x*x+y*y+z*z)
	return normalizeQ((cos(radians),x*s,y*s,z*s))

def toMatrixQ(q):
	w,x,y,z = q[0], q[1], q[2], q[3]
	xx = 2.0*x*x
	yy = 2.0*y*y
	zz = 2.0*z*z
	xy = 2.0*x*y
	zw = 2.0*z*w
	xz = 2.0*x*z
	yw = 2.0*y*w
	yz = 2.0*y*z
	xw = 2.0*x*w
	return (1.0-yy-zz, xy-zw, xz+yw, 0.0,
			 xy+zw, 1.0-xx-zz, yz-xw, 0.0,
			 xz-yw, yz+xw, 1.0-xx-yy, 0.0,
			 0.0, 0.0, 0.0, 1.0)

def rotateVectorQ(q,v):
	qw, qx, qy, qz = q[0], q[1], q[2], q[3]
	x, y, z = v[0], v[1], v[2]
	
	ww = qw*qw
	xx = qx*qx
	yy = qy*qy
	zz = qz*qz
	wx = qw*qx
	wy = qw*qy
	wz = qw*qz
	xy = qx*qy
	xz = qx*qz
	yz = qy*qz
	
	return (ww*x + xx*x - yy*x - zz*x + 2*((xy-wz)*y + (xz+wy)*z),
			ww*y - xx*y + yy*y - zz*y + 2*((xy+wz)*x + (yz-wx)*z),
			ww*z - xx*z - yy*z + zz*z + 2*((xz-wy)*x + (yz+wx)*y))

def interpolateQ(q1, q2, s, shortest=True):
	ca = dotQ(q1,q2)
	if shortest and ca<0:
		ca = -ca
		neg_q2 = True
	else:
		neg_q2 = False
	o = acos(ca)
	so = sin(o)

	if (abs(so)<=1E-12):
		return copyQ(q1)

	a = sin(o*(1.0-s)) / so
	b = sin(o*s) / so
	if neg_q2:
		return subQ(scaleQ(q1,a),scaleQ(q2,b))
	else:
		return addQ(scaleQ(q1,a),scaleQ(q2,b))

```

LMP1.obj - a simple OBJ-format spaceship model
```

# Wavefront OBJ file

# Exported by Misfit Model 3D 1.3.6

# Fri Jan  9 22:59:21 2009



# 13 Vertices

v 0.985767 -0.379487 1.043507

v -0.0 0.050998 -1.606737

v -0.0 0.07388 -2.5526

v -0.985767 -0.379487 1.043507

v -0.0 -0.091687 0.61302

v 0.306791 -0.009609 1.272661

v -0.306791 -0.009609 1.272661

v -0.0 0.194027 1.785505

v 0.153395 0.092209 1.529083

v -0.0 0.379487 1.145188

v 0.14346 0.281515 0.886805

v -0.153395 0.092209 1.529083

v -0.14346 0.281515 0.886805



# 60 Texture Coordinates

vt 1.0 0.0

vt 0.0 0.0

vt 0.0 1.0

vt 1.0 0.0

vt 0.0 0.0

vt 0.0 1.0

vt 1.0 0.0

vt 0.0 0.0

vt 0.0 1.0

vt 1.0 0.0

vt 0.0 0.0

vt 0.0 1.0

vt 0.0 1.0

vt 0.0 0.0

vt 1.0 0.0

vt 0.0 1.0

vt 0.0 0.0

vt 1.0 0.0

vt 0.0 1.0

vt 0.0 0.0

vt 1.0 0.0

vt 0.0 1.0

vt 0.0 0.0

vt 1.0 0.0

vt 0.0 1.0

vt 0.0 0.0

vt 1.0 0.0

vt 0.0 1.0

vt 0.0 0.0

vt 1.0 0.0

vt 0.0 1.0

vt 0.0 0.0

vt 1.0 0.0

vt 0.0 1.0

vt 0.0 0.0

vt 1.0 0.0

vt 1.0 0.0

vt 0.0 0.0

vt 0.0 1.0

vt 1.0 0.0

vt 0.0 0.0

vt 0.0 1.0

vt 1.0 0.0

vt 0.0 0.0

vt 0.0 1.0

vt 1.0 0.0

vt 0.0 0.0

vt 0.0 1.0

vt 1.0 0.0

vt 0.0 0.0

vt 0.0 1.0

vt 1.0 0.0

vt 0.0 0.0

vt 0.0 1.0

vt 0.0 1.0

vt 0.0 0.0

vt 1.0 0.0

vt 1.0 0.0

vt 0.0 0.0

vt 0.0 1.0



# ungrouped, 20 grouped triangles



o ungrouped

g ungrouped



f 1/1 2/2 3/3

f 2/4 4/5 3/6

f 5/7 6/8 7/9

f 6/10 8/11 7/12

f 3/13 6/14 1/15

f 11/16 9/17 6/18

f 7/19 2/20 5/21

f 7/22 4/23 2/24

f 10/25 12/26 8/27

f 3/28 4/29 7/30

f 2/31 6/32 5/33

f 2/34 1/35 6/36

f 9/37 10/38 8/39

f 10/40 11/41 3/42

f 11/43 10/44 9/45

f 12/46 13/47 7/48

f 13/49 10/50 3/51

f 10/52 13/53 12/54

f 3/55 7/56 13/57

f 11/58 6/59 3/60


```

---

### Post by curvedinfinity on 2009-01-11
(Added the pictures)

---

### Post by slavik on 2009-01-11
good stuff.

---

### Post by Kilon on 2009-01-12
WOW , Highly useful stuff. AMAZING! Thanks. 

I am currently using JAVA3D from python (JYTHON) . What is your opinion on 3d and python . How python handles 3d in matters of speed, available functions and ease of use ?

Would really like to hear your opinion on this. 

Your example seems like a perfect inro to OPEGL and Python. Thanks again!

---

### Post by CptPicard on 2009-01-12
> **Kilon said:**
> 
I am currently using JAVA3D from python (JYTHON) . What is your opinion on 3d and python . How python handles 3d in matters of speed, available functions and ease of use ?


The OpenGL stuff is just bindings, the library itself is C (and of course the hardware :) )... so as long as you're just calling OpenGL there are no performance implications but I would suspect that if you start doing 3D math in Python itself, there will be, and big ones. Plus then there is the slowdown of potentially transferring data from Python to OpenGL and back...

---

### Post by Sprut1 on 2009-01-12
Great reading, impressive stuff, thanks!

---

### Post by Kilon on 2009-01-12
> **CptPicard said:**
> The OpenGL stuff is just bindings, the library itself is C (and of course the hardware :) )... so as long as you're just calling OpenGL there are no performance implications but I would suspect that if you start doing 3D math in Python itself, there will be, and big ones. Plus then there is the slowdown of potentially transferring data from Python to OpenGL and back...

I have used the jythonc , which is is a Jtyhon compiler that makes a java source file and the java.class file which is the java bytecode. The Java source file that it created was a mess , although the mess may be a fault of the the jython compiler only and not python's architecture. But I see that there is quite a process to convert python code to java. 

Is it not the situation similar to Jython here ? On other hand I saw claims that jython was 150-300x times slower compared to java! My own benchmarks say that jython is no more slower 4x times than JAVA.

So does in not the wrapping itself create a slowdown ?

Of course even under heavy use on a DUAL CORE , my jython processing intensive apps run in an instant, with no observable delays. So this might be a mute point for DUAL and QUAD CORES with modern graphics cards.

---

### Post by slavik on 2009-01-12
> **Kilon said:**
> I have used the jythonc , which is is a Jtyhon compiler that makes a java source file and the java.class file which is the java bytecode. The Java source file that it created was a mess , although the mess may be a fault of the the jython compiler only and not python's architecture. But I see that there is quite a process to convert python code to java. 

Is it not the situation similar to Jython here ? On other hand I saw claims that jython was 150-300x times slower compared to java! My own benchmarks say that jython is no more slower 4x times than JAVA.

So does in not the wrapping itself create a slowdown ?

Of course even under heavy use on a DUAL CORE , my jython processing intensive apps run in an instant, with no observable delays. So this might be a mute point for DUAL and QUAD CORES with modern graphics cards.
depends on what you are doing ;)

---

### Post by Kilon on 2009-01-12
> **slavik said:**
> depends on what you are doing ;)
Always talking strictly about 3d,

I have no problem implementing some of the code in C++. But would like to create my code minimum 80%, using python.

---

### Post by CptPicard on 2009-01-12
> **Kilon said:**
> I have used the jythonc , which is is a Jtyhon compiler that makes a java source file and the java.class file which is the java bytecode. The Java source file that it created was a mess , although the mess may be a fault of the the jython compiler only and not python's architecture. But I see that there is quite a process to convert python code to java. 

Sure there is -- this is exactly what I'm always talking about when I say that higher-level languages contain lower-level languages trivially, but it does not go the other way, even though they are theoretically equivalent.

Because Java does not have a list comprehension, for example, support code for that needs to be compiled in. And a lot of the runtime stuff still needs an outright runtime engine which is included in the jython JAR.

Now, it is an interesting question how much slower Jython is than Python itself is. Both use bytecode as an intermediate, for Jython it just happens to be the Java bytecode, via a Java source transformation...


> **Kilon said:**
> 
I have no problem implementing some of the code in C++. But would like to create my code minimum 80%, using python.

Combining Python and C is much easier than Python and C++. There is the data transfer at the interface of the two languages whose speed you need to worry about..

---

### Post by curvedinfinity on 2009-01-12
> **Kilon said:**
> WOW , Highly useful stuff. AMAZING! Thanks. 

I am currently using JAVA3D from python (JYTHON) . What is your opinion on 3d and python . How python handles 3d in matters of speed, available functions and ease of use ?

Would really like to hear your opinion on this. 

Your example seems like a perfect inro to OPEGL and Python. Thanks again!

In the current iteration of this example, I have the static ships all drawn by a single display list. Previously, I had them drawn individually, and Python was able to handle about 125 max. That didn't include all of the order 2 loops involved with collision that are normally in a simulation.

In general, that's a real issue with 3D python: the "simulation" part has to either be ultra simple or ultra optimized. As I was continuing, it would have been very necessary to create an oct-tree and some other collision culling optimizations (which wouldn't have been necessary with C++).

That said, you can go bananas with the graphics, as long as they are properly loaded onto the graphics card. Also, this was about a third of the code that is necessary in C++.

EDIT: My job is writing java, and I've done some 3D apps with it before. In general, I have a strong distaste for java. Python gives you much much much more flexibility for a marginal speed hit. If you need the speed, C++ should be used.

---

### Post by Kilon on 2009-01-12
> **curvedinfinity said:**
> In the current iteration of this example, I have the static ships all drawn by a single display list. Previously, I had them drawn individually, and Python was able to handle about 125 max. That didn't include all of the order 2 loops involved with collision that are normally in a simulation.

In general, that's a real issue with 3D python: the "simulation" part has to either be ultra simple or ultra optimized. As I was continuing, it would have been very necessary to create an oct-tree and some other collision culling optimizations (which wouldn't have been necessary with C++).

That said, you can go bananas with the graphics, as long as they are properly loaded onto the graphics card. Also, this was about a third of the code that is necessary in C++.

EDIT: My job is writing java, and I've done some 3D apps with it before. In general, I have a strong distaste for java. Python gives you much much much more flexibility for a marginal speed hit. If you need the speed, C++ should be used.


impressive stuff. That motivates me to take python more seriously with 3d. 

Jython is actually 100% python syntax.I just use it to call JAVA libraries. Unless you mean that you did not like the JAVA3D api and prefer the Python OPENGL wrappings. 

Which one is it ? If it is the second , what you did not like of JAVA3D ?

---

### Post by curvedinfinity on 2009-01-12
My biggest gripe of Java is how it is extremely necessary to know how the language's datastructures work internally, where their innerworkings and functional speed are completely undocumented. Java also has ludicrously drawn out syntax and forces you to do it "their way," which often makes code bloated.

If Jython solves those problems, then it is a good solution.

If you are looking for a serious "solution" for making a game, a set of custom C/C++ bindings to Python or another scripting language would be ideal. The bindings could handle all the fancy physics and collision, while you still have the flexibility of the scripting language.

I was just shooting toward making a game that had few dependencies and a small code base, in which case Python can't be beat.

---

### Post by Kilon on 2009-01-12
> **curvedinfinity said:**
> My biggest gripe of Java is how it is extremely necessary to know how the language's datastructures work internally, where their innerworkings and functional speed are completely undocumented. Java also has ludicrously drawn out syntax and forces you to do it "their way," which often makes code bloated.

If Jython solves those problems, then it is a good solution.

If you are looking for a serious "solution" for making a game, a set of custom C/C++ bindings to Python or another scripting language would be ideal. The bindings could handle all the fancy physics and collision, while you still have the flexibility of the scripting language.

I was just shooting toward making a game that had few dependencies and a small code base, in which case Python can't be beat.

I see , I am new with both Jython and JAVA. That is why I ask. Well I will try both approaches , mine and yours and see what fits me best. 

I am also interested in small code. I try to set goals that I can easily achieve.

---

### Post by curvedinfinity on 2009-01-14
Also, for java try Processing...

[http://www.processing.org](http://www.processing.org)

Processing is amazing. I don't know why no one knows about it...

---

### Post by Wybiral on 2009-01-14
> **curvedinfinity said:**
> If you are looking for a serious "solution" for making a game, a set of custom C/C++ bindings to Python or another scripting language would be ideal. The bindings could handle all the fancy physics and collision, while you still have the flexibility of the scripting language.

A very good solution for handling the collision/physics is PyODE, that's what I typically use for simulations and stuff. But, even more ideal would be one of the larger, full-featured game engines floating around out there (with Python bindings).

---

### Post by curvedinfinity on 2009-01-15
> **Wybiral said:**
> A very good solution for handling the collision/physics is PyODE, that's what I typically use for simulations and stuff. But, even more ideal would be one of the larger, full-featured game engines floating around out there (with Python bindings).

Thats a bad *** library! I'll be playing with that! \\:D/

---

### Post by hod139 on 2009-01-15
An alternative to ODE is Bullet: [http://www.bulletphysics.com](http://www.bulletphysics.com)
For example, blender is now using Bullet for all its collision detection and simulation needs.

ODE and Blender both use similar formulations of the dynamics (and make similar hacks for speed), so preferences in their use will most likely be personal, since the simulation results should be comparable.

---

