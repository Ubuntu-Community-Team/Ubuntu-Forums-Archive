---
title: "Python Help, Variables"
date: 2010-02-23
forum: Programming Talk
---

### Post by Linux000 on 2010-02-23
Hi,

I am using the graphics.py libary from [http://mcsp.wartburg.edu/zelle/python/](http://mcsp.wartburg.edu/zelle/python/)
which contains a "rectangle" function, this rectangle needs a name so the syntax is "foo = retangle(point1, point2)", I have another varible which changes, so something like this
```
	
             for y in range(20):
			bnum = y*20
			bnum = Rectangle(point1, point2)

```
As you can assume, the rectangle "bnum" is created, however I would like the name to be the product of y*20 (assuming it doesn't override 20 itself). How would I do that?

---

### Post by crlang13 on 2010-02-23
Why do you want the name to be the product of y and 20?  

Because I'm thinking you set some stuff up with pointers and rather than have your rectangle named "y*20" you could have it point to that value...

I'm not terribly familiar with python, so that's about as specific as I can get!:P

---

### Post by Linux000 on 2010-02-23
The point is to draw a grid on a screen and I need to reference the rectangle later, the easiest way to do that is number them, I am trying to program Conway's game of life. Thanks for the help.

---

### Post by Simon17 on 2010-02-23
If I'm understanding you right, you don't want to do that.

Just put all the rectangles in an array.

---

### Post by kostkon on 2010-02-23
You could store them in a dictionary, e.g.:
```
rectangles = {}
for y in range(20):
    bnum = y*20
    rectangles[bnum] = Rectangle(point1, point2)
```

---

### Post by crlang13 on 2010-02-23
I see...

Another way to do it, although it may not be terribly efficient is to use matrices.

So I'm assuming you are making 20 rectangles?

Make your rectangles and a 20 x 2 matrix, with each row being the points of a rectangle, something like:

[point1_r1 point2_r1;
point1_r2 point2_r2...
... point1_r20 point2_r20]

Then to access the rectangle again, you can re-create it by accessing the appropriate cells in your matrix.

OR, if this is possible, you can make a 1 x 20 matrix with each cell being a rectangle.

---

### Post by Linux000 on 2010-02-23
I don't know why that didn't cross my mind, thanks for the help, and yes the array works.

---

