---
title: "Filling rectangle with circles, algorithm help needed"
date: 2009-02-28
forum: Programming Talk
---

### Post by tneva82 on 2009-02-28
As title says more of algorithm issue than programming. Anyway I need to figure way to create X/Y co-ordinates(well actually more like X/Z in 3d-space but what the heck) for bunch of circles in a way that the circles would cover whole rectangle. Doesn't matter if some circles extends past rectangle. What does matter is that there's minimal amount of overlapping between circles, ie where-ever I be in rectangle there's only as many circles overlapping as possible.

I know the width and depth of the rectangle plus radius of individual circle(each circle is of same size). Now need to figure out algorithm that creates co-ordinates of the n circles it takes to fill it(doesn't matter how many circles it takes as long as there's least amount of overlapping) regardless of the size of rectangle or radius of circles.

---

### Post by hessiess on 2009-02-28
Calculate the bounding box of the cercle, then do something like the folowing (will only work if the rectangle is acsiss aligned).

```

x = circle bounding box / 2;
y = circle bounding box / 2;
for (ever)
{
    for (ever)
    {
        if(x + bounding box width > rectangle bounding box right)
        {
            place cercle(rectangle bounding box right - circle bounding box / 2)
            break
         }

         place cercle(rectangle bounding box right - circle bounding box / 2)
         x += circle bounding box width
    }
    y += circle bounding box height
    simmaler check to above to stop the cercles poping out the bottom of the rectangle   
}

```

---

### Post by Choad on 2009-02-28
maybe i'm over simplifying this, but wouldn't this work?

```

numCirclesHorz = ceil( rectangle.width / circle.radius )
numCirclesVert = ceil( rectangle.height / circle.radius )
w = ( rectangle.width - circle.radius ) / numCirclesHorz
h = ( rectangle.height - circle.radius ) / numCirclesVert
for ( x = 0 to numCirclesHorz )
  for ( y = 0 to numCirclesVert )
    createCircle( rectangle.x + w * x, rectangle.y + h * y )

```

or am i not understanding the problem right?

(oh and that also assumes that a circle and rectangle's x/y origin is the top left corner not the centre)

---

### Post by WW on 2009-02-28
Or...

Figure out how to tile your rectangle with hexagons (i.e. overlay a honeycomb pattern); you'll need a little trigonometry.  Choose the size of the hexagon so that it is inscribed in your circle.  To cover your rectangle with circles, just put a circle at the center of each hexagon in the honeycomb.

This will give you a feasible solution (i.e. every part of the rectangle is covered), but almost certainly not an optimal solution.  That is, it probably won't give the minimal amount of overlap.

---

### Post by tneva82 on 2009-03-01
> **Choad said:**
> maybe i'm over simplifying this, but wouldn't this work?

Need to try it. Are you sure there won't be blank spots not covered by any circle? Atleast quick test gave hint there might be some blank areas(these are HUGE issues. Better overlaps than blank areas which would cause essentially whole communication spreading system go all haywire the second object enters area not covered by any circles.

However that might be just error in testing code which I hashes around quickly.

Edit: The more I try the more I think your error isn't working as it should. Number of spots which aren't covered is tons.

---

### Post by Choad on 2009-03-01
oh ok, well in that case you want to do what WW suggested and make a diamond pattern (hexagonal pattern is the same as diamond pattern)

```

int rectWidth = 400;
        int rectHeight = 200;
        int rectX = 50;
        int rectY = 300;
        int circleRadius = 30;
        int halfCircle = circleRadius / 2;
        for (int xx = rectX - halfCircle; xx < rectX + rectWidth; xx += circleRadius) {
            for (int yy = rectY - halfCircle; yy < rectY + rectHeight; yy += circleRadius) {
                g.drawOval(xx, yy, circleRadius, circleRadius);
                if (xx + halfCircle < rectX + rectWidth && yy + halfCircle < rectY + rectHeight)
                    g.drawOval(xx + halfCircle, yy + halfCircle, circleRadius, circleRadius);
            }
        }
        g.drawRect(rectX, rectY, rectWidth, rectHeight);

```

tho that is hideously inefficient lol!

---

### Post by tneva82 on 2009-03-01
> **Choad said:**
> tho that is hideously inefficient lol!

Inefficient in what sense? As said it's absolutly _crucial_ there's not one spot that's not covered. If there is...Well I don't want to be trying what happens! I rather have 4 overlaps per circle than spot free. Now if inefficient as in it's going to take a while to calculate who cares. This is done only once at the start of program to create co-ordinates for the circles and after that only reason to do it again is if program is closed and started again.

Alternative solution would be if I could figure out quick way to check which squares are within X radius of me if I use squares instead. Or even more specifically how squares within X radius change as object moves.

---

### Post by simeon87 on 2009-03-01
> **Choad said:**
> oh ok, well in that case you want to do what WW suggested and make a diamond pattern (hexagonal pattern is the same as diamond pattern)

[code removed]

tho that is hideously inefficient lol!

An improvement would be to move the upper left circle a bit up and and a bit to the left so the circle is touching (0,0). Then you can simply create the grid pattern again but you would get rid of the whole outer border of circles as these are mostly outside the rectangle.

---

### Post by WW on 2009-03-01
> **Choad said:**
> oh ok, well in that case you want to do what WW suggested and make a diamond pattern (hexagonal pattern is the same as diamond pattern)

I guess "hexagonal pattern" makes it sound more complicated than necessary.  Maybe it would be clearer to call it a triangular pattern; specifically, equilateral triangles.

[This link](http://www.mathhelpforum.com/math-help/geometry/28804-percentage-area-circles-overlapping-triangle.html) shows a picture of three circles centered at the vertices of an equilateral triangle. To have no gap, you want to use a smaller triangle, so all three circles intersect at the center of the triangle.  To cover the whole region, tile it with equilateral triangles, like the third picture in [this link](http://mathworld.wolfram.com/TriangleTiling.html).

---

### Post by Choad on 2009-03-01
> **tneva82 said:**
> Inefficient in what sense? As said it's absolutly _crucial_ there's not one spot that's not covered. If there is...Well I don't want to be trying what happens! I rather have 4 overlaps per circle than spot free. Now if inefficient as in it's going to take a while to calculate who cares. This is done only once at the start of program to create co-ordinates for the circles and after that only reason to do it again is if program is closed and started again.

Alternative solution would be if I could figure out quick way to check which squares are within X radius of me if I use squares instead. Or even more specifically how squares within X radius change as object moves.
i meant inefficient as in uses too many cpu cycles, but if that's not an issue then it certainly works! it's the most efficient in terms of the circles overlapping each other :)

---

### Post by WW on 2009-03-01
> **Choad said:**
> i meant inefficient as in uses too many cpu cycles, but if that's not an issue then it certainly works! it's the most efficient in terms of the circles overlapping each other :)
Your code is not creating the triangular pattern; it is using a square grid pattern rotated 45 degrees.

