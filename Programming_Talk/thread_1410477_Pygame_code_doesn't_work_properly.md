---
title: "Pygame code doesn't work properly"
date: 2010-02-18
forum: Programming Talk
---

### Post by zosolm on 2010-02-18
I've written this in python and had it running for a while..
the 'worm' is supposed to 'eat' the 'food', which is then to re appear in a random position. However, I changed something a while ago (and don't remember what :() and now the worm starts off already crashed.
can't figure it out. it's my first code, so i know there'll be problems and feedback is always useful (:

Code:

```
 #!/usr/bin/env python

# A simple worm game.

import pygame
import random

class Worm:
    def __init__(self,surface):
        self.surface = surface
        self.x = surface.get_width() / 2
        self.y = surface.get_height() / 2
        self.length = 1
        self.grow_to = 50
        self.vx = 0
        self.vy = -1
        self.body = []
        self.crashed = False
        self.color = 225, 225, 0

    def eat(self):
        self.grow_to += 25

    def event(self, event):
        """ Handle keyboard events. """
        if event.key == pygame.K_UP:
            if self.vy == 1: return
            self.vx = 0
            self.vy = -1
            worm.color = 225, 225, 0
        elif event.key == pygame.K_DOWN:
            if self.vy == -1: return
            self.vx = 0
            self.vy = 1
            worm.color = 0, 225, 225
        elif event.key == pygame.K_LEFT:
            if self.vx == 1: return
            self.vx = -1
            self.vy = 0
            worm.color = 225, 0, 225
        elif event.key == pygame.K_RIGHT:
            if self.vx == -1: return
            self.vx = 1
            self.vy = 0
            worm.color = 0, 225, 0

    def move (self):
        """ Move the worm. """
        self.x += self.vx
        self.y += self.vy

        if (self.x, self.y) in self.body:
            self.crashed = True

        self.body.insert(0,(self.x, self.y))

        if (self.grow_to > self.length):
            self.length += 1

        if len(self.body) > self.length:
            self.body.pop()

    def draw(self):
        #for x, y in self.body:
        #   self.surface.set_at((x,y), self.color)
        x, y = self.body[0]
        self.surface.set_at((x, y), self.color)
        x, y = self.body[-1]
        self.surface.set_at((x, y),(0, 0, 0))
        
    def position(self):
        return self.x, self.y

class Food(object):
    def __init__(self, surface):
        self.surface = surface
        self.x = random.randint(0, surface.get_width())
        self.y = random.randint(0, surface.get_height())
        self.color = 0, 255, 255

    def draw(self):
        pygame.draw.rect(self.surface, self.color, (self.x, self.y, 3, 3), 0)

    def erase(self):
        pygame.draw.rect(self.surface, (0, 0, 0), (self.x, self.y, 3, 3), 0)

    def check(self, x, y):
         if x < self.x or x > self.x + 3:
            return False
         elif y < self.y or y > self.y + 3:
            return False
         else:
            return True    

    def position(self):
        return self.x, self.y

w = 1000
h = 1000

screen = pygame.display.set_mode((w, h))
clock = pygame.time.Clock()

score = 0
worm = Worm(screen)
food = Food(screen)
running = True

while running:
    #screen.fill((0, 0, 0))
    worm.move()
    worm.draw()
    food.draw()

    if worm.crashed:
        running = False      
    elif worm.x <= 0 or worm.x >= w - 1:
        running = False
    elif worm.y <= 0 or worm.y >= h - 1:
        running = False
    elif food.check(worm.x, worm.y):
        score += 1
        print "Score %d" % score
        worm.eat()
        food.erase()
        food = Food(screen)

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
            
pygame.display.flip()
clock.tick(240)
```

Thanks.

---

### Post by zosolm on 2010-03-14
Anybody? please help /:

---

### Post by nvteighen on 2010-03-14
One error I see is the following: it checks whether it crashed against itself or not by checking if the new position to which it has moved is "inside" the body... This means that it will always crash because no matter where the worm is the coordinate will always be in its body :p

You have to check before performing the move and then, if valid, allow it... if not, crash.

---

### Post by gmargo on 2010-03-14
Here's a working version of that tutorial code: [http://lorenzod8n.wordpress.com/2008/03/01/pygame-tutorial-9-first-improvements-to-the-game/](http://lorenzod8n.wordpress.com/2008/03/01/pygame-tutorial-9-first-improvements-to-the-game/)

---

### Post by zosolm on 2010-03-15
Thanks!
I got it working last night, though, after much pulling of hair.
i didn't actually find the problem; i found a simpler, working version of the game that i'd saved and just changed that.
It's *does* help to know what the problem is, though.


```
#! usr/bin/env python

# A simple worm game.

import pygame
import random

class worm:
    def __init__(self,surface):
        self.surface = surface
        self.x = surface.get_width() / 2
        self.y = surface.get_height() / 2
        self.length = 1
        self.grow_to = 50
        self.vx = 0
        self.vy = -1
        self.body = []
        self.crashed = False
        self.color = 225, 225, 0


    def eat(self):
        self.grow_to +=25

    def event(self, event):
        """ Handle keyboard events. """
        if event.key == pygame.K_UP:
            if self.vy == 1: return
            self.vx = 0
            self.vy = -1
            worm.color = 225, 225, 0
        elif event.key == pygame.K_DOWN:
            if self.vy == -1: return
            self.vx = 0
            self.vy = 1
            worm.color = 0, 225, 225
        elif event.key == pygame.K_LEFT:
            if self.vx == 1: return
            self.vx = -1
            self.vy = 0
            worm.color = 225, 0, 225
        elif event.key == pygame.K_RIGHT:
            if self.vx == -1: return
            self.vx = 1
            self.vy = 0
            worm.color = 0, 225, 0
        if event.key == pygame.K_RETURN:
            paused = True


    def move (self):
        """ Move the worm. """
        self.x += self.vx
        self.y += self.vy

        if (self.x, self.y) in self.body:
            self.crashed = True

        self.body.insert(0, (self.x, self.y))

        if (self.grow_to > self.length):
            self.length += 1

        if len(self.body) > self.length:
            self.body.pop()

    def draw(self):
        #for x, y in self.body:
        #   self.surface.set_at((x,y), self.color)
        x, y = self.body[0]
        self.surface.set_at((x, y), self.color)
        x, y = self.body[-1]
        self.surface.set_at((x, y), (0, 0, 0))
        
    def position(self):
        return self.x, self.y
        

class Food(object):
    def __init__(self, surface):
        self.surface = surface
        self.x = random.randint(0, surface.get_width())
        self.y = random.randint(0, surface.get_height())
        self.color = random.randint(0,255), random.randint(0,255), random.randint(0,255)


    def draw(self):
        pygame.draw.rect(self.surface, self.color, (self.x, self.y, 5, 5), 0)

    def erase(self):
        pygame.draw.rect(self.surface, (0, 0, 0), (self.x, self.y, 5, 5), 0)

    def check(self, x, y):
        if x < self.x or x > self.x + 5:
            return False
        elif y < self.y or y > self.y + 5:
            return False
        else:
            return True

    def position(self):
        return self.x,self.y

w = 500
h = 500

screen = pygame.display.set_mode((w, h))
clock = pygame.time.Clock()

score = 0
worm = worm(screen)
food = Food(screen)
running = True

while running:
    #screen.fill((0, 0, 0))
    worm.move()
    worm.draw()
    food.draw()

    if worm.crashed:
        running = False
    elif worm.x <= 0 or worm.x >= w - 1:
        running = False
    elif worm.y <= 0 or worm.y >= h - 1:
        running = False
    elif food.check(worm.x, worm.y):
        score += 1
        worm.eat()
        print "Score %d" % score
        food.erase()
        food = Food(screen)
        
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.KEYDOWN:
            worm.event(event)

    pygame.display.flip()
    clock.tick(240)

```Does anybody know how to add a pause button?
I've had a look online but all i can find is the time.delay thing, but can't figure out how to attribute that to pressing a key..

Thanks again!

---

### Post by gmargo on 2010-03-15
> **zosolm said:**
> i didn't actually find the problem; i found a simpler, working version of the game that i'd saved and just changed that.
It's *does* help to know what the problem is, though.


Do a diff between the first version you posted, and the one you just posted, and the reason for the problem becomes obvious.  It's the indentation of these two lines:
```

    pygame.display.flip()
    clock.tick(240)

```Indentation is crucial in Python.  Indent those two lines and the program starts to work. The other problem is that the key handling for KEYDOWN wasn't there so you can't drive the worm.

---

### Post by gmargo on 2010-03-15
> **zosolm said:**
> Does anybody know how to add a pause button?
I've had a look online but all i can find is the time.delay thing, but can't figure out how to attribute that to pressing a key.

I managed to add a pause button. I won't post the whole thing, just what I changed from your last post:

[LIST=1]
[*]Removed the K_RETURN handling in the worm class.
[*]Added a global "paused" variable, and used it to limit the calling of the worm.move() method.
[*]Added pause key detection in the main event loop.
[/LIST]
  Here's just the main running loop:
```

score = 0
worm = worm(screen)
food = Food(screen)
running = True
**paused = False**

while running:
    #screen.fill((0, 0, 0))
[B]    if not paused:
        worm.move()[/B]
    worm.draw()
    food.draw()

    if worm.crashed:
        running = False
    elif worm.x <= 0 or worm.x >= w - 1:
        running = False
    elif worm.y <= 0 or worm.y >= h - 1:
        running = False
    elif food.check(worm.x, worm.y):
        score += 1
        worm.eat()
        print "Score %d" % score
        food.erase()
        food = Food(screen)

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
[B]        elif event.type == pygame.KEYDOWN and event.key == pygame.K_RETURN:
            paused = not paused[/B]
        elif event.type == pygame.KEYDOWN:
            worm.event(event)

    pygame.display.flip()
    clock.tick(240)


```

This may not be the best method for pausing.  I just realized that you can still turn the worm while paused.

---

