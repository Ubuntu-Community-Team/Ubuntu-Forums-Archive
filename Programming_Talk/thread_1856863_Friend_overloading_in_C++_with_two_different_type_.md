---
title: "Friend overloading in C++ with two different type arguments"
date: 2011-10-09
forum: Programming Talk
---

### Post by mhueting on 2011-10-09
Hi there!

I've got a program which consists of multiple source files and classes. Two of the classes are Vector and Point. When subtracting two points from each other, a vector should be returned.

In vector.h the following is specified:

```
friend Vector operator-(Point&, Point&);//Vector = Point-Point

```

This function has the following definition:

```
Vector operator-(Point& p1, Point& p2)
//returns p1 - p2
{
	Vector v;
	
	v.X = p1.x()-p2.x();
	v.Y = p1.y()-p2.y();
	v.Z = p1.z()-p2.z();
	
	return v;
}

```

This operator should be used in the sphere class, defined as such in sphere.h:

```
	Vector normal(Point p) {return (p-Centre).normalised();}
```


On GCC 4.5.2 this does not compile, giving me the error 

```
g++ -I/usr/opt/glut/build/glut-3.6/include -c sphere.cpp -o sphere.o
In file included from sphere.cpp:3:0:
sphere.h: In member function ‘virtual Vector Sphere::normal(Point)’:
sphere.h:17:36: error: no match for ‘operator-’ in ‘p - ((Sphere*)this)->Sphere::Centre’
make: *** [sphere.o] Error 1

```

Can anyone explain to me if this code is correct and if so how it SHOULD work? Somehow the code does compile on MS Visual Studio and on GCC 4.0.1. Is there a bug that has been fixed since which makes the code incorrect?

If more information is needed to answer the question I'll gladly supply it.

---

### Post by gardnan on 2011-10-09
I am not really a C++ programmer but I will tell you what I think for what its worth. I have always found that using operator overloading in complex statements was finicky at best. Whenever I try to do it, I get an error much like yours, and it seems to me that maybe GCC is trying to pass the whole expression on the right hand side to the function at once, rather than evaluating it to a Point first. I.E you are trying to perform the subtraction operator not on two Points but one Point and one Sphere*->Sphere::Centre (annoying right?). Anyway, the only way I have ever solved the problem is a bit unsatisfying but here goes:
```

Vector normal(Point p) { Point temp = Centre; return (p-temp).normalize(); }
```Just make sure that you have the equals operator satisfactorily defined for Point to avoid errors. I am pretty sure there is a better way to do this, but I can't seem to find it.

---

### Post by ofnuts on 2011-10-09
> **mhueting said:**
> Hi there!

I've got a program which consists of multiple source files and classes. Two of the classes are Vector and Point. When subtracting two points from each other, a vector should be returned.

In vector.h the following is specified:

```
friend Vector operator-(Point&, Point&);//Vector = Point-Point

```This function has the following definition:

```
Vector operator-(Point& p1, Point& p2)
//returns p1 - p2
{
    Vector v;
    
    v.X = p1.x()-p2.x();
    v.Y = p1.y()-p2.y();
    v.Z = p1.z()-p2.z();
    
    return v;
}

```This operator should be used in the sphere class, defined as such in sphere.h:

```
    Vector normal(Point p) {return (p-Centre).normalised();}
```
On GCC 4.5.2 this does not compile, giving me the error 

```
g++ -I/usr/opt/glut/build/glut-3.6/include -c sphere.cpp -o sphere.o
In file included from sphere.cpp:3:0:
sphere.h: In member function ‘virtual Vector Sphere::normal(Point)’:
sphere.h:17:36: error: no match for ‘operator-’ in ‘p - ((Sphere*)this)->Sphere::Centre’
make: *** [sphere.o] Error 1

```Can anyone explain to me if this code is correct and if so how it SHOULD work? Somehow the code does compile on MS Visual Studio and on GCC 4.0.1. Is there a bug that has been fixed since which makes the code incorrect?

If more information is needed to answer the question I'll gladly supply it.Asking the obvious: is Sphere::Centre a Point?

---

