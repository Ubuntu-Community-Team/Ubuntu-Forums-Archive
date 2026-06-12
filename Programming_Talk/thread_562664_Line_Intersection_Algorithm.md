---
title: "Line Intersection Algorithm"
date: 2007-09-29
forum: Programming Talk
---

### Post by Lster on 2007-09-29
Hi all

I am following a tutorial at TopCoder and have successfully produced a function that finds if and where two straight lines cross. The algorithm appears to work (although I've only tested it a bit), but I really don't understand the first step. Here is the tutorial address: [http://www.topcoder.com/tc?module=Static&d1=tutorials&d2=geometry2](http://www.topcoder.com/tc?module=Static&d1=tutorials&d2=geometry2)

... Problem is fixed. See next post! ...

This is where I am stuck! I can't see how that works. So basically, I'm just asking for the proof of the algorithm. This would be really useful as I have not been able to find a simple explanation on the internet or in any of my text books. I also tried deriving/ proving it myself but I am getting nowhere!

Thanks,
Lster

PS: Please post if you need any more information.

---

### Post by aks44 on 2007-09-29
> **Lster said:**
> Apparently we need the values of A, B and C in the equation Ax+By=C. And if we have 2 points (x1, y1) and (x2, y2)

Let's start easy, and find D & E in y=Dx+E (I'll get to your equation Ax+By=C later).

[img]http://img165.imageshack.us/img165/7826/reprevm0.png[/img]

For now, let's assume we are in the general case: dx!=0 and dx'!=0 (ie. x1!=x2 and x1!=0)

D (the "slope") = dy / dx = dy' / dx'

D = (y2-y1)/(x2-x1) = (y1-E)/(x1-0)

we end up with

D = (y2-y1)/(x2-x1)
E = y1 - x1.(y2-y1)/(x2-x1)

ie.
y = x.(y2-y1)/(x2-x1) + ( y1 - x1.(y2-y1)/(x2-x1) )
or
x.(y2-y1)/(x2-x1) - y + ( y1 - x1.(y2-y1)/(x2-x1) ) = 0

Now, just multiply everything by (x2-x1) :

x.(y2-y1) - y.(x2-x1) + ( y1.(x2-x1) - x1.(y2-y1) ) = 0

What you're looking for is: Ax+By=C or Ax+By-C=0
Well, you already have it:
A = y2-y1
B = x1-x2
-C = y1.(x2-x1) - x1.(y2-y1)
so C = x1.A + y1.B

The advantage of the line equation they chose is that, contrary to y=Dx+E they don't have problems when dx (or dx') is zero since they don't need divisions.

Now, finding the intersection of two lines is as easy as solving that pair of equations

A1.x + B1.y - C1 = 0
A2.x + B2.y - C2 = 0


I'll let you do the rest of the maths... ;)

Hope this helps, even if that's not a "formal" proof...

---

### Post by Lster on 2007-09-29
Thank you! That was brilliant and I understand it all. Have you considered (or are you?) becoming a maths teacher ;). You would be better than many of the maths teachers at my college...

---

### Post by Lster on 2007-09-29
Just a quick update. I've now finished tutorial and am fine with it all - woohoo!

---

### Post by aks44 on 2007-09-29
> **Lster said:**
> Have you considered (or are you?) becoming a maths teacher

No way... I tend to use too many "shortcuts", they are OK as far as programming goes (when everyone "knows" something, why bother with a proof?) but "correct" maths are too picky for me.


FWIW, there are too many holes in my above explanation to make it a correct proof, but I can't be bothered with filling the gaps. ;)

---

