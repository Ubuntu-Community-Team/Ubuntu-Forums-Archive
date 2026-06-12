---
title: "The Language of Calculus"
date: 2009-02-05
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-02-05
I posted here because programmers tend to be math oriented

I am trying th find the volume of a vertical cylinder using integrals, my teacher told me to integrate the area of the horizontal slice (pi*r^2), but I want to find it by integrating the vertical slices and then rotating those around an axis (r*h around the y). I can do his way but if I could do my way too then I would be happier!

Think of his way as chopping a cucumber, and mine as the way an orange opens

---

### Post by CptPicard on 2009-02-05
Well, check this out.

[http://en.wikipedia.org/wiki/Solid_of_revolution](http://en.wikipedia.org/wiki/Solid_of_revolution)

IMO the "disc method" is much clearer in this case...

---

### Post by croto on 2009-02-07
If I understand correctly, you want to think of the volume of the cylinder as the sum of slices, as if it was a cake, right? Well, I would start from the volume of one of those infinitesimal slices. The height of the cake is h, the radius is r, and the slice extends an angle d_theta in radians. Since d_theta is very small, we can think of that slice as a triangular slice, and the volume is:

d_V = Area of triangle * h = (height of triangle) * (base of triangle)/2 * h
d_v = (r) * (r*d_theta)/2 * h

notice that it's important for d_theta to be expressed in radians so that the base of the triangle is r*d_theta. Then, all of those slices are represented for theta going from 0 to 2*pi. Let's add them up:

V = int_0^(2pi) h*r*r/2 d_theta = h*r^2/2 theta | (theta=2pi - theta=0) 
V = h*r^2/2 * 2pi = h*r^2*pi

---

### Post by haemulon on 2009-02-08
.

---

### Post by dburnett77 on 2009-02-08
> **Mr.Macdonald said:**
> I posted here because programmers tend to be math oriented

I am trying th find the volume of a vertical cylinder using integrals, my teacher told me to integrate the area of the horizontal slice (pi*r^2), but I want to find it by integrating the vertical slices and then rotating those around an axis (r*h around the y). I can do his way but if I could do my way too then I would be happier!

Think of his way as chopping a cucumber, and mine as the way an orange opens

R=Radius
h=height
theta=arc segment in radians.  There are 2*pi in a revolution

For one sheet, A=Area=
==R*h,
then multiply by the area formula for 360degrees, in radians.

So, A=R*h*theta*360deg/2pi=360*R*h/2, or thereabouts, I think...

---

