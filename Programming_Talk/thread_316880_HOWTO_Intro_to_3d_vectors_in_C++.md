---
title: "HOWTO: Intro to 3d vectors in C++"
date: 2006-12-11
forum: Programming Talk
---

### Post by Mickeysofine1972 on 2006-12-11
Hi 

Theres yet another great HOWTO on The Ubuntu Games Developer Resource Wiki!

Well done again to Wybiral for another eye opener!

Mike

---

### Post by hod139 on 2006-12-11
Cool. I can't wait for my semester to be over so I can start writing some stuff instead of just commenting!!

Comment 1.  Why not use a templated class so the types are not restricted to floats?

Comment 2.  There is a neat performance trick to scalar division.  Since division is super slow, you can compute the division once and then do many multiplications
```

vec3 operator/ (float b)
{
assert(b != 0)
float scalar = 1. / b;
return vec3(x*scalar, y*scalar, z*scalar);
}

```Comment 3. Your cross product assumes a right handed coordinate system.  This is fine for OpenGL but will break for left handed systems (e.g. DirectX). Why anyone would want to use a left-handed system for game programming is another question, but some do.

Comment 4.  I assume a matrix class is coming soon, and just wanted to see if you are aware of the Simple Vector Library ([SVL]("http://www.cs.cmu.edu/%7Eajw/doc/svl.html")).  It's a really nice light weight vector/matrix class with general vector matrix classes and also specializations for size 2,3, and 4 vectors and size 2x2, 3x3, and 4x4 matrices.  It is even made to [work with OpenGL]("http://www.cs.cmu.edu/%7Eajw/doc/svl.html#opengl").

**Edit: **Comment 5.  Just thought of another one.  Some people are probably going to suggest that you make your member functions non-friend non-member functions.  I tend to flip back and forth, but non-friend non-member functions tend to provide better data encapsulation.

---

### Post by Mickeysofine1972 on 2006-12-11
All in good time my friend ;-)

Mike

---

### Post by Wybiral on 2006-12-12
In response to hod's comments:

All good suggestions, but once again I didn't want to confuse anyone with extra code. But thanks for the suggestions!

---

### Post by Mickeysofine1972 on 2006-12-12
Hey - we already thought of that dude!

You just have to wait for the story to unfold hehe!

Mike

---

### Post by Wybiral on 2006-12-12
Btw, that vector class can easily work with OpenGL with a slight modification just use a three dimensional array instead of (x, y, z) and call it something like "vec" something like...

```

class vec3 {
    public:
        float vec[3];

```

Then supplement the x,y,z with the appropriate array element. Then you can use it with OpenGL in commands like...

```

glVertex3fv(myVector.vec);

```

instead of...

```

glVertec3f(myVector.x, myVector.y, myVector.z);

```

---

### Post by hod139 on 2006-12-12
> **Wybiral said:**
> Btw, that vector class can easily work with OpenGL with a slight modification just use a three dimensional array instead of (x, y, z) and call it something like "vec" something like...

I never doubted it could, sorry if my statement sounded that way.  I only mentioned SVL because it does everything we need, has a matrix class (which I assume you were planning), is very lightweight (as opposed to say Boost), and is well tested.  Part of the beauty of open source is code reuse.

---

### Post by Wybiral on 2006-12-12
Well, I might look into for myself, but the main point of this tutorial was to teach people about vector mathematics, the class is just there to show them how you might implement those functions in C++. Also, for a lot of things, I like to do them myself.

I know it's easier to use an already made library, but for personal satisfaction, I just prefer trying to write it on my own. It's also easier for me to use/add my own class's to my program because I don't have to read a manual on it or anything because I know all of it's odds and ends and how it does what it does.

---

### Post by Wybiral on 2006-12-13
Here's the same vector class written in python...

```

from math import sqrt
 
class vec3:
 def __init__(self, X, Y, Z):
  self.x=X
  self.y=Y
  self.z=Z
 def __add__(self, b):
  return vec3(self.x+b.x, self.y+b.y, self.z+b.z)
 def __sub__(self, b):
  return vec3(self.x-b.x, self.y-b.y, self.z-b.z)
 def __mul__(self, b):
  return vec3(self.x*b + self.y*b + self.z*b)
 def __div__(self, b):
  return vec3(self.x/b + self.y/b + self.z/b)
 def length(self):
  return sqrt(self.x*self.x + self.y*self.y + self.z*self.z)

def normalize(a):
 return vec3(a.x/a.length(), a.y/a.length(), a.z/a.length())
def dotproduct(a, b):
 return a.x*b.x + a.y*b.y + a.z*b.z
def crossproduct(a, b):
 return vec3(a.y*b.z-a.z*b.y, a.z*b.x-a.x*b.z, a.x*b.y-a.y*b.x)

```

