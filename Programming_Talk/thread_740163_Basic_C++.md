---
title: "Basic C++"
date: 2008-03-30
forum: Programming Talk
---

### Post by mikeym on 2008-03-30
Hi,

I'm trying to get started with C++ and I'm finding it about as clear as mud. There appear to be a lot of functions that work behind the scenes that you just have to *know* how they work. 

I'm coming from a background of java and scipting languages such as PHP and bash and (*cough*) VB. So that's the language I'll employ to describe what I'm looking for.

I want to create an abstract class *Shape* and a non abstract implementation of it Sphere. I wanted to put most of the standard functions into Shape and have a abstract function Create to do the business of actually creating the specific shapes.

Now no matter what I've tried I can't get it to compile. I've even tried abandoning the abstract class idea because I thought it might be simpler but that's not worked.

Anyway this is where I'm at:

**Shape.h**
```

/***
	Author: Mikey	
	Email: abc.mikey@googlemail.com
	Modified: 30/03/08
***/
#ifndef SHAPE_H
#define SHAPE_H 1

#include <GL/gl.h>
#include "svl/SVL.h"
#include "svl/SVLgl.h"
#define PI 3.1415926535897932384626433832795 


class Shape {
	public:

		Shape() {
			maxLong=0;
			maxLat=0;
			closedlong=false;
			closedlat=false;
		}
		void setLong(int Long);
		void setLat(int Lat);
		int getLong() { return maxLong+1; }
		int getLat() { return maxLat +1; }
		bool ClosedLong() { return closedlong; }
		bool ClosedLat() { return closedlat; }
		Vec3 getMatrix(int Long, int Lat);
		void setMatrix(int Long, int Lat, Vec3 v);
		void Create();
	private:
		Vec3 *vmatrix;
		int maxLong;
		int maxLat;
		bool closedlong;
		bool closedlat;
 };

class Sphere : public Shape {
	public:
		void Create();
		void Create(float rad);
		Sphere(float rad) { Create(rad); }
		Sphere() { }
		int getSegments() { return segments; }
		void setSegments(int segs);
	private:
		float rad;
		int segments;
};

#endif

```

**Shape.cpp**
```

/***
	Author: Mikey	
	Email: abc.mikey@googlemail.com
	Modified: 30/03/08
***/
#include "Shape.h"


void Shape::setLong(int Long) {
	maxLong = Long + 1;
	if(maxLong >= 0 && maxLat >= 0) {
		delete [] vmatrix;
		vmatrix = new Vec3[maxLong][maxLat];
	}
}

void Shape::setLat(int Lat) {
	maxLat = Lat + 1;
	if(maxLong >= 0 && maxLat >= 0) {
		delete [] vmatrix;
		vmatrix = new Vec3[maxLong][maxLat];
	}
}

Vec3 Shape::getMatrix(int Long, int Lat) {
	if (Long < 0 || Long > maxLong || Lat < 0 || Lat > maxLat ) {
		std::cerr << "Shape::getMatrix - ERROR **:  Out Of Range." << std::endl;
	}
	return *vmatrix[Long][Lat];
}

void Shape::setMatrix(int Long, int Lat, Vec3 v) {
	if (Long < 0 || Long > maxLong || Lat < 0 || Lat > maxLat ) {
		std::cerr << "Shape::setMatrix - ERROR **:  Out Of Range." << std::endl;
	}
	*vmatrix[Long][Lat]=v;
}

void Shape::Create() { 
}

void Sphere::Create() { 
	rad = 1;
	setSegments(20);
	Create(rad);
}

void Sphere::Create(float rad) {
	float theta, phi;
	for(int i=0;i<=maxLat;i++) {
		theta = i*PI/maxLat;
		for(int j=0;j<=maxLong;j++) {
			phi = j*2*PI/maxLong;
			x = r*cos(theta)*sin(phi);
			y = r*sin(theta)*sin(phi);
			z = r*cos(phi);
			vmatrix[j][i]= Vec3(x,y,z);
			printf("V%i%i(%f,%f,%f) at %f by %f\n", j, i, x, y, z, 180*theta/PI, 180*phi/PI);
		}
	}
}

void Sphere::setSegments(int segs) {
	if (segs < 2) {
		std::cerr << "Shape::setSegments - ERROR **:  Segments must be >= 2." << std::endl;
	}
	if (segs % 2 != 0) {
		std::cerr << "Shape::setSegments - ERROR **:  Must be even number of segments." << std::endl;
	}
	setLat(segs/2+1):
	setLong(segs);
	segments = segs;
}

```

