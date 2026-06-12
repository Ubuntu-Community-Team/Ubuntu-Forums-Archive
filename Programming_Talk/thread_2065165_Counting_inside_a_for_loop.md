---
title: "Counting inside a for loop"
date: 2012-10-01
forum: Programming Talk
---

### Post by DaimyoKirby on 2012-10-01
So I'm doing an independent study on python 3 in school right now, and I was working on this problem: [http://interactivepython.org/courselib/static/thinkcspy/Labs/montepi.html](http://interactivepython.org/courselib/static/thinkcspy/Labs/montepi.html)

The problem is, I can't figure out how to have my code count the number of red "darts" (the darts that hit the target), since everything I've tried always gives me a 0.  This is what I currently have:
```
import turtle
import math
import random

wn = turtle.Screen()
wn.setworldcoordinates(-1,-1,1,1)

jim = turtle.Turtle()

def dartboard (someturtle):
    someturtle.speed(0)
    drawCircle(someturtle)
    drawSquare(someturtle) #create square board around circle

def drawCircle(someturtle):
    someturtle.up()
    someturtle.goto(0, -1)
    someturtle.down()
    someturtle.circle(1, 360, 1000)
def drawSquare(someturtle):
    someturtle.up()
    someturtle.goto(1, -1)
    someturtle.down()
    for square in range(4):
        someturtle.lt(90)
        someturtle.fd(2)
        
def colorDart(someturtle):
    if someturtle.distance(0, 0) <= 1:
        someturtle.color('red')
    else:
        someturtle.color('blue')

dartboard(jim)
jim.up()

numdarts = 10
insideCount = 0
for i in range(numdarts):
    randx = random.uniform(-1, 1)
    randy = random.uniform(-1, 1)
    jim.goto(randx, randy)
    colorDart(jim)
    jim.stamp()
    if jim.color() == 'red':
        insideCount += 1
print(insideCount)

wn.exitonclick()
```As you may have noticed, I'm trying to increment insideCount every time turtle jim is red, but for some reason this doesn't work.
What am I doing wrong?

---

### Post by DaimyoKirby on 2012-10-01
Well, I solved it by changing
```
    if jim.color() == 'red':
        insideCount += 1
```to
```
    if jim.distance(0, 0) <= 1:
        insideCount += 1
```However, I'm still curious: is there a way to increment using the color as the deciding factor, like I did in my original post?

---

### Post by Vaphell on 2012-10-01
what do you get from jim.color()? i see that color() is a method setting the color, but i am not convinced it returns what you think it returns.
add some print statement to make things clear eg print( jim.color() )

---

### Post by ofnuts on 2012-10-01
> **DaimyoKirby said:**
> Well, I solved it by changing
```
    if jim.color() == 'red':
        insideCount += 1
```to
```
    if jim.distance(0, 0) <= 1:
        insideCount += 1
```However, I'm still curious: is there a way to increment using the color as the deciding factor, like I did in my original post?
You draw a circle, not a full disc, so inside your circle you still have the original color. You'll see red only if you are exactly on the circle.

---

### Post by DaimyoKirby on 2012-10-03
> **Vaphell said:**
> what do you get from jim.color()? i see that color() is a method setting the color, but i am not convinced it returns what you think it returns.
add some print statement to make things clear eg print( jim.color() )

Inserting a "print(jim.color())" right after jim.stamp() returned:
```
('blue', 'blue')
('red', 'red')
('red', 'red')
('red', 'red')
('red', 'red')
('red', 'red')
('red', 'red')
('blue', 'blue')
('red', 'red')
('red', 'red')
```I changed my code to
```
if jim.color() == ('red', 'red'):
```and that worked. And now that I think about it, that makes sense, since the .color() method sets both the pen color and the fill color, which would explain the two values returned each time print(jim.color()) was executed.  So if I wanted to do what I had originally planned, I would have to use either .pencolor() or .fillcolor(), since they only hold a single value.

Thanks for the help! This has really helped me learn more about how python works.

---

