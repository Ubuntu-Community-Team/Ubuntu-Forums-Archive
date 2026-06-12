---
title: "Find the angle between two lines"
date: 2009-01-09
forum: Programming Talk
---

### Post by tom66 on 2009-01-09
Please could someone tell me how to calculate the angle of two lines which intersect? I don't mind if it involves trigonometry. Please see attached diagram (I need angle a; I know all coordinates). The programming language is Python, but any formula should be good. 

Thanks,
Tom

---

### Post by Krydahl on 2009-01-09
This might help:

[http://www.teacherschoice.com.au/Maths_Library/Trigonometry/solve_trig_SSS.htm](http://www.teacherschoice.com.au/Maths_Library/Trigonometry/solve_trig_SSS.htm)

---

### Post by dwhitney67 on 2009-01-09
Or this:  [http://www.devx.com/tips/Tip/33124](http://www.devx.com/tips/Tip/33124)

Basically, use Google to conduct your research, and use the Ubuntu Forum Programming section when you have programming problem.

---

### Post by Ruhe on 2009-01-09
You can use [Law of cosines]("http://en.wikipedia.org/wiki/Law_of_cosines"). 
This formula, but you'll need arccos of the right side of it:

[IMG]http://upload.wikimedia.org/math/4/d/8/4d8d17cae0a354660b66327415507651.png[/IMG]

You'll need to find lengths of sides of triangle. Then calculate arccos.

But I think there might be more fast method, using the coordinates of points.

---

### Post by tom66 on 2009-01-09
I did use Google before coming here. In fact, I tried the first eight results with no avail - I was throwing MathDomainErrors because of acos values being too big, or I was getting bizarre and incorrect angles. I'll give this law of cosines a shot, but at the moment, I'm having trouble. How do I translate the formulas given for the law of cosines into Python? Here's my best attempt, but when it gets an 'A' angle, it crashes and burns with a MathDomainError:

```

def length_of_line(x1, y1, x2, y2):
	# Calculates the length of a line in 2d space.
	return sqrt(pow(x1 - x2, 2) + pow(y1 - y2, 2))

def theta_triangle(p1, p2, p3):
	# Calculates the angles of a triangle and returns them as an array.
	# Requires three points, for each point of the triangle. Returns 
	# angles in degrees.
	#
	# With help from:
	# http://www.teacherschoice.com.au/Maths_Library/Trigonometry/solve_trig_SSS.htm
	
	# Get the lengths of our three sides. Store them as 'al', 'bl' and
	# 'cl'. We use these later in the code.
	al = length_of_line(p1[0], p1[1], p3[0], p3[1])
	bl = length_of_line(p3[0], p3[1], p2[0], p2[1])
	cl = length_of_line(p2[0], p2[1], p1[0], p1[1])
	
	if al == 0 or bl == 0 or cl == 0:
		return (90, 0, 0)
	
	# Find the largest side, and use this to find the largest angle;
	# which we'll attempt to calculate first. 
	large_angle = ''
	angle = 0
	
	if al > bl and al > cl:
		large_angle = 'A'
		angle = acos((-pow(al, 2) + pow(bl, 2) - pow(cl, 2)) / (2 * cl * bl))
	elif bl > al and bl > cl:
		large_angle = 'B'
		angle = acos((pow(al, 2) - pow(bl, 2) + pow(cl, 2)) / (2 * cl * al))
	elif cl > al and cl > bl:
		large_angle = 'C'
		angle = acos((pow(al, 2) + pow(bl, 2) - pow(cl, 2)) / (2 * al * bl))
	elif al == bl == cl:
		print "Line lengths are equal, returning 60 for all angles. "
		return (60, 60, 60)
	
	print "Large angle is " + large_angle + ", which is " + str(rad2deg(angle)) + " degrees"
	
	return (0, angle, 0)

```

---

### Post by Reiger on 2009-01-09
I've implemented a different algorithm for measuring 2d angles (it was a side-product for an algorithm to draw bisectors) once:

Here are the points (remember this is for bisector drawing, originally):
[list="1"]
[*]Obtain 3 input points A B C, such that the angle to measure/compute is defined as the angle ABC. (In other words, A and C are points on distinct line-segments which intersect at B.)
[*]Calculate a radius Z given as the average of |AB| and |BC| (distances between the points)
[*]Given this radius Z calcualte new points O and P such that O lies on the same line-segment as A does and |OB| = Z; and that P lies on the same line-segment as C does and |BP| = Z. (This is done by recalcuting distances over the X and Y axis using sine and cosine forumlae.)
[*]Calculate the point R which is given as the 'mean' of points O P or more formally: R(x) = (O(x) + P(x))/ 2 and R(y) = (O(y) + P(y))/2.
[*]Now the bisector of angle ABC is given as the line which intersects both B and R. Use a drawing algorithm to draw only n discrete subsegments of this line based on user input.
[/list]

So where does the solution to your problem drop out as a side-product?
[list="1"]
[*]Given these points A,B, O,P,R and B; then consider:
[*]The angle ORB is exactly 90 degrees (consider that |OB| = Z as is |BP|, recall you knowledge about Euclid geometry)
[*]The angle OBR is exactly half the angle OBP (By definition of a bisector.)
[*]The angle ABC is the same as the angle OBP. (Trivial, really...)
[*]Therefore by the formula for sine and arcsine we can calculate the angle OBP as 2 * arcsin(|RO|/Z);
[/list]

---

### Post by tom66 on 2009-01-09
I'm sorry, I'm not very good at maths extending into clever operators. What do two letters with vertical bars on the sides mean? I've seen this before, but never understood it. Also, how could this be implemented by using my input data, could you give some pseudocode? 

This is for my collision detection algorithm. It might be completely wrong, but I got the idea from a web site. Essentially, I initially assume a collision has occurred. I take two points at a time on the polygon and draw an invisible line to my object which I am checking; in this case, a space ship in my game. I then calculate the angles of the two intersections at the ship. If the angles total to about 360 degrees, then the object has intersected the polygon - otherwise it's impossible for a 360 degree total. I know how to do this, but the degree calculation is just throwing me off completely. Am I going at this the right way? Is it even possible to do collision detection this way?

---

### Post by Reiger on 2009-01-09
Ah, I suppose you're from the USA? The vertical bars are (widely) used to denote "absolute thingies" of all sorts, in geometry: distance if you use the German (European) 'symbol'. (Hence my "distance between points" clarification.)

|AB| = d(A,B). Or: distance between A and B, calculated using Pythagoras' nifty formula.

And for your case, excuse me for saying this... but you can do it more efficiently given a convex polygon (as in your diagram)
[list="1"]
[*]Store all corners of your polygon in order in some array/list or such like data structure. Store the center of your polygon as a special coordinate.
[*]For each line segment defined by a pair of consecutive corners in the data structure calculate wether or not the space ship is in bounds by calculating if the distance to the segment (drop a perpendicular!) is greater than the distance to the "far-side of the ship". Note that the first and last corner in the data structure form a segment too!
[/list]

---

### Post by tom66 on 2009-01-10
No, I'm from the UK. 

Well, I'm going to try and do something else, I'm going to attempt the separating axis algorithm to do polygon collision detection. It would seem significantly easier to implement, although it doesn't work with concave polygons, I probably won't have any of them - or I'll use a different algorithm

---

### Post by ProgramErgoSum on 2009-01-10
I got tired of not being able to find an easy way of exporting an Open Document Formula to a PNG. So, here is a PDF of what I suggest.

You can test it by taking a point on X axis and a point on Y axis so that the intersection point is (0,0) and angle of intersection is, of course, 90 degrees.

---

### Post by wmcbrine on 2009-01-10
> **Reiger said:**
> Ah, I suppose you're from the USA?For future reference, no one from the US says "maths" (with that final "s").

---

