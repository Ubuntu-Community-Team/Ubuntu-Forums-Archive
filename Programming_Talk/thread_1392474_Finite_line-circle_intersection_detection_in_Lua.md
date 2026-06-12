---
title: "Finite line-circle intersection detection in Lua"
date: 2010-01-28
forum: Programming Talk
---

### Post by Nevon on 2010-01-28
I have a **finite** straight line somewhere. I know its ending point coordinates. I also have a circle of which I also know the coordinates (of the center) and also the radius.

Now I need to figure out whether or not the circle intersects the line somewhere. I've found several examples online, but I haven't been able to get one to work properly. 

The simplest method I've found so far looks like this, but the syntax is unfamiliar to me, so I'm having problems reimplementing it:
```
bool IntersectCircleSegment(
    const Vector2& c,        // center
    float r,                            // radius
    const Vector2& p1,     // segment start
    const Vector2& p2)     // segment end
{
    Vector2 dir = p2 - p1;
    Vector2 diff = c - p1;
    float t = diff.Dot(dir) / dir.Dot(dir);
    if (t < 0.0f)
        t = 0.0f;
    if (t > 1.0f)
        t = 1.0f;
    Vector2 closest = p1 + t * dir;
    Vector2 d = c - closest;
    float distsqr = d.Dot(d);
    return distsqr <= r * r;
}
```

If someone could walk me through this code and explain it line by line (or something like that anyway) that would be great. I'm having some problems with the dot product method and I don't quite know how subtraction of vectors work. In my code I have the various coordinates (at least when I send them to the function) as their own variables, rather than lumped together in a vector.

---

### Post by Reiger on 2010-01-28
You have a problem of triangles. In order to see it, you should probably draw the lines on paper as I describe them to you:

Consider the line-segment AB, and the circle with centre M and radius r; then:
Consider the triangle AMB.

Determine if the d(M,AB) <= r. With d the distance function between &#8216;objects&#8217; (e.g. points, lines, line-segments).

In order to find the distance between line-segment AB and point M; consider how you would calculate the area of the triangle AMB:

Drop a perpendicular from M onto the line (straight lines are by definition infinitely large) of which AB is a segment, call the point at which it intersects P, let x = d(P,A); let h = d(P,M), let z = d(A,B).

Then to solve for h implies to solve for x; because:

Courtesy of Pythagoras' theorem:
h^2 = d(A,M)^2 - x ^2.
h^2 = d(B,M)^2 - (z - x) ^2 = d(B,M)^2 -z^2 -x^2 + 2zx

Therefore (subtract both definitions of h^2):
0 = d(A,M)^2 - x ^2 - d(B,M)^2 + z^2 + x^2 - 2zx
(Cross-out both -x^2 and +x^2):
0 = d(A,M)^2 - d(B,M)^2 + z^2 - 2zx

And so (group & divide by 2z):
x = (d(A,M)^2 - d(B,M)^2 + z^2) / 2z

Now, if x <=0 it means that d(M,AB) = d(M,A); if x >= z it means that d(M,AB) = d(M,B); if 0 <= x <= z  it means that d(M,AB) = h = sqrt(d(A,M)^2 - x^2).

You must further check that either d(M,A) and d(M,B) are >= r; otherwise there is no intersection but the entire segment AB is *inside* the circle.

---

### Post by Nevon on 2010-01-28
Wow, that is quite an extensive answer. One I wish I could fully comprehend.

With the help of a good friend, we were able to come up with a solution that looks like this:
```
function checkLineCollision(x1,y1,x2,y2, circlex, circley, circler)
    for n=0,1,0.001 do
        local x = x1 + ((x2 - x1) * n)
        local y = y1 + ((y2 - y1) * n)
        local dist = math.sqrt((x - circlex)^2 + (y - circley)^2)
        if(dist <= circler) then return true end
    end
end
```

It divides the line into a hundred points and checks each of those points to see if the distance from the point lower than the radius of the circle. It's not optimal, but there will never be more than one line to check, and probably less than 5 circles to check, so it should be fast enough.

---

### Post by Reiger on 2010-01-28
Here's a picture to help clarify what I mean:

[[IMG]http://img706.imageshack.us/img706/8343/linecircleintersect.th.png[/IMG]](http://img706.imageshack.us/i/linecircleintersect.png/)

Imagine playing a bit with the location of M and therefore P, notice how x would become larger/smaller. Similarly imagine what happens when you decrease the radius or reposition A and B.

EDIT: d(A,B) -x is z. Notice how in your scenario nearly everything is known (d(A,B) because you know A and B; similarly d(A,M) and d(B,M)); so all you really have to do is figure out h by figuring out x and do some sanity checks to see if the line segment AB is *inside* the circle.

---

