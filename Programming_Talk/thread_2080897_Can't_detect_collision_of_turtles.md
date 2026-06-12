---
title: "Can't detect collision of turtles"
date: 2012-11-05
forum: Programming Talk
---

### Post by DaimyoKirby on 2012-11-05
So right now I'm working on an exercise program for a python tutorial I'm doing, and it has me making a program where a turtle randomly turns left or right, and then moves forward 50, always bouncing off the edges of the window if it tries to go out that far.
The exercise has me expand this program by making two turtles move around, and it wants me to have the program halt if the turtles collide.

Easier said than done.

I've tried quite a bit, and it seems like there's always some problem or something that makes it so, despite output logs saying they were in fact at the same spot at on time (I added that for debugging this issue), the turtles just keep on moving.
Here's the code:
```
import turtle
import random

wn = turtle.Screen()

jim = turtle.Turtle()
jim.shape('turtle')
joe = turtle.Turtle()
joe.shape('turtle')

def isOnScreen(window, someturtle):
    leftbound = -window.window_width()/2
    rightbound = window.window_width()/2
    topbound = window.window_height()/2
    bottombound = -window.window_height()/2
    
    turtleX = someturtle.xcor()
    turtleY = someturtle.ycor()
    
    if turtleX > rightbound or turtleX < leftbound or turtleY > topbound or turtleY < bottombound:
        someturtle.lt(180)
        someturtle.fd(50)
        
def collisionCheck(turtle1, turtle2):
    crash = True
    print(turtle1.pos(), turtle2.pos())
    if turtle1.pos() != turtle2.pos():
        crash = False
    return crash

def startPos(window, turtle1, turtle2):
    leftbound = -window.window_width()/2
    rightbound = window.window_width()/2
    bottombound = -window.window_height()/2
    topbound = window.window_height()/2
    for turtle in [turtle1, turtle2]:
        turtle.up()
        randomX = random.randrange(int(leftbound), int(rightbound), 50)
        randomY = random.randrange(int(bottombound), int(topbound), 50)
        turtle.goto(randomX, randomY)
        turtle.down()

def randomMove(turtle):
    coinflip = random.randrange(0, 2)
    if coinflip == 0:
        turtle.lt(90) #heads
    else:
        turtle.rt(90) #tails
    turtle.fd(50)

startPos(wn, jim, joe)


infLoop = 1
while infLoop != 0:
    for turtle in [jim, joe]:
        randomMove(turtle)
        if collisionCheck(jim, joe) == True:
            infLoop = 0
            break
        isOnScreen(wn, turtle)

wn.exitonclick()
```

I'm using Python 3.2, and I'm writing this in Eclipse 4.2.1 using PyDev 2.7
My question: does anyone know how to make the above program detect when the turtles are standing upon the same spot, and force the program to stop (break the while loop) when this occurs?

---

### Post by muteXe on 2012-11-05
You could write a 'shell' script....


I'll get me coat...

---

### Post by trent.josephsen on 2012-11-05
@muteXe -- I laughed.

It looks to me as if the turtles will very rarely collide, since the collision check is done only after both turtles have already moved 50 steps to their final location. That is, the second one stands still and waits until the first one is done moving, then vice versa, and then the collision check is done once. Right? (Never done turtle stuff with Python before, forgive me if I'm making a bad assumption.)

How did you log it to verify that they're both in the same spot at the same time?

I also notice that you do the collision check *before* "bouncing" the turtle off the wall, which seems odd if not exactly wrong.

---

### Post by DaimyoKirby on 2012-11-05
Well, I put an if statement in between movement and the isOnScreen check, so I would think that that checks right after each turtle moves (i.e., two collision checks per while loop execution); however, I don't know how I can confirm if this is actually happening.

I log their coordinates after each move; in the collisionCheck function, I included a print for both the turtle's positions.  At points where they appear to be on the same spot, the coordinates usually confirm they are (rarely there are discrepancies like 0.00 vs. -0.00, which I don't know how to fix).

The check is in the middle only because I moved the call to randomMove() above the collisionCheck, to see if that would do anything different, and didn't bother moving the isOnScreen call with it.

---

### Post by trent.josephsen on 2012-11-05
Ok, you're right that it checks after each turtle moves -- I misread it. But what I'm saying is that if turtle A starts 20 steps east of the origin facing west, and turtle B starts 20 steps west of the origin facing east, you won't detect a collision even though they start and end on opposite sides of each other.

I didn't realize the coordinates of the turtles' positions were floating point numbers -- that's probably your problem, and the -0.00 / +0.00 was a big clue. You'll want to convert those to integers, probably, and figure out whether they're referring to the same... pixel, I guess. 0.00000001 and 0.00000002 are different numbers, but you probably don't want to treat them as such.

---

