---
title: "Which is closer to which, on a cirlce."
date: 2009-10-15
forum: Programming Talk
---

### Post by valros on 2009-10-15
I have an object that is following another through terms of rotating and going straight. It needs to know whether the desired rotation in comparison to its current rotation is faster reached by going clockwise or counter-clockwise.

        if (this.rotation - desired_rotation < 0){
            this.rotation = this.rotation + this.turning_speed*to_radians
        }
        else {
            this.rotation = this.rotation - this.turning_speed*to_radians
            }

The above works well until it tries to go from 359 degrees to 0 degrees(and vice versa), because it cant wrap around the circle, it thinks it has to go all the way around again clockwise to reach 0. How can this be solved?

---

### Post by lisati on 2009-10-15
> **valros said:**
> I have an object that is following another through terms of rotating and going straight. It needs to know whether the desired rotation in comparison to its current rotation is faster reached by going clockwise or counter-clockwise.

        if (this.rotation - desired_rotation < 0){
            this.rotation = this.rotation + this.turning_speed*to_radians
        }
        else {
            this.rotation = this.rotation - this.turning_speed*to_radians
            }

The above works well until it tries to go from 359 degrees to 0 degrees(and vice versa), because it cant wrap around the circle, it thinks it has to go all the way around again clockwise to reach 0. How can this be solved?

Homework?
It might be necessary to think outside the normal "limits" of 360 degrees while doing the calculation and then apply some modulus arithmetic. Will it hurt the calculation to have temporarily a measurement of, say, 361 degrees?

---

### Post by valros on 2009-10-15
No just a hobby, there's no problem with a temporary measurement.

---

### Post by valros on 2009-10-15
One limitation might be that this is being done in radians, and I would rather not convert to degrees and back again if possible.

---

### Post by Can+~ on 2009-10-15
Puting the things linear:

```

 0             PI              2PI
          x         y             
          [...y-x...]
..........]         [............
    x                  2PI - y
         

```

For each y >= x:

|y-x| yields the space in-between the two measures (clockwise)
x-y+2PI yields the space not in between the two measures (counter clockwise)

For example (in degrees for better understanding), if x = 0, and y = 359

```
y-x = 359
x-y+2PI = 0 - 359 + 360 = 1
```

If both x = y, then:

```
y-x = 0
x-y+2PI = 360.
```

Which makes a lot of sense.

I just came up with this, so I'm not sure how wrong/right I am.

---

### Post by wmcbrine on 2009-10-15
this.rotation %= 2 * PI

---

### Post by Arndt on 2009-10-16
> **valros said:**
> I have an object that is following another through terms of rotating and going straight. It needs to know whether the desired rotation in comparison to its current rotation is faster reached by going clockwise or counter-clockwise.

        if (this.rotation - desired_rotation < 0){
            this.rotation = this.rotation + this.turning_speed*to_radians
        }
        else {
            this.rotation = this.rotation - this.turning_speed*to_radians
            }

The above works well until it tries to go from 359 degrees to 0 degrees(and vice versa), because it cant wrap around the circle, it thinks it has to go all the way around again clockwise to reach 0. How can this be solved?

I'm not following the code completely, but what if you normalize all rotation differences to lie between -180 and 180 degrees? Then you have the sign there directly.

---

### Post by valros on 2009-10-21
Ok, just now revisiting this, stretching the circle onto a line is the way to go but the above solution only works when y >= x, this will not always be the case.

---

### Post by valros on 2009-10-21
```
    var desired_rotation = get_angle(this.x,this.y,x,y);

    if (Math.abs(this.rotation - desired_rotation) < this.turning_speed*to_radians){
        this.rotation = desired_rotation;
    }
    else {
        div5.innerHTML = this.rotation;
        cw_distance = desired_rotation - this.rotation;
        if (cw_distance < 0){cw_distance = cw_distance + Math.PI * 2;}
        if (cw_distance > Math.PI*2){cw_distance = Math.PI*2}
        ccw_distance = Math.PI*2 - cw_distance;

        div7.innerHTML = cw_distance;
        div8.innerHTML = ccw_distance;
        
        var applied_turn = true;
        if (cw_distance < ccw_distance){
            div6.innerHTML = 'clockwise';
            this.rotation = this.rotation + this.turning_speed*to_radians
        }
        else {
            div6.innerHTML = 'counter-clockwise'
            this.rotation = this.rotation - this.turning_speed*to_radians
            }
    }
```

This is what I have right now, it works to a point, however if the desired rotation is in the 3rd quadrant, then it begins to just keep subtracting from the rotation of the object, even passing up the desired rotation. Does this help anyone?

---

### Post by Can+~ on 2009-10-21
> **valros said:**
> Ok, just now revisiting this, stretching the circle onto a line is the way to go but the above solution only works when y >= x, this will not always be the case.

It's the same thing, but flipping the direction:

It would be simpler, to consider that, if the delta between the two, is less than PI (meaning that, the other direction would be bigger, because 2PI-delta would be larger than PI), then it needs to rotate, depending on the sign (for integers):