---

### Post by Mickeysofine1972 on 2006-12-13
In the long run I think it would be nice to see a howto on using one or some of the Open Source Physics engines too as this is some thing that would be really cool

But as wybiral said, we want to make sure that, if you cant get hold of something like that, you can still have information available to guide you in making your own.

Actually, I'd just like to say that, after only 2 to 3 weeks of writting I am really over the moon with the progress the wiki is making.:-D 

Mike

---

### Post by hod139 on 2006-12-13
> **Mickeysofine1972 said:**
> In the long run I think it would be nice to see a howto on using one or some of the Open Source Physics engines too as this is some thing that would be really cool

The only open source physics engine I know of is Open Dynamics Engine ([ODE]("http://ode.org/")).  Remember a few weeks back when you asked me if complementarity was real?  Well, not only is it real but it is what ODE uses! From their [manual]("http://opende.sourceforge.net/wiki/index.php/Manual")[LIST]
[*] Simulation method: The equations of motion are derived from a Lagrange multiplier velocity based model due to Trinkle/Stewart and Anitescu/Potra.
[*] Contact and friction model: This is based on the Dantzig **LCP** solver described by Baraff, although ODE implements a faster approximation to the Coloumb friction model.[/LIST]Emphasis on LCP is mine.  LCP stands for Linear Complementarity Problem, and the approximation they make is because games need to run in real time and solving the unrelaxed model is too slow.  Instead they make some assumptions about friction that allow them to solve a smaller problem that is still "believable".  

Oh, what's really cool is that the Trinkle mentioned in the method quote is Jeff Trinkle, who is my advisor right now!

> 
But as wybiral said, we want to make sure that, if you cant get hold of something like that, you can still have information available to guide you in making your own.
I don't think this kind of information can come from simply looking at code.  In my opinion, this kind of information comes from years of formal education.

> 
Actually, I'd just like to say that, after only 2 to 3 weeks of writting I am really over the moon with the progress the wiki is making.:-D 
Agreed.  Very impressive.

---

### Post by Mickeysofine1972 on 2006-12-13
> **hod139 said:**
> I don't think this kind of information can come from simply looking at code.  In my opinion, this kind of information comes from years of formal education.

Agreed. But wasn't the point I was making. I was saying that our discussions and demonstrations of these ideas along with code examples of how we have interpreted them ourselves, will provide a bit more than just a theoretical discussion but also a bit more than a 'look at what I did' learning experience.

But seriously, thanks for the words of praise! we work very hard to do the best we can and I look forward to your thesis on comp.... comple...complementarity ;-)

Mike

---

### Post by POW R TOC H on 2009-03-04
I hope you don't mind, i modified your vec3 class for my project (I also used a template, so it can be used with any type you need). I changed normalization, dot and cross products to be member functions, so it all fits in a header file now. Also, I've added length2(), because I often need the length squared :)

Here it is, in case you find it useful :)

```

#ifndef _VEC3_H
#define _VEC3_H

#include <cmath>

template <class T>
class vec3 {
    public:
        T x, y, z;
        vec3(){x=0; y=0; z=0;}
        vec3(T X, T Y, T Z){
            x=X;
            y=Y;
            z=Z;
        }
        vec3 operator+ (vec3  b){return vec3(x+b.x, y+b.y, z+b.z);}
        vec3 operator- (vec3  b){return vec3(x-b.x, y-b.y, z-b.z);}
        vec3 operator* (T b){return vec3(x*b, y*b, z*b);}
		T operator* (vec3  b){return x*b.x + y*b.y + z*b.z;}
        vec3 operator/ (T b){return vec3(x/b, y/b, z/b);}
        vec3 cross    ( vec3  b){return vec3(y*b.z-z*b.y, z*b.x-x*b.z, x*b.y-y*b.x);}
		vec3 normalize()
			{
			T c = 1/ length();
			return vec3(x*c, y*c, z*c);
			}

        T length(){return sqrt(x*x + y*y + z*z);}
		T length2(){return x*x + y*y + z*z;}
		T* array(){ T arr[2] = {x, y, z}; return arr; }

};

#endif


```

---

