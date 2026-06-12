---
title: "Game Design. Circular Surface Deflection"
date: 2012-06-12
forum: Programming Talk
---

### Post by Dr Belka on 2012-06-12
I'm making a simple 2D game. It's coded in Java.  

In the game, there is a planet and objects that move around the planet according the force of gravity.  I've got the gravity working but I just can't wrap my mind around how to deal with the object to planet collisions.  

When one of the moving objects strikes the surface of the planet, I want it to properly deflect based on the angle at which it struck.  I just can't wrap my brain around how to do this.  

Something to work with:

```


class Planet {

public int getX();
public int getY();
public int getRadius();

}

class MovingObject {

public int posX;
public int posY;
public float velX;
public float velY;

}

class Physics {

public static float getDistane(int x1, int y1, int x2, int y2);
public static float getAngle(int x1, int y1, int x2, int y2);

}

Planet p;
MovingObject s;
.....;
// if collision
if (Physics.getDistance(s.posX, s.posY, p.getX(), p.getY()) < p.getRadius) {
// deflection occurs
}



```


Any help would be much appreciated.  Thank you.

---

### Post by Vaphell on 2012-06-12
arctan delta(y)/delta(x) -> angle of movement vector

arctan (yi-y0)/(xi-x0) -> angle created by r anchored in x0,y0 in the point of impact xi,yi

calculate the difference and mirror that angle on the other side of radius. Use this newly created angle to calculate new movement vector

... or something

---

### Post by Dr Belka on 2012-06-12
Thank you so much for your reply.

> **Vaphell said:**
> arctan delta(y)/delta(x) -> angle of movement vector

Yup, that's what Physics.getDistance() does.

> **Vaphell said:**
> arctan (yi-y0)/(xi-x0) -> angle created by r anchored in x0,y0 in the point of impact xi,yi

And that's what Physics.getAngle() does.

> **Vaphell said:**
> calculate the difference and mirror that angle on the other side of radius. Use this newly created angle to calculate new movement vector

... or something

And this is what I'm trying to figure out how to do.

---

### Post by Dr Belka on 2012-06-12
Here's a picture showing what I would like to happen.  

[ATTACH]219598[/ATTACH]

---

### Post by Vaphell on 2012-06-12
a - movement angle
b - radius angle
----------------
c = (180+a)-b
n = b-c = 2b-180-a

let's check it: from the picture, a is roughly -80deg (object moving down), b 30deg
c = 70deg
n = 30deg-70deg = -40deg which is what you approximately see

---

### Post by Dr Belka on 2012-06-14
> **Vaphell said:**
> a - movement angle
b - radius angle
----------------
c = (180+a)-b
n = b-c = 2b-180-a

let's check it: from the picture, a is roughly -80deg (object moving down), b 30deg
c = 70deg
n = 30deg-70deg = -40deg which is what you approximately see

Thank you so much.  I'm going to try this out

---

### Post by muteXe on 2012-06-15
Isn't this an object bounding off a flat surface?

---

### Post by Vaphell on 2012-06-15
doesn't matter (unless you are writing some serious physics simulator). You can assume that deflection off the circular surface = deflection off the tangent plane in the point of contact (dashed line on picture)

---

### Post by muteXe on 2012-06-15
yea exactly. not sure what the confusing picture's all about then. Or even the mention of a sphere come to think of it.

---