**testshapes.cpp**
```

#include <stdio.h>
#include <stdlib.h>
#include "Shape.h"

 
// Init everything
int main(int argc, char* argv[]) {
	Sphere s(1);
	return (0);
};

```

Oh yeh! Here's the current error (they all centre around the constructors and create):

```

/tmp/ccJduq65.o: In function `Sphere::Sphere(float)':
testshapes.cpp:(.text._ZN6SphereC1Ef[Sphere::Sphere(float)]+0x2a): undefined reference to `Sphere::Create(float)'
collect2: ld returned 1 exit status

```

---

### Post by mikeym on 2008-03-30
OK so basically how do I organize my .cpp file and .h file? I thought you put the definition of the class in the .h file and everything else in the .cpp file written like 

```
Shape::Shape() {
//do it
}
```

But it's not finding anything that's in the cpp file. Do I need to explicitly include it or something?

---

### Post by WW on 2008-03-30
There are many little mistakes in your code.  I recommend developing and debugging your class hierarchy in smaller steps.  Don't try to define the Sphere object until after you have a working (i.e. compiled and tested) Shape object.  As you develop Sphere and other objects, you'll probably go back and revise the base Shape object, but still, it would be better to have a first draft of Shape working before coding up the Sphere object.

A few details:

In the Shape class, you have declared maxLat (and other data) to be "private", but then you try to use it directly in the Sphere class.  This is not allowed. Either use your "getter" and "setter" methods  for the data, or declare them "protected".
 
If you use std::cerr, <<, etc for output, you must include <iostream>, not <stdio.h>. This is C++, not C.

In Sphere::Create(float rad) , you use r, but I think you mean rad.  Also you haven't declared x, y and z.

In Sphere::setSegments(int segs), there is a statement terminated with a : instead of a ;

---

### Post by mikeym on 2008-03-30
Thanks.

That's quite a though assessment of the mistakes I made. I had encounted most of them by moving my functions from Shape.cpp to Shape.h which will let me attempt to compile, but there must be a way of using the .h file with the .cpp file or else there is no point to it!

The reason I hadn't tested it till this stage is that origionaly it contained an abstract function so wouldn't compile. 

<iostream> over <stdio.h> is again something that you just have to know I suppose.

---

### Post by WW on 2008-03-30
> **mikeym said:**
> OK so basically how do I organize my .cpp file and .h file? I thought you put the definition of the class in the .h file and everything else in the .cpp file written like 

```
Shape::Shape() {
//do it
}
```

Sounds good.
> **mikeym said:**
> 
But it's not finding anything that's in the cpp file. Do I need to explicitly include it or something?
What do you mean?  Show the all commands that you are using to compile the code.  If you are using an IDE, try using the command line to build it (at least until you figure out the problem.)  E.g., in a terminal, these should work:
> 
$ g++ -c Shape.cpp            # add options needed for the libraries
$ g++ -c testshapes.cpp
$ g++ testshapes.o Shape.o -lgl -lsvl -o testshapes   # add other options for the libraries
$


---

### Post by WW on 2008-03-30
> **mikeym said:**
> 
<iostream> over <stdio.h> is again something that you just have to know I suppose.
Well, you are trying to write a C++ program, so yes,  you should know some C++ :)
Nobody "just knows" things like that.  They learn them by, either in a class or from a book or online tutorial. (Just be careful: there are some bad tutorials out there.)

By the way, is this project heading towards a generalization of the OpenGl program that you showed in your other thread?

---

### Post by mikeym on 2008-03-30
I have the files with the fixes you've mentioned and when I run I get:

```

g++ -o test  testshapes.cpp
/tmp/cc4FDEBr.o: In function `main':
testshapes.cpp:(.text+0xa2): undefined reference to `Shape::getMatrix(int, int)'
/tmp/cc4FDEBr.o: In function `Sphere::Sphere(float)':
testshapes.cpp:(.text._ZN6SphereC1Ef[Sphere::Sphere(float)]+0x2a): undefined reference to `Sphere::Create(float)'
collect2: ld returned 1 exit status

```

If I copy and paste the same functions to the end of my Shapes.h file it will compile... 

I've no idea why except that it could be because it is demanding that all the functions that get called from withing the constructor are in the header file. (That however is all of them.)

---

### Post by WW on 2008-03-30
The command you used hasn't told the compiler about Shapes.cpp.  You need to include Shapes.cpp in the command:
> 
   g++ -o testshapes  testshapes.cpp Shapes.cpp

(I don't like calling my executable files "test", since "test" is also a bash command.)

---

