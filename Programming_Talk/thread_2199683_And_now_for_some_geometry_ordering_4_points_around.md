---
title: "And now for some geometry: ordering 4 points around a quadrangle"
date: 2014-01-15
forum: Programming Talk
---

### Post by ofnuts on 2014-01-15
Simply said: a user gives me 4 pairs of coordinates for 4 points that are the vertices of a quadrangle in any order. How can I identify the 4 corners (top left, top right, bottom left, bottom right)? I'll be dealing with only convex quadrangles and I have seen [this](http://stackoverflow.com/questions/1315921/identifying-the-corners-of-a-polygon-in-2d-space).

---

### Post by spjackson on 2014-01-15
Doesn't this simple method work if you know that the quadrilateral is convex?

Sort points ascending by y value. 1st two are "bottom". 2nd two are "top". For the tops then the bottoms, use the x value to decide which is "left" and "right".

---

### Post by Vaphell on 2014-01-15
does labeling points make any sense? What is top-left in case of a square rotated 45deg?

asking to clarify: is the input an unordered list of points and the goal is to establish the order of vertices that will create a convex quadrilateral?

In a convex shape diagonals have to cross, so you need to find pairs that create crossing segments. Once you have them, alternate, eg A1->B1->A2->B2

---

### Post by ofnuts on 2014-01-15
> **spjackson said:**
> Doesn't this simple method work if you know that the quadrilateral is convex?

Sort points ascending by y value. 1st two are "bottom". 2nd two are "top". For the tops then the bottoms, use the x value to decide which is "left" and "right".

No :)

[IMG]http://i.imgur.com/nRCnIlH.png[/IMG]

---

### Post by ofnuts on 2014-01-15
> **Vaphell said:**
> does labeling points make any sense? What is top-left in case of a square rotated 45deg?

asking to clarify: is the input an unordered list of points and the goal is to establish the order of vertices that will create a convex quadrilateral?

In a convex shape diagonals have to cross, so you need to find pairs that create crossing segments. Once you have them, alternate, eg A1->B1->A2->B2

That's a start,  it will put the points in some perimeter order but that won't tell me which one is at top left, for instance, and if the top right is the one after the top left or the one before (ie I can't tell if this generates a clockwise or counter-clockwise perimeter). However, I think I can walk the list until I find a point where the next has a bigger X and the previous has a bigger Y, and if I don't find it, I can reverse the list I search again. Then I have the top left one.

For a full background: this is for a Gimp script. The user specifies 4 points by drawing a path, and the script covers the quadrangle using an existing rectangular image with a perspective transform. This transforms requires, in a specific order, the 4 corners of the quadrangle that correspond to the 4 corners in the image. The problem is that the user hasn't got much control over the order of the points in the path. If he is reasonably careful things could be OK, but in the general case they won't be, so I prefer having a good way to guess the right order (an output a message otherwise).

---

### Post by spjackson on 2014-01-15
> **ofnuts said:**
> No :)

[IMG]http://i.imgur.com/nRCnIlH.png[/IMG]

That is a valid counter example if you think that B is "top left". By what definition do you deduce that B is "top left"? Consider a "diamond" shape where A and D have the same x value, and B and C have the same y value. In that case, what labelling would be correct? (By which I mean for example A is at 1,1 B is at 0,0 C is at 2,0 and D is at 1,-1.)

---

### Post by ofnuts on 2014-01-15
> **spjackson said:**
> That is a valid counter example if you think that B is "top left". By what definition do you deduce that B is "top left"? Consider a "diamond" shape where A and D have the same x value, and B and C have the same y value. In that case, what labelling would be correct? (By which I mean for example A is at 1,1 B is at 0,0 C is at 2,0 and D is at 1,-1.)

I call B "top left" because I don't see any other point that could be labelled as "top left".  B and D are more on the left than A and C, so their are the ones on the left, and B is above D so it is the top one. Of course we can decide that the is no top left vertex...

---

### Post by trent.josephsen on 2014-01-15
What about [this](http://www.wolframalpha.com/input/?i=x+%3C+3+and+y+%3C+x+%2B+3+and+y+%3E+x+-+1+and+y+%3E+0)?

Here's the algorithm I thought of:
0_ Using the knowledge that the polygon is convex, order the points so you can tell which ones are adjacent.
1_ Determine the point with the greatest y-value. Call it P. This is one of your upper corners.
2_ Draw lines from P to both its neigbors. Take the endpoint of the line that has the *shallower angle* (closer to horizontal), and call it Q.
3_ If P's x-value is less than Q's x-value, then P is your top left vertex and Q is top-right. If P's x is greater than Q's, exactly the opposite.
4_ The other points fall out from the ordering.

---

### Post by Vaphell on 2014-01-15
no matter how you slice it, it's ambiguous. With that algorithm you can have a [top-left that has the lowest y]("http://www.wolframalpha.com/input/?i=x+%3C+3%2B0.2*y+and+y+%3C+x+%2B+3+and+y+%3E+x+-+1+and+y+%3E+0.2*x"). If you did the same algorithm but from the bottom you'd get something else (this point would be bottom-* by definition). You could also say by looking at the picture that the edge connecting the highest and the lowest point should be top-left to bottom-left
Square rotated 45deg obviously has 2 equally valid solutions (top vertex=top-left or top-right) thanks to symmetry.

---

### Post by trent.josephsen on 2014-01-15
Yes, that's true. But if I were trying to stretch a rectangular photo into a canvas that shape, that's what I'd call "top left". I was shooting for a solution that would do the right thing most of the time, not a mathematically rigorous one.

---

### Post by Vaphell on 2014-01-16
yes, solution doing the right thing most of the time is the best we can get here. But what if the user draws a square rotated 45deg, the script shows him a solution but he wants the other one?
I'd say that if the algorithm and its reversed version (rotated versions?) yield the same result then we are golden, if these algorithm passes yield different solutions the user should be prompted to choose one.

---

### Post by ofnuts on 2014-01-16
In practice the path is set by putting its vertices over the corners of real windows in a photograph, so I doubt that the perfect diamond will ever show up...

---

### Post by Vaphell on 2014-01-17
yes, i suppose it's not going to happen :-)

it occured to me that finding the order by finding crossing pairs is an overkill. It's enough to take 1 vertex and calculate a (y=ax+b) of lines connecting it to other vertices. a in the middle means diagonal (it has to be between sides) so if you sort a's you get vertices in order.
Having the order go to step 2.

---

### Post by ofnuts on 2014-01-17
> **Vaphell said:**
> yes, i suppose it's not going to happen :-)

it occured to me that finding the order by finding crossing pairs is an overkill. It's enough to take 1 vertex and calculate a (y=ax+b) of lines connecting it to other vertices. a in the middle means diagonal (it has to be between sides) so if you sort a's you get vertices in order.
Having the order go to step 2.

Will give that some thought. Looks like a good idea. There are algorithms to detect crossing segments, but I'll have to brush up my math to use them :)

---

