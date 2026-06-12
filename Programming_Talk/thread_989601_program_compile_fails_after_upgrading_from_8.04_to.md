---
title: "program compile fails after upgrading from 8.04 to 8.10"
date: 2008-11-21
forum: Programming Talk
---

### Post by mysydney on 2008-11-21
Hi all,
My c/c++ program works fine under Ubuntu8.04, but after I upgraded to Ubuntu 8.10. I cannot get compile the program successfully. My program is a graphics program, and uses opengl APIs. Errors are not related with graphics stuffs, but I found that the compile errors are related with Ubuntu 8.10 c/c++ libraries or compilers. Anyone give me any information on how to solve compiling problems after upgrading from Ubuntu 8.04 to 8.10? Thanks a lot!

---

### Post by slavik on 2008-11-21
Can you post the errors?

---

### Post by mysydney on 2008-11-21
> **slavik said:**
> Can you post the errors?
Hi, Thanks for your quick reply. Here is part of errors, others are similar with follows:

joye@joye-desktop:~/cgvis/trunk/vis$ make
g++ -c -pipe -Wall -W -g -D_REENTRANT  -DUSE_ZLIB -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -Isrc -I/usr/include -I/usr/include/cg -I/usr/include/qt3 -I/usr/include/qt3 -I/usr/X11R6/include -I/usr/X11R6/include -Itmp/moc/ -o tmp/obj/Tree.o src/Tree.cpp
In file included from src/GeomTypes.h:4,
                 from src/Tree.h:10,
                 from src/Tree.cpp:1:
src/Geometry/Point.h:46: error: declaration of &#8216;typedef class Geometry::Vector<ScalarParam, dimensionParam> Geometry::Point<ScalarParam, dimensionParam>::Vector&#8217;
src/Geometry/Vector.h:33: error: changes meaning of &#8216;Vector&#8217; from &#8216;class Geometry::Vector<ScalarParam, dimensionParam>&#8217;
src/Geometry/Point.h:47: error: declaration of &#8216;typedef struct Geometry::AffineCombiner<ScalarParam, dimensionParam> Geometry::Point<ScalarParam, dimensionParam>::AffineCombiner&#8217;
src/Geometry/Point.h:34: error: changes meaning of &#8216;AffineCombiner&#8217; from &#8216;struct Geometry::AffineCombiner<ScalarParam, dimensionParam>&#8217;
In file included from src/Geometry/Rotation.h:29,
                 from src/GeomTypes.h:7,
                 from src/Tree.h:10,
                 from src/Tree.cpp:1:
src/Geometry/HVector.h:44: error: declaration of &#8216;typedef class Geometry::Vector<ScalarParam, dimensionParam> Geometry::HVector<ScalarParam, dimensionParam>::Vector&#8217;

......

where 
Geometry/Vector.h, Point.h, ... are libraries from others used for basic geometry processing, and it works fine under 8.04.

---

### Post by slavik on 2008-11-21
try writing code without the above typedefs?

---

### Post by mysydney on 2008-11-21
> **slavik said:**
> try writing code without the above typedefs?
THis does not work if I remove "typedef" inside, and errors are like follows:

.......
In file included from src/GeomTypes.h:4,
                 from src/Tree.h:10,
                 from src/Tree.cpp:1:
src/Geometry/Point.h:48: error: declaration of &#8216;Geometry::Vector<ScalarParam, dimensionParam> Geometry::Point<ScalarParam, dimensionParam>::Vector&#8217;
src/Geometry/Vector.h:33: error: changes meaning of &#8216;Vector&#8217; from &#8216;class Geometry::Vector<ScalarParam, dimensionParam>&#8217;
src/Geometry/Point.h:49: error: declaration of &#8216;Geometry::AffineCombiner<ScalarParam, dimensionParam> Geometry::Point<ScalarParam, dimensionParam>::AffineCombiner&#8217;
src/Geometry/Point.h:34: error: changes meaning of &#8216;AffineCombiner&#8217; from &#8216;struct Geometry::AffineCombiner<ScalarParam, dimensionParam>&#8217;
In file included from src/Geometry/Rotation.h:29,
                 from src/GeomTypes.h:7,
                 from src/Tree.h:10,
                 from src/Tree.cpp:1:
src/Geometry/HVector.h:46: error: declaration of &#8216;Geometry::Vector<ScalarParam, dimensionParam> Geometry::HVector<ScalarParam, dimensionParam>::Vector&#8217;
src/Geometry/Vector.h:33: error: changes meaning of &#8216;Vector&#8217; from &#8216;class Geometry::Vector<ScalarParam, dimensionParam>&#8217;

.......

---

### Post by slavik on 2008-11-22
since I don't have a copy of the code, I'm afraid I won't be of much help. I have not seen those errors before, either.

---

### Post by kripkenstein on 2008-11-22
> **slavik said:**
> since I don't have a copy of the code, I'm afraid I won't be of much help. I have not seen those errors before, either.
Ditto. I think we can only help if we see the full source.

---

### Post by mysydney on 2008-11-22
> **kripkenstein said:**
> Ditto. I think we can only help if we see the full source.
Here is part of the code of Point.h. The line number of errors is the line where "typedef" locates in the following code:


#include <Geometry/MathTemplates.h>
#include <Geometry/ComponentArray.h>
#include <Geometry/Vector.h>

namespace Geometry {

/* Forward declarations: */
template <class ScalarParam,int dimensionParam>
class AffineCombiner;

template <class ScalarParam,int dimensionParam>
class Point:public Geometry::ComponentArray<ScalarParam,dimensionParam>
	{
	/* Declarations of inherited types/elements: */
	public:
	using ComponentArray<ScalarParam,dimensionParam>::dimension;
	using ComponentArray<ScalarParam,dimensionParam>::components;
	
	/* Embedded classes: */
	public:
	typedef Vector<ScalarParam,dimensionParam> Vector; // Compatible vector type
	typedef AffineCombiner<ScalarParam,dimensionParam> AffineCombiner; // Compatible affine combiner type
	
	/* Constructors and destructors: */
	static const Point origin; // The zero point (origin of local coordinate system)
	Point(void) // No initialization
		{
		};

.....
.....
};

---

### Post by kripkenstein on 2008-11-22
Still can't figure it out. The error messages reference another file as well.

Also, to really help you, I'd need to compile it over here to see how changes to the code affect the error messages.

---

### Post by zipperback on 2008-11-22
Perhaps you could post your source code online for others to download. This way we can try to actually help you resolve the problem.

Unless of course you don't plan on releasing your application as open source.

Either way, if the code is available it might be easier to help you.


- zipperback

---

### Post by mysydney on 2008-11-22
> **zipperback said:**
> Perhaps you could post your source code online for others to download. This way we can try to actually help you resolve the problem.

Unless of course you don't plan on releasing your application as open source.

Either way, if the code is available it might be easier to help you.


- zipperback
Thanks, because my code is related to a project, so there are problem for post code online. I will figure it out these days.

---

