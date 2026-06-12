---
title: "Python Pygame Graphics"
date: 2010-09-26
forum: Programming Talk
---

### Post by acreech on 2010-09-26
I am trying to help my son learn Python and we have ran into a snag on a section. I have not been able to find a command that will solve our problem. We are working on a tutorial that uses "livewires" when is supposed to make it easier for kids to learn. 


Towards of the bottom of of the code I set the variable "smile". I would like make it rotate the smile 180 degrees to make it a frown. The code that I have here will not rotate smile. 


```

from livewires import *
import os, sys
import random
import pygame
from pygame.locals import *
w=640
h=480


begin_graphics()
set_colour(Colour.blue)
screen = pygame.display.set_mode((w, h))


circle(300, 200, 80)
circle(270,230,20)
circle(330,230, 20)


move (300,210)
draw(280,180)
draw(320,180)
draw(300,210)

smile = circle(300, 180, endpoints=((270,180), (340,180)))
smile.flip(20)

```

---

### Post by gmargo on 2010-09-26
It would be a lot easier to help if you would provide a link to the tutorial that you are following.

Update: I found the **The LiveWires Python Course** at [http://www.livewires.org.uk/python/home]("http://www.livewires.org.uk/python/homeThe")

As far as I can tell, the **circle()** method does not return any object, so there's nothing to call **flip()** on. (I can't find any **flip()** at the moment.)

---

### Post by acreech on 2010-09-26
> **gmargo said:**
> It would be a lot easier to help if you would provide a link to the tutorial that you are following.

[HTML]http://www.livewires.org.uk/python/home[/HTML]

The manual is  here. 

[HTML]http://www.livewires.org.uk/python/worksheets[/HTML]

We are in section 3. I have attached that particular section. 

Thanks for any suggestions.

---

### Post by gmargo on 2010-09-26
Crossing posts... In case you didn't see my edits above.... 

The **circle()** method does not return an object, so there's nothing to **flip()**.

---

### Post by acreech on 2010-09-26
> **gmargo said:**
> Crossing posts... In case you didn't see my edits above.... 

The **circle()** method does not return an object, so there's nothing to **flip()**.

This is probably part of the problem of dumbing down a program language to make it easier for kids (and me) to learn. With the livewires module install on the computer and then importing its library, the circle command works. If you don't import the Livewires module then none of this works......

So I guess I need to find the actual python code to create the semi-circle. Which might be the circle command with defined endpoints. 

My main goal was to get him through this small tutorial, knowing that it is not necessarily correct and then move him into learning more of the full code instead of the livewires module.

---

### Post by acreech on 2010-09-26
> **gmargo said:**
> Crossing posts... In case you didn't see my edits above.... 

The **circle()** method does not return an object, so there's nothing to **flip()**.

So this is the correct command to make a circle

```

pygame.draw.circle(windowSurface, BLUE, (300, 50), 20, 0)

```

What I need to define endpoints to the circle to make a semi-circle.

---

### Post by acreech on 2010-09-26
I found a way to do this with the livewires module. I have attached the code below to show what I came up with, I just have to move the semi-circle to the position I want it in. 

The explanation that was given to me for this is as follows. 

> 
However, i could get TK to draw it (livewires is using another library called tk that does the drawing for it). First i had to get access to the canvas object, then i was able to use tk's create_arc() function:


from livewires import *
import livewires.beginners
begin_graphics()
canvas = livewires.beginners._canvas
canvas.create_arc(100,350, 50,300, start=0, extent=180, style="arc")


I'll describe how it works, but incase i fail, here's the documentation for create_arc: 
[HTML]http://www.tcl.tk/man/tcl8.5/TkCmd/canvas.htm#M111[/HTML]


First off, the coordinates are going to be different. Livewires has the coordinate 0,0 at the bottom left corner of the window, but tk has 0,0 at the top left corner of the window. So if you want to move down 100 pixels, you have to add 100 to the y coordinate, and if you want to go up 100 pixels you have to subtract. Its kind of funny, but it's how most computer graphics work internally.


So the way arc works, is you define the coordinates of two opposite sides of a rectangle, and it draws an arc between those two corners. Since we want a semi-circle, we'll use a square. That's what the 100,350,50,300 are about; 100,350 is the lower right corner of the square and 50,300 is the upper right corner of the square.


create_arc() draws in terms of degrees and draws counterclockwise. So saying start=0 is telling it to start drawing at degree 0 (perfectly horizontal and to the right), and extent=180 tells it to draw for 180 degrees, eg half a circle.



```

from livewires import *
import os, sys
import random
import pygame
from pygame.locals import *
import livewires.beginners

#w=640
#h=480





begin_graphics()
canvas = livewires.beginners._canvas
set_colour(Colour.blue)
#screen = pygame.display.set_mode((w, h))

canvas.create_arc(100,350, 50,300, start=0, extent=180, style="arc")

circle(300, 200, 80)
circle(270,230,20)
circle(330,230, 20)


move (300,210)
draw(280,180)
draw(320,180)
draw(300,210)

circle(300, 180, endpoints=((270,180), (340,180)))


```

---

