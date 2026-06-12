---
title: "tricky area problem"
date: 2009-07-15
forum: Programming Talk
---

### Post by manualqr on 2009-07-15
Here's a tricky problem I've run into while doing video analysis:

You have ***n*** dots on a bounded grid and have drawn a straight line between each dot to another. Assuming you know the coordinate pairs of each dot, what is the most efficient way to find the area of the polygon?

Now, your first instinct is to say "bah! I don't do homework for kids!". Well, I live in Kentucky - so school doesn't start for another month. Plus I've already taken AP Computer Science AB (and I got a 5 :D), so it's not like I'm doing any assignments ahead of time or anything.

Currently, I've solved this problem fitting a bounding box around the dots and iterating through it - keeping a count of all pixels that are within the constraints of the polygon. But this is ugly and kinda slow (when you have thousands of frames of video to process - and it's gotta be done in Matlab).

So if anyone has any cool ideas, let me know.

thanks

---

### Post by keplerspeed on 2009-07-15
If you know the co-ordinates of the dots, then I would break the polygon into triangles, and find the area of each triangle, using Area=0.5*ab*sin(c), or 0.5*height*base, just some trig etc. This should run quite fast.

---

### Post by manualqr on 2009-07-15
I don't think it's as easy as you make it sound.. The dots are in a very irregular pattern and finding triangles in it seems fairly difficult. Plus, between the dots - there is a lot of other data as well. Computers are bad at "eyeballing" solutions.

I'm going to try this instead and see if it actually works:
[http://www.wikihow.com/Calculate-the-Area-of-a-Polygon](http://www.wikihow.com/Calculate-the-Area-of-a-Polygon)

---

### Post by c0mput3r_n3rD on 2009-07-15
[http://www.mathopenref.com/polygonirregulararea.html](http://www.mathopenref.com/polygonirregulararea.html) That should help.  It basically suggests what the dude in the post above said.  I remember learning in school getting the areas of the triangles, or doing what you said which is drawing a box around it and doing it that way.  It's basically the only way it can be done because each side can be different and each interior angle can be different, so you have to turn it into something.  If the programming language you're using is slow at it, use another language that's better at number crunching such as C/C++.

Hope that helps.

---

### Post by croto on 2009-07-16
Do you care about the convex polygon that encloses the points (convex hull)? Or a possibly concave/convex polygon like this (where the "O"s are the initial points):

```

O*******O
  *     *
   O    *
  *     *
O*******O

```

If  it's the first case, there are very fast libraries (like qhull). I think it's even in a matlab toolbox. If it's the second case, I wouldn't know, but it looks more complicated.

---

### Post by JohnnySage50307 on 2009-07-16
> **manualqr said:**
> I don't think it's as easy as you make it sound.. The dots are in a very irregular pattern and finding triangles in it seems fairly difficult. 
 
Actually, "calculating the area of each triangle within a polygon *is* the most efficient way of solving for the area of any polygon, albeit normal or complex."  This comes from the lecture notes of Dr. Eliza Marai, professor and chair of the Computer Bio-Imaging and Graphical Analysis Lab at the University of Pittsburgh.  Between verticies, you can have an infinite amout of information, BUT it's all irrevelant information.
 
Pseudo-wise, here's a simple algorithm:

1. Select a point to mark black; mark all others white
2. Select another point and mark it grey
3. Set Total=0
4. While there are still white points:
--A. Select the nearest point to the grey one and mark that grey
--B. Calculate the area of that triangle (i.e. invoke law of cosines)
--C. Mark 1st grey point black.
--D. Add calculated triangle's area to Total.
 
At the end of the loop, Total will be the total area of the polygon.  And to calculate the area of a triangle using the Law of Cosines isn't terribly difficult either.  It's nowhere near as computationally intensive as applying a graphical rotation!

---

### Post by PandaGoat on 2009-07-16
I derived the following method sort of quickly, and I'm not sure how to easily verify that it works for all polygons or to see if I made a mistake; although, do not fret, it worked on a simple rectangle!

I can explain more if you'd like, but here is the simplification:

Using Green's theorem, we can easily find the area of a region given its boundary.  

Let &#947; be a connection between two points; that is, &#947; is a line, between two given points, that composes the polygon; I'm assuming you can easily iterate through all &#947;.  Now, you should iterate through all &#947;, maintaining a cumulative sum (the result will be the area).

The following will focus on what to do with each iteration. Let r' and r be the start and end respectively of &#947;. x' is the x component of r', y' is the y component of r', and so forth for r.  Add to the cumulative sum x' * (x - x') + .5 * (x - x') * (y - y').

It is important to maintain a sense of direction and be consistent--do not switch the direction mid-iteration.  There may be a way around this using absolute values. If the current iteration is &#947;', and your next iteration is &#947;, then the starting point of &#947; should be the end point of &#947;'.

After you go through each &#947;, the resulting sum will be the area of the polygon; it might be negative depending on which direction you went, so take the absolute value of the sum.  I hope this helps!

---

### Post by elbarto_87 on 2009-07-16
What about matlabs inbuilt "polyarea" function? Or is it not suited to your application?

---

### Post by manualqr on 2009-07-16
Thanks elbarto_87, I think I'll use the polyarea function - I didn't know it existed! I like this solution because of 2 reasons;
1. it's a one-liner
2. it returns the area of all polygons described by an array of vertices (meaning I can get the area of polygons even if the lines overlap)

I think matlab functions are written in C, so it should be speedy.

I like all of the other suggestions as well, and I'll look into them again if (when) I rewrite this in C.

thanks!

---

