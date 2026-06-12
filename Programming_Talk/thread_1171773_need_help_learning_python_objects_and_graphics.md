---
title: "need help learning python objects and graphics"
date: 2009-05-27
forum: Programming Talk
---

### Post by burntresistor on 2009-05-27
The book im using problem it has given me is create a program that uses squares instead of circles on the one it gives me,be able to draw additional squares on click im guessing it means cloning and not moving
have a message saying quit in a button. Im using rectangle because square wasnt in the command list in this chapter.

from graphics import *

def main():
	win=GraphWin()
	shape= Rectangle(Point(50,50), 20)
	shape.setOutline("blue")
	shape.setFill("blue")
	shape2 = shape.clone()
	shape.draw(win)
	for i in range(10) :	
	    p= win.getMouse()
	    c = shape2.getCenter()
	    dx = p.getX()-c.getX()
	    dy=p.getY() - c.getY()
	shape.move(dx,dy)
#enter in quit box
	button.setText("quit")
	win.getMouse()
	win.close()
main()



im getting this attribute error and im not sure what I need to fix:
AttributeError: 'int' object has no attribute 'clone'

---

### Post by necromantula on 2009-05-27
shape.setFill("blue")
	shape2 = shape.clone()
	shape.draw(win)


try getting rid of the clone()
perhaps just making a second copy of the variable would be enough

---

### Post by burntresistor on 2009-05-27
im having a hard time getting a grasp of this once I got to ch 5(which is all object oriented) the way the python programming by John zelle book lays out is there a better source I can learn from

---

