---
title: "[JAVA] Java swing help with DNA Chaos game."
date: 2010-03-25
forum: Programming Talk
---

### Post by Steveh15 on 2010-03-25
Hello
I'm a bit of a newb when in comes to Java, wondering if anybody could lend a hand with my Java assignment.

I have to create a DNA driven chaos game. For those not familiar with it, I'm basically plotting lots and lots of different points in a square, and when lots of these points are plotted they make a pattern

For the final part of this experiment I'm plotting almost 8 million points in a 800 * 800 pixel square. Obviously when i plot all these the square is completely filled and no pattern is visible.

What I need to do is divide the square up into smaller squares(at least 8*8 = 64 squares but preferably 16*16=256 squares). In each of these smaller squares I determine how many points lie within the square, and then colour the square according to that number. 
Overall the entire square becomes a density plot, hopefully with different colours represently different densities of points.

The Problem is I have no idea how to do this.

I thought I could create64 or 256 different polygons and then go through each of the 8 million points and find out which Polygon it belongs to, ultimately keeping a tally on how many points a polygon has and then plotting them accordingly at the end. This doesn't seem very efficient to me.

Does anybody have any ideas of suggestions to what I need to do?

I can provide for details or screen shots if you like.

Here is a website describing what I'm doing. It's not exactly the same, they visualize them in a different way but it's the general idea.
[http://orion.math.iastate.edu/danwell/CG/CG.html](http://orion.math.iastate.edu/danwell/CG/CG.html)

Thanks very much
Regards
Steve.

---

### Post by GregBrannon on 2010-03-25
Start here: [http://ubuntuforums.org/showthread.php?t=717011]("http://ubuntuforums.org/showthread.php?t=717011")

---

### Post by LKjell on 2010-03-26
Have a look at game of life. Just google it. With the DNA game I guess you need to have some rules as well.

---