---

### Post by tneva82 on 2009-03-01
> **Choad said:**
> i meant inefficient as in uses too many cpu cycles, but if that's not an issue then it certainly works! it's the most efficient in terms of the circles overlapping each other :)

Well as said this is once per program start calculation that is done. Part of the initialisation. Sure it might take few seconds more but that's hardly crucial speed component. This is something that doesn't need to be fast for real-time calculation. I just need to create bunch of co-ordinates which are then used in rest of the program.

Frankly if it doesn't take up several minutes I don't think anybody is going to notice. Especially as in ideal world this program won't be shutdown and restarted all the time so taking long to calculate isn't going to kill me :D

---

### Post by Choad on 2009-03-01
> **WW said:**
> Your code is not creating the triangular pattern; it is using a square grid pattern rotated 45 degrees.
i don't see a more effiecient way of doing it tbh. by all means prove me wrong tho!

---

### Post by WW on 2009-03-01
[This link](http://www.naic.edu/~pfreire/tiling/) shows the pattern that I am talking about.

---

### Post by Choad on 2009-03-01
> **tneva82 said:**
> Well as said this is once per program start calculation that is done. Part of the initialisation. Sure it might take few seconds more but that's hardly crucial speed component. This is something that doesn't need to be fast for real-time calculation. I just need to create bunch of co-ordinates which are then used in rest of the program.

Frankly if it doesn't take up several minutes I don't think anybody is going to notice. Especially as in ideal world this program won't be shutdown and restarted all the time so taking long to calculate isn't going to kill me :D
what are you making?

---

### Post by Choad on 2009-03-01
> **WW said:**
> [This link](http://www.naic.edu/~pfreire/tiling/) shows the pattern that I am talking about.
ahhh i c! yes that looks a lot better!

---

### Post by tneva82 on 2009-03-01
> **Choad said:**
> what are you making?

This would be server program of network program I'm making. Whole bunch of objects(some clients, some server-internal objects). Clients need to be aware of other objects but NOT about every single one of them. More of roughly in same area only. Therefore I decided I would split the area into smaller areas(these are the circles) and only inform of changes to objects to those who are member of same area object is. This reduces number of messages I need to send through network(handy speed optimisation).

Then when objects move around they are reassigned in their areas(they are members of more than where they are just to ensure they know of objects in the edge of area BEFORE they cross that edge themselves!) as they move around.

Need a way to figure out faster way to check which areas they are(and more importantly how they _change_). Should be possible to optimise it by using knowledge that the circles form essentially 2 dimensional grid(albeit stored in 1-dimensional vector).

And since the rectangle(map) and zones(circles) are only created once during the initialisation of server doesn't matter if it takes a while. But to ensure everybody receives updates they need there must not be areas not covered. In fantasy game term that could cause you to walk next to dragon and be killed by it and never seeing the dragon because server never told you there's dragon since it's not member of any zone ;-)

---

### Post by tneva82 on 2009-03-01
> **Choad said:**
> ahhh i c! yes that looks a lot better!

Indeed. That's what I'm talking about! Now I need to create code to create co-ordinates of those circles regardless of what's the rectangles size and radius of circle.

---

### Post by Choad on 2009-03-01
```

        double x1 = 50;
        double y1 = 150;
        int circleRadius = 60;
        double xOff = Math.cos( Math.toRadians( 30 )) * circleRadius;
        double yOff = circleRadius*1.5;
        
        for (int i = 0; i < 3; i++) {
            for ( int ii = 0; ii < 6; ii++) {
                g.drawOval( (int)( x1 + xOff * ii ), (int)( y1 + yOff * i), circleRadius, circleRadius);
                g.drawOval( (int)( x1 + xOff * ii + xOff / 2), (int)(y1 + yOff * i + yOff / 2), circleRadius, circleRadius);
            }
        }

```

that looks about right...

---

### Post by Choad on 2009-03-01
> **tneva82 said:**
> This would be server program of network program I'm making. Whole bunch of objects(some clients, some server-internal objects). Clients need to be aware of other objects but NOT about every single one of them. More of roughly in same area only. Therefore I decided I would split the area into smaller areas(these are the circles) and only inform of changes to objects to those who are member of same area object is. This reduces number of messages I need to send through network(handy speed optimisation).

Then when objects move around they are reassigned in their areas(they are members of more than where they are just to ensure they know of objects in the edge of area BEFORE they cross that edge themselves!) as they move around.

Need a way to figure out faster way to check which areas they are(and more importantly how they _change_). Should be possible to optimise it by using knowledge that the circles form essentially 2 dimensional grid(albeit stored in 1-dimensional vector).

And since the rectangle(map) and zones(circles) are only created once during the initialisation of server doesn't matter if it takes a while. But to ensure everybody receives updates they need there must not be areas not covered. In fantasy game term that could cause you to walk next to dragon and be killed by it and never seeing the dragon because server never told you there's dragon since it's not member of any zone ;-)
reading what you want... wouldn't it make a bit more sense to use squares? it just simplifies the whole process. update the client with info from the square he is in plus each of the 8 surrounding suares. simples!

---

### Post by tneva82 on 2009-03-01
> **Choad said:**
> reading what you want... wouldn't it make a bit more sense to use squares? it just simplifies the whole process. update the client with info from the square he is in plus each of the 8 surrounding suares. simples!

That's what I have been thinking about. Only problem is figuring out which nearby squares he is closeby. Or just inform him of all surrounding but even then I need method to check _changes_. Ie when you enter new square and when you leave square so that I can inform of objects inside square that object X entered/left square. Already had this one solved with circles which is why I'm trying to solve the circle creation.

Funny that. I have square placement figured out but not how to use it. With circles it's otherway around :D

---

### Post by Choad on 2009-03-01
surely it would just be a matter or storing the squares in a 2d array and collecting the info from each square who's index is next to the index of the square he is in.

ie, a client who is in square[3][6] will recieve updates from square[2][5]...square[4][7]

---

### Post by tneva82 on 2009-03-01
> **Choad said:**
> surely it would just be a matter or storing the squares in a 2d array and collecting the info from each square who's index is next to the index of the square he is in.

ie, a client who is in square[3][6] will recieve updates from square[2][5]...square[4][7]

Again I need to be able to detect when things _change_ so I can react to that. For example send in base data about objects in the zone. No point sending "Object X's Y variable changed by Z amount" if the client doesn't know what was original value that got modified ;-) Too much information to be sent over continuously(15 int/float variables and string and need to send several times per second).

Also when it changes object is assigned to the zone. So ATM it works like this. Object X changes. Program then goes through zones he's member of. For each zone it loops through sending same message for every object it finds in those zones(still trying to figure out how to remove duplicate messages efficiently and wether or not duplicate messages are lesser evil than extra loops to make sure he wasn't already included).

---

