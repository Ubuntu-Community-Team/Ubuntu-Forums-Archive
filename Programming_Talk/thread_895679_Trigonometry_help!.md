---
title: "Trigonometry help!"
date: 2008-08-20
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-08-20
So, I don't know anything about trigonometry. And I want to know, how to check if...

1. two lines cut eachothers?

2. a point is inside a triangle?

Could you post it in trigonometry? And if possible, post it in python. 
I think I'd be able to convert it to python, altrough I don't know trigonometry.

If I'm asking ridiculous things, could you post me a link to a site where are python scripts like those?

And no fries with that this time, thanks.

---

### Post by Lster on 2008-08-20
I've had these problems myself.

What format do you have the lines in? And are they lines or line segments?

---

### Post by hod139 on 2008-08-20
[http://geometryalgorithms.com/algorithm_archive.htm](http://geometryalgorithms.com/algorithm_archive.htm)

Point in Polygon: [http://geometryalgorithms.com/Archive/algorithm_0103/algorithm_0103.htm](http://geometryalgorithms.com/Archive/algorithm_0103/algorithm_0103.htm)

Intersection of lines: [http://geometryalgorithms.com/Archive/algorithm_0104/algorithm_0104B.htm](http://geometryalgorithms.com/Archive/algorithm_0104/algorithm_0104B.htm)

---

### Post by crazyfuturamanoob on 2008-08-20
I am presenting my lines in a form of (x1,y1,x2,y2). But I feel dizzy if I try to look at those examples hod139 posted, I just don't get them.

Well, I actually found one, but it is in c++. Anyone able to translate it to python? Here it is:
```
float linx,liny;

float abs2(float x)
{
      if (x<0) {return -x;}
      return x;
}

int LinesCross(float x0,float y0,float x1,float y1,float x2,float y2,float x3,float y3)
{
	float d=(x1-x0)*(y3-y2)-(y1-y0)*(x3-x2);
	if (abs2(d)<0.001) {return -1;}
	float AB=((y0-y2)*(x3-x2)-(x0-x2)*(y3-y2))/d;
	if (AB>0.0 && AB<1.0)
	{
		float CD=((y0-y2)*(x1-x0)-(x0-x2)*(y1-y0))/d;
		if (CD>0.0 && CD<1.0)
        { 
			linx=x0+AB*(x1-x0);
			liny=y0+AB*(y1-y0);
			return 1;
        }
    }
	return 0;
}

```
Oh, that is supposed to check line intersection.
If you translate it to python, could you make it so it returns True and False, not 1 and 0? And I would like it to be packed in one clean function.

---

### Post by Lster on 2008-08-20
To test if a line crosses another with two lines in the format:

(ax0, ay0) (ax1, ay1)
(bx0, by0) (bx1, by1)

Get the gradient for both:

am = (ay0-ay1)/(ax0-ax1)
bm = (by0-by1)/(bx0-bx1)

Get the intercept:

ac = ay0-am*ax0
bc = by0-bm*bx0

Now since:

y = am*x + ac
y = bm*x + bc

am*x + ac = bm*x + bc
(am-bm)*x = bc-ac
x = (bc-ac)/(am-bc)

Finally, the lines only intersect if:

min(ax0, ax1) &#8804; x &#8804; max(ax0, ax1)

and

min(bx0, bx1) &#8804; x &#8804; max(bx0, bx1)

You should note that this method fails if ax0 = ax1 or bx0 = bx1 or am = bc. I can make some changes if you need these cases to work.

As for checking is a point lies inside a triangle: for each of the three sides, check that the point lies the same side as the point that isn't making the side. This is one way... Others may be better, so check:

[http://mathforum.org/library/drmath/view/54735.html](http://mathforum.org/library/drmath/view/54735.html)

:)

---

### Post by jinksys on 2008-08-20
> **crazyfuturamanoob said:**
> 
And no fries with that this time, thanks.

:roll:

That's really gonna make me want to help, geez.

---

### Post by hod139 on 2008-08-20
> **crazyfuturamanoob said:**
> 
If you translate it to python, could you make it so it returns True and False, not 1 and 0? And I would like it to be packed in one clean function.

Would you like me to do your laundry too!!!   You asked questions about two geometry algorithms, I gave links with explanations and C++ implementations.  Your posting style makes this sounds suspiciously like a homework assignment you are stuck on, and there are [rules]("http://ubuntuforums.org/showthread.php?t=717011") in place about this.  I suggest you read the links that I provided, and if you have any **specific** questions post back and many people will be eager to help you.  You have to be willing to put in some effort yourself though, and not only rely solely on the generous effort of others.

---

### Post by jinksys on 2008-08-20
> **hod139 said:**
> Would you like me to do your laundry too!!!   

Sure! And make sure there's a command line switch for whites and colors, hate when my whites lose their luster!

---

### Post by ghostdog74 on 2008-08-20
> **crazyfuturamanoob said:**
> I am presenting my lines in a form of (x1,y1,x2,y2). But I feel dizzy if I try to look at those examples hod139 posted, I just don't get them.

Well, I actually found one, but it is in c++. Anyone able to translate it to python? Here it is:
```
float linx,liny;

float abs2(float x)
{
      if (x<0) {return -x;}
      return x;
}

int LinesCross(float x0,float y0,float x1,float y1,float x2,float y2,float x3,float y3)
{
	float d=(x1-x0)*(y3-y2)-(y1-y0)*(x3-x2);
	if (abs2(d)<0.001) {return -1;}
	float AB=((y0-y2)*(x3-x2)-(x0-x2)*(y3-y2))/d;
	if (AB>0.0 && AB<1.0)
	{
		float CD=((y0-y2)*(x1-x0)-(x0-x2)*(y1-y0))/d;
		if (CD>0.0 && CD<1.0)
        { 
			linx=x0+AB*(x1-x0);
			liny=y0+AB*(y1-y0);
			return 1;
        }
    }
	return 0;
}

```
Oh, that is supposed to check line intersection.
If you translate it to python, could you make it so it returns True and False, not 1 and 0? And I would like it to be packed in one clean function.

this is so easy to convert to Python. Remove the braces { } and ( ). Remove the types (float,int) etc.. I am sure you know what to do.

---

### Post by crazyfuturamanoob on 2008-08-21
I understand why you think it is homework. It isn't. But I can't prove it.

Some weeks ago I came from primary school to highschool. They haven't even taught
me yet da trigonometries. I think they teach it some time after xmas. And I am
trying to learn programming myself, without a teacher. I am making a pys60 game just for fun.

I have copied some code, like checking key presses, because I am noob in programming, and 
I can't make those things myself. And it is hard to learn, when I'm trying to learn it myself.

...

[SIZE="1"]Ofcourse nobody believes, no matter what I say it sounds like a lie...[/SIZE]

Edit: I tried to make that code to python from c++ but it doesn't work. It always returns 0, even if the lines cross.
[PHP]
from math import *

def abs2(x):
      if (x<0) :
        return -x
      else:
        return x

def LinesCross(x0, y0, x1, y1, x2, y2, x3, y3):
	d=(x1-x0)*(y3-y2)-(y1-y0)*(x3-x2)
	if (abs2(d)<0.001):
            return -1
	AB=((y0-y2)*(x3-x2)-(x0-x2)*(y3-y2))/d
	if (AB>0.0 and AB<1.0):
                CD=((y0-y2)*(x1-x0)-(x0-x2)*(y1-y0))/d
		if (CD>0.0 and CD<1.0):
			linx=x0+AB*(x1-x0)
			liny=y0+AB*(y1-y0)
			return 1
	return 0


print LinesCross(0,0,50,0, 25,25,25,-25)[/PHP]

---

### Post by Jessehk on 2008-08-21
Two lines intersecting in 3 dimensions is a linear algebra problem, not trigonometry. 

Generally you'd construct matrices and solve them using the Gauss-Jordan method.
See [here](http://en.wikipedia.org/wiki/Gauss-Jordan_elimination).

---

### Post by crazyfuturamanoob on 2008-08-21
> **Jessehk said:**
> Two lines intersecting in 3 dimensions is a linear algebra problem, not trigonometry. 

Generally you'd construct matrices and solve them using the Gauss-Jordan method.
See [here](http://en.wikipedia.org/wiki/Gauss-Jordan_elimination).
I want to check for 2 lines intersecting, in 2d. Not 3d. What is algebra or matrice? :confused: Or gauss method? Am I just stupid or is this too advanced maths for me?

---

### Post by hod139 on 2008-08-21
> **Jessehk said:**
> Two lines intersecting in 3 dimensions is a linear algebra problem, not trigonometry. 

Actually, segment-segment intersect testing would fall under the field of computational geometry.

> 
Generally you'd construct matrices and solve them using the Gauss-Jordan method.
See [here]("http://en.wikipedia.org/wiki/Gauss-Jordan_elimination").Not for segment-segment testing you wouldn't: [http://en.wikipedia.org/wiki/Line_segment_intersection](http://en.wikipedia.org/wiki/Line_segment_intersection)

---

### Post by hod139 on 2008-08-21
> **crazyfuturamanoob said:**
> I want to check for 2 lines intersecting, in 2d. Not 3d. What is algebra or matrice? :confused: Or gauss method? Am I just stupid or is this too advanced maths for me?

Linear algebra (not algebra which you will learn in high school) is a college level math that studies properties of vectors (and vector spaces) and matrices.  It's pretty advanced stuff.  The Gauss-Jordan method is a standard way for inverting a matrix, which is a required step in solving a system of equations.  Don't worry about any of this though, it isn't needed.

---

### Post by hod139 on 2008-08-21
> **crazyfuturamanoob said:**
> 
I have copied some code, like checking key presses, because I am noob in programming, and 
I can't make those things myself. And it is hard to learn, when I'm trying to learn it myself.

Of course it's hard, but that's part of learning.


> 
Edit: I tried to make that code to python from c++ but it doesn't work. It always returns 0, even if the lines cross.

Where did you get the C++ code from?  That codes does not look very reliable, since it fails in the case when the lines are perpendicular, which is exactly what you gave the function.  I suggest you read some of the articles I posted, and try and first understand the math.  Once you understand that, then you can start coding.  Blindly copying and pasting code is never a good idea.

---

### Post by Jessehk on 2008-08-21
> **hod139 said:**
> 
Not for segment-segment testing you wouldn't

I didn't know we were talking about segments. I should probably read the topic a bit more closely, eh? :)

---