```
if | y - x | < 180º: (meaning that, rotating inside the circle is better)
  if y - x is positive (y > x, (y is further away)), x should move CW.
  if y - x is negative (y < x, (y is behind)), x should move CCW.
else if | y - x | == 0:
  it's already there
else:  (meaning that rotating in the other direction is the shorter distance)
  if y - x is positive (y > x), x should move CCW.
  if y - x is negative (y < x), x should move CW.
```

Now, if you're working with movement, in real numbers (floats), then you can't do | y - x | == 0, it will probably be non-zero, so you'll need to do | y - x | < epsylon, to compensate the floating point error.

Here's in python:

[PHP]def howmuch(mobile, fixed, epsylon=1.0):
	
	# 1: CW, -1: CCW.
	direction = 1
	
	delta = fixed - mobile
	
	# If it's on the same position
	if abs(delta) < epsylon:
		direction = 0
	else:
		direction = cmp(180, abs(delta))*cmp(delta, 0)
	
	return direction

# For prettier output
clock = {-1:"CCW", 0:"done", 1:"CW"}

print "It should be",clock[howmuch(0, 359.0)] # 359.0 <- 0 CCW
print "It should be",clock[howmuch(359.0, 0)] # 0 <- 359.0 CW

print "It should be",clock[howmuch(30, 60)] # 30 -> 60, CW
print "It should be",clock[howmuch(60, 30)] # 60 <- 30, CCW

print "It should be",clock[howmuch(30, 29.5)] # done[/PHP]

Using the [FONT="Courier New"]cmp(a, b)[/FONT] which yields -1 if a < b, and 1 if a > b.

---

### Post by valros on 2009-10-21
I tried Can+~'s solution, but its still thrown off by the move from 359 to 1 degrees and vice versa.

```

    if (Math.abs(desired_rotation - this.rotation) < Math.PI){
        if (desired_rotation - this.rotation > 0) {rotate_which_way = 'cw'}
        if (desired_rotation - this.rotation < 0) {rotate_which_way = 'ccw'}
        else {
            if (Math.abs(desired_rotation-this.rotation) < this.turning_speed*to_radians){
                this.rotation = desired_rotation
            }
            else {
                if (desired_rotation - this.rotation > 0){rotate_which_way = 'ccw'}
                if (desired_rotation - this.rotation < 0){rotate_which_way = 'cw'}
            }
        }
    }

```

---

### Post by PandaGoat on 2009-10-21
Let -1 denote clockwise, 1 denote counter-clockwise, and 0 denote either way.

Then the way you want to go is determined by sgn(sin(desiredAngle-currentAngle)). Where sgn is the signum function (the sign of the value).

You will have to define the sgn function yourself probably:

C/C++ code
```

int sgn (int n)
{
    return n == 0 ? 0 :(n > 0 ? 1 : -1);
}

```

---

### Post by valros on 2009-10-21
and the uncondensed c++ code?

---

### Post by valros on 2009-10-21
Wow. The entire time all I needed was:

```
    if (Math.sin(desired_rotation - this.rotation) > 0){
        this.rotation = this.rotation + this.turning_speed*to_radians;
    }
    else {
        this.rotation = this.rotation - this.turning_speed*to_radians
    }
```

Ok, solved. Thanks Panda

---

### Post by PandaGoat on 2009-10-21
I didn't want to edit my previous post since you are currently online in case you do not see my edit, so:

You should consider an implementation where you calculate the amount of angle to rotate through:

```

int amountToRotate = abs(currentAngle - desiredAngle);
int rotate = sgn(sin(desiredAngle-currentAngle)) * amountToRotate;
currentAngle += rotate/numberOfTicks;

```

This will handle rotating by nothing if desiredAngle equals currentAngle.

[EDIT] I didn't see your last post.  I did not try to comprehend if how you implemented this works in all cases, so if it works ignore this post :).

---

### Post by Can+~ on 2009-10-21
> **PandaGoat said:**
> I didn't want to edit my previous post since you are currently online in case you do not see my edit, so:

You should consider an implementation where you calculate the amount of angle to rotate through:

```

int amountToRotate = abs(currentAngle - desiredAngle);
int rotate = sgn(sin(desiredAngle-currentAngle)) * amountToRotate;
currentAngle += rotate/numberOfTicks;

```

This will handle rotating by nothing if desiredAngle equals currentAngle.

[EDIT] I didn't see your last post.  I did not try to comprehend if how you implemented this works in all cases, so if it works ignore this post :).

I'm also not sure if valros' solution will work.

I didn't think on using sin() for the angle (duh), but there's a problem in this line:

[PHP]int rotate = sgn(sin(desiredAngle-currentAngle)) * amountToRotate;[/PHP]

Because you (in the previous post) defined -1 as CW, this will go exactly in the opposite direction.

And this still needs to check for floating point error, otherwise, it will keep "oscillating" when it reaches the desired angle.

---

