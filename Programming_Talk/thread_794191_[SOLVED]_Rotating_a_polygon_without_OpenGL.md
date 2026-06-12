---
title: "[SOLVED] Rotating a polygon without OpenGL"
date: 2008-05-14
forum: Programming Talk
---

### Post by Zeotronic on 2008-05-14
C++/SDL/Trigonometry: I have been working on a program for quite some time now... presently, I am trying to figure out how to rotate a polygon outside of OpenGL (as I am using SDL for rendering)... I know that I could do this with trigonometry, but the last piece I think I need to do this is finding the degrees of an angle based on any combination of the opposite, adjacent, and hypotenuse (as the angles are all unknown, save for the 90* one)... and I cannot, for the life of me, figure out how to do it. I've looked through several math books, and on the internet... and though I have probably stumbled right past the answer, I could not understand it... so quite simply, I need someone to *give* it to me. **Does anyone know how to find a triangle's angle without knowing the other two angles? OR: Does anyone know how to rotate a (2D) polygon without OpenGL?**

---

### Post by Lux Perpetua on 2008-05-14
It's simple trigonometry. If the legs are A and B and the hypotenuse is C and the  angle between sides A and C is t, then:

A/C = cos(t), or t = arccos(A/C)
B/C = sin(t), or t = arcsin(B/C)
B/A = tan(t), or t = arctan(B/A)

About rotating the polygon: to rotate a point (x, y) by t radians counterclockwise about the origin (0, 0), the transformed coordinates (x', y') can be computed by:

x' = cos(t)*x - sin(t)*y
y' = sin(t)*x + cos(t)*y

To rotate the entire polygon, you would just rotate each vertex. To rotate about a different point (c, d) (not necessarily (0, 0)), replace (x, y) and (x', y') respectively by (x-c, y-d) and (x'-c, y'-d) in the above formula.

---

### Post by Zeotronic on 2008-05-14
> It's simple trigonometry. If the legs are A and B and the hypotenuse is C and the angle between sides A and C is t, then:

A/C = cos(t), or t = arccos(A/C)
B/C = sin(t), or t = arcsin(B/C)
B/A = tan(t), or t = arctan(B/A)
Yes... simple trigonometry... that explains why I couldn't find it anywhere... Sure it *is* simple... but I didn't see anything about arctan (and the others) anywhere. *scrolls down another open tab* oh wait... there it is. But seriously though, I don't remember getting taught this in trigonometry. I swear I was paying attention!
> About rotating the polygon: to rotate a point (x, y) by t radians counterclockwise about the origin (0, 0), the transformed coordinates (x', y') can be computed by:

x' = cos(t)*x - sin(t)*y
y' = sin(t)*x + cos(t)*y

To rotate the entire polygon, you would just rotate each vertex. To rotate about a different point (c, d) (not necessarily (0, 0)), replace (x, y) and (x', y') respectively by (x-c, y-d) and (x'-c, y'-d) in the above formula.
Your math is interesting... my math is considerably different...

radius=sqrt(vertex.x^2+vertex.y^2)

angle=atan(vertex.x/vertex.y)

angle+=rotation

vertex.x=cos(angle)*radius
vertex.y=sin(angle)*radius

Which would be proformed onto each vertex... sadly... neither your math, nore my math... are displaying the proper results. My math renders the polygon folded, and your math is flattening it after enough rotation... but I may have translated it wrong.

---

### Post by Lux Perpetua on 2008-05-14
Post the code. 

But preemptively: you need to be careful about atan. The value of atan(x) is always between -pi/2 and pi/2; this can only represent angles in the first and fourth quadrants! Your library ought to have a variant of atan that takes two arguments, y and x, and essentially computes the arctangent of y/x but puts it in the correct quadrant. (In C, this function is double atan2(double y, double x).) 

I would still prefer my method to yours, since it is computationally simpler.

---

### Post by Zeotronic on 2008-05-14
Ok, yea, C++ also has atan2, so now my code is working, but as you have stated, I would also prefer your math, as it is simpler... I am trying to keep my game compatable for a platform with a low processing power, so I would prefer to waste not.

In the case of your math... this is how I have translated it into my program:

vertex.x=cos(rotation*dtr)*vertex.x-sin(rotation*dtr)*vertex.y;
vertex.y=sin(rotation*dtr)*vertex.x+cos(rotation*dtr)*vertex.y;

rotation is in degrees, and you said it needed to be in radians right? So I multiplied it by dtr (which I defined to be the proper value to convert degrees to radians, hence DTR). vertex.x/y are the x/y position of the vertex, no suprise there, and the rotation of the polygon is caclulated with a fresh copy of the polygon every step... so the effects of this modification don't add up.

---

### Post by Lux Perpetua on 2008-05-14
You're updating vertex.x too soon (very common mistake). The update for vertex.y is supposed to use the old value of vertex.x, but you've already overwritten it with the new one.

---

### Post by Zeotronic on 2008-05-14
Oh... DUH!

---

### Post by Jonny D on 2008-09-15
Hey, I just added some functions to Sprig that do this.  They're not in the library yet, but you can still find them on the Sprig page:
[http://pubpages.unh.edu/~jmb97/SPriG.html](http://pubpages.unh.edu/~jmb97/SPriG.html)

---

