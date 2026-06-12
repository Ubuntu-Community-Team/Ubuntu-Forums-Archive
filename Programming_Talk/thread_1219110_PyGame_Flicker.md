---
title: "PyGame Flicker"
date: 2009-07-21
forum: Programming Talk
---

### Post by matmatmat on 2009-07-21
Attached is my breakout like program.
When block are removed others flicker and the blocking blocks ("_" in the array) don't work
Can someone help please?

---

### Post by .Maleficus. on 2009-07-21
I'll be able to help more when you attach the program ;).

---

### Post by matmatmat on 2009-07-21
Oops!
That's the second time!

---

### Post by Sockerdrickan on 2009-07-21
Are you flipping the screen surface? Doublebuffer?

---

### Post by matmatmat on 2009-07-21
Don't think so
(im new to game programming)

---

### Post by Sockerdrickan on 2009-07-21
Ok check those out then, what you are describing are classic screen buffering calibration errors

---

### Post by lavinog on 2009-07-21
> **matmatmat said:**
>  and the blocking blocks ("_" in the array) don't work
Can someone help please?

```

						if barray[i] == "_":
                                                        blocksp = sblock(sblocki, n2, n)
                                                        blocks.append(blocksp)
                                                        lastn2 = n2
                                                        i += 1													

```
May not be the reason but the if statement is indented with tabs, while the other lines are indented with spaces

Edit: the function for sblock.move() also mixes indentions.

---

### Post by lavinog on 2009-07-21
I noticed that the ball doesn't react to any blocks

for sblock change the ```
ball.move_y = -4
``````
 to ball.move_y = 4
```
-y is up and +y is down

---

### Post by smartbei on 2009-07-22
Bunch of things that I see:
[list]
[*]The loop you have that creates the blocks has a bug - you have 4 of these with minor differences:
```

if barray[i] == 'r':
    blocksp = block(rblock, n2, n, "r")
    blocks.append(blocksp)
    lastn2 = n2
    i += 1

```
The problem is that you increment i and then continue checking... what if barray[i] == 'r', and barray[i+1] == 'b'?
[*]And about that loop - that is an extremely inefficient and inflexible way to do it... How about this instead:
```

try:
    for y in xrange(0, 250, rblock.get_height()):
        for x in xrange(0, 600, rblock.get_width()):
            if barray[i] == 'r':
                blocks.append(block(rblock, x, y, 'r'))
            elif barray[i] == 'b':
                blocks.append(block(bblock, x, y))
            elif barray[i] == '_':
                blocks.append(sblock(sblocki, x, y))
            i += 1
except IndexError:
    pass

```
Note that this actually looks like what you would expect it to by looking at barray itself (note especially the part with '_', 'r', '_').
[*]The block classes could all be one class with slightly different parameters... perhaps you could do this with inheritance.
[*]The calculations for some collisions you do according to the top-left corner of an object. For example, the ball is out of the playing part of the screen on the right only when it's top left corner hits the side (which is probably why you made the playing screen wider than the blocks). How about this instead:
```

if self.x >= (600 - self.ball.get_width()):

```
Then you can make the playing screen as wide as the blocks.
[*]In the ball and block collisions you compare move_x to 4, but in reality it could be any of [2,3,4]. Really want you want to do is negate it:
```

ball.move_x = -ball.move_x

```
[*]Oh - and indentations, as mentioned above - Best Practice for Python is considered 4 spaces per indentation level. You can do a search-and-replace on the tabs and convert them to spaces (or let idle untabify it for you).
[/list]

As for why it flickers - I've been looking at it for a while and nothing pops out at me...

There are a bunch of things above that I would correct, but keep in mind that this is actually something that I think is really positive - that you just run forward and implement what you want, rather than stalling and asking lots of questions, etc. So don't get discouraged by the bugs :-).

---

### Post by matmatmat on 2009-07-23
Thanks for all the replies! I think the flickering might be just my screen.
I'm now going to do more kind of blocks.

---

