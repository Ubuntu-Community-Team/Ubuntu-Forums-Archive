---
title: "Turtle Graphing"
date: 2013-07-15
forum: Programming Talk
---

### Post by Sky001 on 2013-07-15
Hello everyone, 

I've bumped into two strange problems on my ubuntu 12.04 installation. I'm a novice programmer here. I was playing around with turtle graphics when my python 3.3.0 stopped doing what I wanted. Here is the simple code. 
```

import math
import turtle

wn = turtle.Screen()
wn.bgcolor('white')
wn.setworldcoordinates(0,-1.25,360,1.25)
fred = turtle.Turtle()
lin = turtle.Turtle()

for angle in range(0,361):
    y = math.sin(math.radians(angle))
    fred.color('red')
    fred.speed(0)
    fred.goto(angle,y)
    lin.speed(0)
    lin.goto(angle,0)

wn.exitonclick()
```

The two things that bother me are, python is ignoring ```
fred.speed(0)
``` and ```
lin.speed(0)
```, which should effectively cut the animation time, yet do not. And the color doesn't come out right. Instead of fred forming a red line, he forms a black which then becomes red (How do I upload images?). Anyone know how I can approach these issues?

---

### Post by alan9800 on 2013-07-15
after having installed the python-tk package (that is requested by the turtle module), I tested your code under python 2.7.3 (the standard python release on Ubuntu 12.04) and all worked fine.
Also [the python 3.3.0 documentation]("http://docs.python.org/release/3.3.0/library/turtle.html#module-turtle") specifies that you need the python-tk package for using properly the turtle module.

---

### Post by Sky001 on 2013-07-16
tk is Tkinter in python 2 and tkinter in python 3, right? I followed [this]("http://wiki.python.org/moin/TkInter") test, towards the bottom of the page to make sure that _tkinter was installed and could be called. Am I missing something? 

My problem isn't that the code isn't running, but rather the speed it executes at and the coloring. ```
fred.speed(0)
``` means that the code should execute without the animation. This is not the case for me. As for the coloring, ```
fred.color('red')
``` means that turtle fred should be completely red. But fred starts off as black, then sometime later decides to change to red. I hope the image works this time aroud. [IMG][[IMG]http://i1313.photobucket.com/albums/t543/Precetria/oddity01_zps4b122344.png[/IMG]]("http://s1313.photobucket.com/user/Precetria/media/oddity01_zps4b122344.png.html")[/IMG]

Forgive the massive image: not sure how to resize it. The reason these two bother be is because, I'm thinking there is a problem here, that if i don't take care of really soon, I might regret not doing so at a later date. 

Thanks

---

### Post by alan9800 on 2013-07-16
my "fred" is completely red, as you can see:

[IMG]http://img839.imageshack.us/img839/117/2ei.png[/IMG]

I ran your code with python 2.7.3, as I have already said in my previous post.

---

