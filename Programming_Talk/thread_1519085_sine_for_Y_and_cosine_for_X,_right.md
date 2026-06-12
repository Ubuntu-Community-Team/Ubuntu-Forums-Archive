---
title: "sine for Y and cosine for X, right?"
date: 2010-06-27
forum: Programming Talk
---

### Post by kahumba on 2010-06-27
Hi,
while reading the OpenGL SuperBible (4th edition) I noticed the author uses the sine to get X and the cosine to get Y (in a for loop he uses these points/calculations to draw a circle, you know..).
But, I read earlier in other sources that it's the other way around: sine for Y and cosine for X, like here:
[http://en.wikipedia.org/wiki/Unit_circle](http://en.wikipedia.org/wiki/Unit_circle)

So which approach is the right one?
In my example both of them seem to work, just wanna make sure I'm not missing something.

---

### Post by Tony Flury on 2010-06-27
If all you are doing is drawing a complete circle - it does not matter which way round you use. If you are trying to calculate the exact x and y co-ordinates for a single angle (what would be described as translating polar to cartesian co-ordinates), then you need to get them right 

Sine = y/radius.
Cosine = x/radius
Tanget = y/x 

If you want to see the difference that getting them wrong (when drawing a circle) slow your loop down - you will see that the circle is drawn in an unusual way - where as if you have them the right way round the circle will be drawn in the way you might expect.

---

### Post by kahumba on 2010-06-27
Thanks a lot,
then I should stick with X for cosine and Y for sine.

edit: and the author should do the same, but that book's source code is actually quite buggy anyway.

---

### Post by MadCow108 on 2010-06-27
you should not stick to cos = x sin = y, as this depends on which angle you use and the "size" of the triangle (and the naming of your coordinate system).

use the more general definition:
cos = adjacent/hypotenuse
sin = opposite/hypotenuse
where opposite and adjacent are in respect to which angle you measure

these are valid in any **right angled** triangle (in euclidean space)

---

### Post by Tony Flury on 2010-06-27
Madcow - you are correct 

kahumba : My formulas only apply if : 

x and y axis are at right angles to each other - and the angle (that you take the sine and cosine of) is the angle measured from the x axis (normally the horizontal axis) to the radius.

Any other arrangement of axis - and angles, will change the ratios that you need to use.

---

### Post by trent.josephsen on 2010-06-27
> **MadCow108 said:**
> you should not stick to cos = x sin = y, as this depends on which angle you use and the "size" of the triangle (and the naming of your coordinate system).

use the more general definition:
cos = adjacent/hypotenuse
sin = opposite/hypotenuse
where opposite and adjacent are in respect to which angle you measure

these are valid in any **right angled** triangle (in euclidean space)

I prefer the "more general" definition, choosing cosine = C(t) and sine = S(t) such that dC/dt = -S(t) and dS/dt = C(t) for the initial conditions S(0) = 0 and C(0) = 1.  Or perhaps the definition sin(t) = Im[e^jt], cos(t) = Re[e^jt].  (I'm kidding.)

The unit circle definitions are more general than the right-triangle definitions, which only apply for positive, acute angles.  But hey, use whatever helps you remember.

---

### Post by DanielWaterworth on 2010-06-28
> **trent.josephsen said:**
> Or perhaps the definition sin(t) = Im[e^jt], cos(t) = Re[e^jt].  (I'm kidding.)

Or even 1/2(e^jt+e^-jt) for cos and 1/2j(e^jt-e^-jt) for sin. (In truth though, they are useful when you have powers of sin and cos).

---

### Post by Bachstelze on 2010-06-28
> **trent.josephsen said:**
> I prefer the "more general" definition, choosing cosine = C(t) and sine = S(t) such that dC/dt = S(t) and dS/dt = C(t) for the initial conditions S(0) = 0 and C(0) = 1.

Surely you meant dC/dt = -S(t). ;)

---

### Post by trent.josephsen on 2010-06-28
> **Bachstelze said:**
> Surely you meant dC/dt = -S(t). ;)
Of course. :) (Fixed in the original.)

---