### Post by lavinog on 2009-07-23
> **matmatmat said:**
> Thanks for all the replies! I think the flickering might be just my screen.
I'm now going to do more kind of blocks.

It flickered for me too.

you may want to look at [http://rene.f0o.com/mywiki/LectureThree](http://rene.f0o.com/mywiki/LectureThree)
look at the sections **Drawing the monkey onto the screen.** and **Fliping the display**

---

### Post by matmatmat on 2009-07-23
THe attached has most of the blocks that lbreakout has (it's missing TNT blocks & some that take 3 or 4 times to destory)

---

### Post by matmatmat on 2009-07-23
Any features that could/should be implemented?

---

### Post by lavinog on 2009-07-23
You could take advantage of object inheritance.
ex:
```


class Block:
    def fun1:
        ...
    def fun2:
        ...

class UnbreakableBlock(Block):
# don't need fun1 because fun1 here is the same as Block.fun1

    def fun2:
        ...

```
With this you can eliminate most of your if..elif statements and just make a class for each type of block. Especially since you are checking for the block type on every collision.


I would improve on your variable names.

---

### Post by lavinog on 2009-07-23
I converted the tabs to spaces, to make the code a little easier for everyone to read:
```

# -*- coding: utf-8 -*-
balli = "data/ball.png"
bati = "data/bat.png"

import pygame
from pygame.locals import *
from sys import exit
from random import randint
from sys import argv
class ballc:
    def __init__(self, ball):
        self.ball = ball
        self.x = 400
        self.y = 400
        self.rx = randint(2, 4)
        self.ry = randint(2, 4)
        self.move_x = -self.rx 
        self.move_y = -self.ry
        self.speed = 70
    def move(self, screen, time):
        self.rx = randint(2, 4)
        self.ry = randint(2, 4)
        self.x += self.move_x * self.speed * time
        self.y += self.move_y * self.speed * time
        screen.blit(self.ball, (self.x, self.y))
        if self.x >= (600 - self.ball.get_width()):
            self.move_x = -self.rx 
        if self.x <= 0:
            self.move_x = self.rx
        if self.y <= 0:
            self.move_y = self.ry
        if self.y >= 480:
            return False
        return True
    def coll(self, x, y, image):
        if (self.x >= x and self.x - self.ball.get_width() <= x + image.get_width()) and (self.y >= 470 - bat.get_height()):
            if self.move_x == 4:
                self.move_x = -4
            else:
                self.move_x = 4
            self.move_y = -4

class block:
    def __init__(self, block, x, y,name="",mustc=1):
        self.block = block
        self.x = x
        self.y = y
        self.name = name
        self.mustc = mustc
        self.c = 0
    def move(self, screen, time):
        screen.blit(self.block, (self.x, self.y))

    def coll(self, x, y, image, score, ball):
        if self.x <= x:
            if x <= self.x + self.block.get_width():
                if self.y <= y:
                    if y <= self.y + self.block.get_height():
                        self.c += 1
                        if self.c >= self.mustc:
                            if self.name == "b":
                                score += 1
                            elif self.name == "r":
                                score += 2
                            elif self.name == "2":
                                score += 5
                            elif self.name == "g":
                                score += 3
                            return True, score
                        elif self.name == "2":
                            self.block = pygame.image.load("data/22block.png")
                        elif self.name.startswith('t'):
                            if self.name.endswith('r'):
                                self.name = 'r'
                                self.block = pygame.image.load("data/rblock.png")
                            elif self.name.endswith('b'):
                                self.name = 'b'
                                self.block = pygame.image.load("data/bblock.png")
                            elif self.name.endswith('g'):
                                self.name = 'g'
                                self.block = pygame.image.load("data/gblock.png")
                            elif self.name.endswith('2'):
                                self.name = '2'
                                self.block = pygame.image.load("data/2block.png")

                        ball.move_x = -ball.move_x
                        ball.move_y = 4                 
                        
        return False, score

class sblock:
    def __init__(self, block, x, y, name=""):
        self.block = block
        self.x = x
        self.y = y
        self.name = name
    def move(self, screen, time):
        screen.blit(self.block, (self.x, self.y))
    def coll(self, x, y, image, score, ball):
        if self.x <= x:
            if x <= self.x + self.block.get_width():
                if self.y <= y:
                    if y <= self.y + self.block.get_height():
                        ball.move_x = -ball.move_x
                        ball.move_y = -ball.move_y
        return False, score

if len(argv) > 1:
    barray = []
    f = open(argv[1], "r")
    lines = f.readlines()
    for line in lines:
        for char in line:
            barray.append(char.strip())
else:
    barray = ["r","r","r","r","r","r","r","r","r","r","r","b","b","b","b","b","b","b","b","b","b","b", "!","_","r","b","r","b","r","b","r","_","!", "","","_","b","b","b","b","b","_","","","","","","_","r","r","r","_","","","","","","","","_","b","_","","","","", "2","2","2","2","2","2","2","2","2","2","2", "g","g","g","g","g","g","g","g","g","g","g", "!", "£", "$", "%", "!", "£","$","%","!","£","$"]

screen = pygame.display.set_mode((605,480), 0, 32)
clock = pygame.time.Clock()
ball = pygame.image.load(balli)
bat = pygame.image.load(bati)
i = 0
lastn = 0
lastn2 = 0
rblock = pygame.image.load("data/rblock.png")
bblock = pygame.image.load("data/bblock.png") 
sblocki = pygame.image.load("data/_block.png")
twoblock = pygame.image.load("data/2block.png")
gblock = pygame.image.load("data/gblock.png")
tblock = pygame.image.load("data/tblock.png")
blocks = []
score = 0
try:
    for y in xrange(0, 250, rblock.get_height()):
		for x in xrange(0, 605, rblock.get_width()):
			if barray[i] == 'r':
				blocks.append(block(rblock, x, y, 'r'))
			elif barray[i] == 'b':
				blocks.append(block(bblock, x, y, 'b'))
			elif barray[i] == '_':
				blocks.append(sblock(sblocki, x, y))
			elif barray[i] == '2':
				blocks.append(block(twoblock, x, y, "2", 2))
			elif barray[i] == 'g':
				blocks.append(block(gblock, x, y, 'g'))
			elif barray[i] == '!':
				blocks.append(block(tblock, x, y, 'tr', 2))
			elif barray[i] == '£':
				blocks.append(block(tblock, x, y, 'tb', 2)) 
			elif barray[i] == '$':
				blocks.append(block(tblock, x, y, 'tg', 2)) 
			elif barray[i] == '%':
				blocks.append(block(tblock, x, y, 't2', 3)) 
			i += 1
except IndexError:
    pass
y = 470 - bat.get_height()
yd = 0 
balls = ballc(ball)
while True:
    time_passed = clock.tick(30) / 1000.0
    screen.fill((255,255,255))
    for event in pygame.event.get():
        if event.type == QUIT:
            exit()
        
    for i in blocks:
        i.move(screen, time_passed)
        coll, score = i.coll(balls.x,balls.y,ball,score,balls)
        if coll:
            blocks.remove(i)
    x,yd = pygame.mouse.get_pos()
    x -= bat.get_width()/2
    screen.blit(bat, (x,y))
    balls.coll(x, y, ball)
    draw = balls.move(screen, time_passed)
    if not draw or len(blocks) == 0:
        print score
        exit()
    pygame.display.update()

```

I would suggest breaking your main code up into functions to make it easier to debug, and give feedback on areas that can use improvement.
I have never used pygame before, so I am learning alot from this thread too.
I think if you should be able to make a generic block image, and have the program color it for you. This would let you easily add any color block without having to make a new image.

Also like mentioned earlier you should set the screen resolution to match the block array

for the block array, break it up so it is readable and understandable:
```

    barray = [  "r","r","r","r","r","r","r","r","r","r","r",
                "b","b","b","b","b","b","b","b","b","b","b",
                "!","_","r","b","r","b","r","b","r","_","!",
                "" ,"" ,"_","b","b","b","b","b","_","" ,"" ,
                "" ,"" ,"" ,"_","r","r","r","_","" ,"" ,"" ,
                "" ,"" ,"" ,"" ,"_","b","_","" ,"" ,"" ,"" ,
                "2","2","2","2","2","2","2","2","2","2","2",
                "g","g","g","g","g","g","g","g","g","g","g",
                "!","£","$","%","!","£","$","%","!","£","$"]

```

---

### Post by lavinog on 2009-07-23
you should remove the excess random number picking when it isn't needed:
```

    def move(self, screen, time):
        self.rx = randint(2, 4)
        self.ry = randint(2, 4)
        self.x += self.move_x * self.speed * time
        self.y += self.move_y * self.speed * time
        screen.blit(self.ball, (self.x, self.y))
        if self.x >= (600 - self.ball.get_width()):
            self.move_x = -self.rx 
        if self.x <= 0:
            self.move_x = self.rx
        if self.y <= 0:
            self.move_y = self.ry
        if self.y >= 480:
            return False
        return True

``````

    def move(self, screen, time):
        self.x += self.move_x * self.speed * time
        self.y += self.move_y * self.speed * time
        screen.blit(self.ball, (self.x, self.y))
        if self.x >= (600 - self.ball.get_width()):
            self.move_x = randint(-4,-2)
        if self.x <= 0:
            self.move_x = randint(2,4)
        if self.y <= 0:
            self.move_y = randint(2,4)
        if self.y >= 480:
            return False
        return True

```

---

### Post by lavinog on 2009-07-24
I modified your code...entirely ;)
I used this as a opportunity to learn new things

Overall I don't think it is an improvement. If anything it may be more confusing.
line count:
  180 breakout.py
  568 mybreakout.py

---

### Post by matmatmat on 2009-07-25
> **lavinog said:**
> I modified your code...entirely ;)
Hmm, I can see where you've made changes,
everywhere
That's a lot of lines...