### Post by DaimyoKirby on 2012-11-07
Ohhh, that makes quite a bit of sense. I didn't realize that the log wouldn't necessarily report the full floating number.
Well, I changed it, and it worked:
[spoiler]```
import turtle
import random

wn = turtle.Screen()

jim = turtle.Turtle()
jim.shape('turtle')
joe = turtle.Turtle()
joe.shape('turtle')

def isOnScreen(window, someturtle):
    leftbound = -window.window_width()/2
    rightbound = window.window_width()/2
    topbound = window.window_height()/2
    bottombound = -window.window_height()/2
    
    turtleX = someturtle.xcor()
    turtleY = someturtle.ycor()
    
    if turtleX > rightbound or turtleX < leftbound or turtleY > topbound or turtleY < bottombound:
        someturtle.lt(180)
        someturtle.fd(50)
        
def collisionCheck(turtle1, turtle2):
    crash = True
    turtle1X = turtle1.xcor()
    turtle1Y = turtle1.ycor()
    turtle2X = turtle2.xcor()
    turtle2Y = turtle2.ycor()
    turtle1Pos = (int(turtle1X), int(turtle1Y))
    turtle2Pos = (int(turtle2X), int(turtle2Y))
    if turtle1Pos != turtle2Pos:
        crash = False
    return crash

def startPos(window, turtle1, turtle2):
    leftbound = -window.window_width()/2
    rightbound = window.window_width()/2
    bottombound = -window.window_height()/2
    topbound = window.window_height()/2
    for turtle in [turtle1, turtle2]:
        turtle.up()
        randomX = random.randrange(int(leftbound), int(rightbound), 50)
        randomY = random.randrange(int(bottombound), int(topbound), 50)
        turtle.goto(int(randomX), int(randomY))
        turtle.down()

def randomMove(turtle):
    coinflip = random.randrange(0, 2)
    if coinflip == 0:
        turtle.lt(90) #heads
    else:
        turtle.rt(90) #tails
    turtle.fd(50)

startPos(wn, jim, joe)


infLoop = 1
while infLoop != 0:
    for turtle in [jim, joe]:
        randomMove(turtle)
        if collisionCheck(jim, joe) == True:
            infLoop = 0
            break
        isOnScreen(wn, turtle)

wn.exitonclick()
```[/spoiler]

However, when I tried to clean the code up, the turtles would initialize, move to random starting locations, and then not move; if I click on the window, it'll close, suggesting the program is skipping my while loop and going right to wn.exitonclick(). Here's the modified code:
```
import turtle
import random

wn = turtle.Screen()

jim = turtle.Turtle()
jim.shape('turtle')
joe = turtle.Turtle()
joe.shape('turtle')

def isOnScreen(window, someturtle):
    leftbound = -window.window_width()/2
    rightbound = window.window_width()/2
    topbound = window.window_height()/2
    bottombound = -window.window_height()/2
    
    turtleX = someturtle.xcor()
    turtleY = someturtle.ycor()
    
    if turtleX > rightbound or turtleX < leftbound or turtleY > topbound or turtleY < bottombound:
        someturtle.lt(180)
        someturtle.fd(50)
        
def collisionCheck(turtle1, turtle2):
    crash = False
    turtle1X = turtle1.xcor()
    turtle1Y = turtle1.ycor()
    turtle2X = turtle2.xcor()
    turtle2Y = turtle2.ycor()
    turtle1Pos = (int(turtle1X), int(turtle1Y))
    turtle2Pos = (int(turtle2X), int(turtle2Y))
    if turtle1Pos == turtle2Pos:
        crash = True
    return crash

def startPos(window, turtle1, turtle2):
    leftbound = -window.window_width()/2
    rightbound = window.window_width()/2
    bottombound = -window.window_height()/2
    topbound = window.window_height()/2
    for turtle in [turtle1, turtle2]:
        turtle.up()
        randomX = random.randrange(int(leftbound), int(rightbound), 50)
        randomY = random.randrange(int(bottombound), int(topbound), 50)
        turtle.goto(int(randomX), int(randomY))
        turtle.down()

def randomMove(turtle):
    coinflip = random.randrange(0, 2)
    if coinflip == 0:
        turtle.lt(90) #heads
    else:
        turtle.rt(90) #tails
    turtle.fd(50)

startPos(wn, jim, joe)

while collisionCheck == False:
    for turtle in [jim, joe]:
        randomMove(turtle)
        isOnScreen(wn, turtle)

wn.exitonclick()
```It seems to me that this should work fine, but for some reason it isn't. Do you know what might be causing this?

(As a side irritation, do you know why we can't use spoilers?)

---

### Post by spjackson on 2012-11-07
> **DaimyoKirby said:**
> 
```

while collisionCheck == False:
    for turtle in [jim, joe]:
        randomMove(turtle)
        isOnScreen(wn, turtle)

```
However, when I tried to clean the code up, the turtles would initialize, move to random starting locations, and then not move; if I click on the window, it'll close, suggesting the program is skipping my while loop and going right to wn.exitonclick(). 
I think you mean
```

while collisionCheck(jim, joe) == False:

```

---

### Post by DaimyoKirby on 2012-11-07
> **spjackson said:**
> I think you mean
```

while collisionCheck(jim, joe) == False:

```

*facepalm*
...I feel like an idiot.

Well, that fixes everything, and I'm satisfied with how it's turned out,  so I can finally put this project to rest.

Thanks for all the help, trent.josephsen and spjackson! You guys rock.

---

