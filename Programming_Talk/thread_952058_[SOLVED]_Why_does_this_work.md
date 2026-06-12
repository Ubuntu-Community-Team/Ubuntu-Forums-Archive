---
title: "[SOLVED] Why does this work?"
date: 2008-10-18
forum: Programming Talk
---

### Post by snova on 2008-10-18
A break from the usual, "Why doesn't it work? How do I fix it? What's going on?" kind of question. :)

Recently my Physics textbook has gotten into vectors, particularly adding them. Since this is a rather repetitious task (and one I often make small mistakes in while punching numbers into the calculator) I wrote a short Python script to do so without erring.

But I have come across a pecularity of the trigonometric functions in the math module. The documentation says that they work in radians, so I converted appropriately- but only to find out that some of them appear to return in degrees, or take arguments in degrees and return in radians.

Why is this? Is this something to do with Python or (more likely, since the math module is supposed to be little more than a wrapper) the C functions underneath? Or is it something else entirely?

Anyway, here's the code I wrote. The class is probably overkill, but I might later give it the ability to perform other operations (like subtraction, but that doesn't seem to be requested in the book very often).

(The FromAddedVectors function could also stand to be something like __add__ or a global function, but I haven't bothered yet.)

```

#!/usr/bin/python

# Usage: <Angle A> <Magnitude A> <Angle B> <Magnitude B>

from sys import argv
from math import *

class Vector:
    @staticmethod
    def FromAngleAndMagnitude( name, angle, magnitude ):
        vec = Vector()
        vec.name = name
        vec.angle = angle
        vec.magnitude = magnitude
        [COLOR="#ff0000"]vec.x = cos( radians( angle ) ) * magnitude
        vec.y = sin( radians( angle ) ) * magnitude[/COLOR]
        return vec

    @staticmethod
    def FromComponents( name, x, y ):
        vec = Vector()
        vec.name = name
        vec.x = x
        vec.y = y
        [COLOR="Red"]angle = degrees( atan( y / x ) )[/COLOR]
        if x < 0:
            angle += 180
        elif y < 0:
            angle += 360
        vec.angle = angle
        vec.magnitude = sqrt( x * x + y * y )
        return vec

    @staticmethod
    def FromAddedVectors( name, a, b ):
        x = a.x + b.x
        y = a.y + b.y
        return Vector.FromComponents( name, x, y )

    def __str__( self ):
        return "Vector %s: Angle = %f, Magnitude = %f, X = %f, Y = %f" % \
               ( self.name, self.angle, self.magnitude, self.x, self.y )

################################################################################

A = Vector.FromAngleAndMagnitude( 'A', float( argv[1] ), float( argv[2] ) )
B = Vector.FromAngleAndMagnitude( 'B', float( argv[3] ), float( argv[4] ) )
C = Vector.FromAddedVectors( 'C', A, B )

print A
print B
print C

```

The odd bits are highlighted (obviously). Since it dumps state at the end and the variables *were* in degrees (checked against the answer I'm supposed to get in the book), I know that this isn't merely because I forgot to convert out of radians and thusly did not have to convert back into them for the next operation.

This is what I tested it with, and it matches perfectly with the answer in the book, every number:

```

xxxx@xxxxxxxx[05:54]:~/Desktop$ python addvec.py 150 1.2 250 3.2
Vector A: Angle = 150.000000, Magnitude = 1.200000, X = -1.039230, Y = 0.600000
Vector B: Angle = 250.000000, Magnitude = 3.200000, X = -1.094464, Y = -3.007016
Vector C: Angle = 228.444679, Magnitude = 3.216579, X = -2.133695, Y = -2.407016

```

Review would be nice, but I'm more interested in finding out why this works as expected.

Edit: Just in case, this is *not* a homework question (although technically it's all homework). I already know how to do this, I just wonder why my program gives correct results.

Edit 2: Just to clarify what the odd thing is, it's that cos and sin are returning values in degrees and atan is taking an argument in degrees when the documentation says they work in radians. I am entirely certain (unless you can prove me wrong) of these units.

---

### Post by Can+~ on 2008-10-18
The question is about general mathematical cosine and sine function, or only in python? And python return value of this functions is a float between -1 and 1, just like real sine and cosine work.

Remember the Goniometric circle:
[IMG]http://img.photobucket.com/albums/v517/CanXp/cosine.png[/IMG]

The magnitude of the vector is given and it's equal to the hypotenuse, so:

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot1-1.png[/IMG]

(same goes for cosine).

(edit: I love LaTeX :D)

---

### Post by snova on 2008-10-18
The question is why the Python math libraries are acting as they are. The numbers I get out from them match exactly with what's in my book- which uses degrees.

The question is why they output (and sometimes takes input as) degrees, when I thought these were supposed to work in radians.

So, yes, it's a Python question.

---

### Post by Can+~ on 2008-10-18
> **snova said:**
> The question is why the Python math libraries are acting as they are. The numbers I get out from them match exactly with what's in my book- which uses degrees.

The question is why they output (and sometimes takes input as) degrees, when I thought these were supposed to work in radians.

So, yes, it's a Python question.

Sine and cosine always return Real numbers between -1* and 1. The Radian or Degrees thing is just for the arguments, since both units are equivalent:

*1 [degree] = PI / 180 [radians]

1 [radian] = 180 / PI [degrees]

*edit: fixed the degrees/radians proportion, just a little brain fart
*edit2: another mistake.

---

### Post by pp. on 2008-10-18
It has been some time since I used trig functions. However, I was under the impression that sin(), cos() and tan() each took an angle as argument and returned a ratio, while their inverse function took a ratio and returned an angle. Further, I 'd think that atan() was the inverse of tan().

---

### Post by snova on 2008-10-18
Phft. Duh! :oops:

That was the glaringly obvious answer I was looking for. Somehow it escaped me that they don't return angles at all, but the lengths of the sides...

Sorry for wasting forum space! That was silly.

---

### Post by meanburrito920 on 2008-10-18
I think the problem is that the docs are a bit confusing. for example: 
```

    cos(...)
        cos(x)
        
        Return the cosine of x (measured in radians).

```
means that x is measured in radians (which it is) not that the value returned is measured in radians.

---

### Post by snova on 2008-10-18
Perhaps it is ambiguous, but I should have realized that it wasn't supposed to return an angle in this particular case. It wasn't a problem with the math library, but with my observation skills. It was silly, as things often are.

---

### Post by ad_267 on 2008-10-18
Just a side note, you might want to check out the numpy and scipy modules for python.

---

### Post by MONODA on 2008-10-19
> (edit: I love LaTeX )
you made THAT with LaTeX!?!?!? *launches TexMaker*

---