---

### Post by smartbei on 2009-07-25
@lavinog - I am kind of of the opinion you overdid it :-). Regardless, it doesn't work for me - actually, the behavior is a bit random. One time I started the game and the ball just went side to side, and the paddle followed it, out of my control. Another time the ball just went up and down, and when it hit the paddle it made a small dent in it, but again, I couldn't control the paddle.

Have you tried running it yourself?

---

### Post by matmatmat on 2009-07-25
Shouldn't the bat move by itself?

The file test.py has special blocks to help you win (eg adding another ball), but there is still the flicker, and some times the bat just stops!

---

### Post by lavinog on 2009-07-25
> **smartbei said:**
> @lavinog - I am kind of of the opinion you overdid it :-). Regardless, it doesn't work for me - actually, the behavior is a bit random. One time I started the game and the ball just went side to side, and the paddle followed it, out of my control. Another time the ball just went up and down, and when it hit the paddle it made a small dent in it, but again, I couldn't control the paddle.

Have you tried running it yourself?

I set it to play for me for testing purposes.
To enable bat control change line 529 from
```
        bat.move(screen,ball)
```
to:
```
        bat.move(screen)
```

I left the random movement as a feature.
```
  def move(self, screen, time,randfact=400):
        
        #randomize some movement
        rnd=randint(0,randfact)
        if rnd==0:
            self.move_y+=randint(-2,2)
            
        if rnd==1:
            self.move_x+=randint(-2,2)

```
The ball puts dents in everything. It has to do with not doing a full screen update.
I could try doing a full screen update on each collision, and do partial updates when the ball and bat move.

I want to look at using vectors for ball movement. This should make the ball movement more dynamic. Also use floats for ball velocity instead of integers. This should smooth out the ball movement.

I think the code became complicated because I was trying to avoid hard coding any dimensions. I tried to make it work with different sized images. Also some of the code is poorly designed workarounds for things like the transparent and doublebreak blocks. I am still learning about classes and inheritance.

---

