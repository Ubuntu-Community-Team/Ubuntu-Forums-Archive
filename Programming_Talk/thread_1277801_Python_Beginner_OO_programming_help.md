---
title: "Python Beginner OO programming help"
date: 2009-09-28
forum: Programming Talk
---

### Post by burntresistor on 2009-09-28
Well I got to the point in the book I'm learning from to get to OO programming and I'm spending more of my time getting IDLE to understand there graphics.py module that its based on than anything else.

This is the problem I'm on I thought it would be easier to see it before I edited the way needed. I'm getting errors like it doesn't recognize what graphics means and when I change from graphics import to import graphics. It doesn't understand what circle means. The book I'm learning from is python programing by john zelle its written alright getting the supplement material to actually work is the problem.

```

from graphics import *

def main():
	win = GraphWin()
	shape = Circle(Point(50,50), 20)
	shape.setOutline("red")
	shape.setFill("red")
	shape.draw(win)
	for i in range(10) :
	    p=win.getMouse()	
	    c=shape.getCenter()
	    dx = p.getX() - c.getX()
	    dy= p.getY() - c.getY()
	    shape.move(dx,dy)
	    win.close()
	main()

```

Oh and I'm using Idle

---

### Post by lhowaf on 2009-09-28
Have you installed the graphics module?

---

### Post by Bachstelze on 2009-09-29
Unrelated, but 

from graphics import *

is bad practice, as it will pollute your namespace. Rather do

import graphics

and prepend all functions that belong to the graphics module with "graphics." (for example graphics.GraphWin() instead of GraphWin()).

---

### Post by burntresistor on 2009-09-29
> **lhowaf said:**
> Have you installed the graphics module?

Install how? It worked before by just importing it the module is just one file called graphics.py 
I became impatient dealing with this problem with there supplements and read ahead 2 chapters (functions and decision structures) Is there any 3rd party module I can download elsewhere that might be easier to install and get working? To go back and do the problems

---

### Post by Michael.Godawski on 2009-09-30
Moved to PT. ;)

---

### Post by nvteighen on 2009-09-30
Have you placed graphics.py into the same directory where your code lies in?

---

