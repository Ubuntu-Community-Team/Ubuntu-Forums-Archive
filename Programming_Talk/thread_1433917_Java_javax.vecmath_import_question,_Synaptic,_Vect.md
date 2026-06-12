---
title: "Java javax.vecmath import question, Synaptic, Vector3d"
date: 2010-03-19
forum: Programming Talk
---

### Post by raequin on 2010-03-19
Hi there.  I want to use the Vector3d object for a Java application I'm writing.  I searched for and installed the javax.vecmath package via Synaptic.  I do not know what else I need to do in order to use this package in my application.  Here's a quick snippet and then some of the errors I'm getting on compile.

```
import javax.vecmath.*;

class ThreeDData {    

    Vector3d centroidOfTriangle(double[] corners) {
	/* Generate Vector3d's for the point coordinates of each corner of the triangle */
	Vector3d[] vertices = new Vector3d[3];
	for (int i = 0; i < 3; i++)
	    vertices[i] = new Vector3d(corners[3 * i], corners[3 * i + 1], corners[3 * i + 2]);


	/* Find the mid points of two legs of the triangle */
	Vector3d rA = new Vector3d();
	rA.add(vertices[0], vertices[2]);
	rA.scale(.5);
	Vector3d rB = new Vector3d();
	rB.add(vertices[0], vertices[1]);
	rB.scale(.5);

...

```

etc.

Then, here are some results from make:

```
ThreeDData.java:1: package javax.vecmath does not exist
import javax.vecmath.*;
                    ^
ThreeDData.java:6: cannot find symbol
symbol  : class Vector3d
location: class ThreeDData
    Vector3d centroidOfTriangle(double[] corners) {
    ^
ThreeDData.java:8: cannot find symbol
symbol  : class Vector3d
location: class ThreeDData
	Vector3d[] vertices = new Vector3d[3];
	^
ThreeDData.java:8: cannot find symbol
symbol  : class Vector3d
location: class ThreeDData
	Vector3d[] vertices = new Vector3d[3];
	                          ^
ThreeDData.java:10: cannot find symbol
symbol  : class Vector3d
location: class ThreeDData
	    vertices[i] = new Vector3d(corners[3 * i], corners[3 * i + 1], corners[3 * i + 2]);
	                      ^
ThreeDData.java:14: cannot find symbol
symbol  : class Vector3d
location: class ThreeDData
	Vector3d rA = new Vector3d();
	^
ThreeDData.java:14: cannot find symbol
symbol  : class Vector3d
location: class ThreeDData
	Vector3d rA = new Vector3d();

```

And here's what I get from "locate vecmath"

```
/usr/share/doc/libvecmath-java
/usr/share/doc/libvecmath-java/changelog.Debian.gz
/usr/share/doc/libvecmath-java/copyright
/usr/share/java/vecmath-1.5.2.jar
/usr/share/java/vecmath.jar
/var/cache/apt/archives/libvecmath-java_1.5.2-2_all.deb
/var/lib/dpkg/info/libvecmath-java.list
/var/lib/dpkg/info/libvecmath-java.md5sums

```

So can you tell me what I'm missing?  Thanks for looking.

---

### Post by raequin on 2010-03-19
Okay, so I guess I solved this.  I changed the first line of makefile to look like this:

```
JFLAGS = -cp ../Jama\-1\.0\.2.jar:../utils/:/usr/share/java/vecmath\-1\.5\.2.jar:.
```

Sorry for the slackness of prematurely posting.  Later.

---

