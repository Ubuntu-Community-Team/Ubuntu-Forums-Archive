---
title: "Moving a polygon a distance at a specific angle"
date: 2009-01-05
forum: Programming Talk
---

### Post by tom66 on 2009-01-05
I have the following code:

```

def ship_move():
	global ship_angle, ship_speed, ship_pos
	
	rads = ship_angle * (pi / 180)
	
	mul_x = sin(rads)
	mul_y = cos(rads)
	
	print "X*: " + str(mul_x) + ", Y*: " + str(mul_y) + ", Ship Angle: " + str(ship_angle) + " deg (" + str(ship_angle_rads) + " rads)"
	
	speed = ship_speed
	
	# if rads <= 1: speed = +speed
	# else: speed = -speed
	
	ship_pos[0] += (-speed) * mul_x
	ship_pos[1] += (-speed) * mul_y

```

It is in python, but the 'formula' should apply to all programming languages. I am trying to move an object, specifically a polygon, a distance in pixels, at a specific angle. The angle can vary, and is not always a multiple of 90 or 45. It is converted from degrees into radians. 

I have tried sine and cosine but with no luck - the ship moves at angles, but it is: a) in the incorrect direction in some angles, and b) the angle modifies the speed, and some angles go faster than others. Tangent seems to converge to infinity and just flies all over the place when it reaches a 90 degree angle. 

Any help appreciated!

---

### Post by kjohansen on 2009-01-05
at first glance I think you want to use the cos for the x coord and the sin for the y coord.

tan is undefined at 90 that is why you get infinity.

---

### Post by tom66 on 2009-01-05
Thank you, that worked, but it required a slight fix. For anyone interested, I had to increase the angle by 90 which was then converted to radians and then sin/cos worked out as appropriate. 

Thanks!

---

