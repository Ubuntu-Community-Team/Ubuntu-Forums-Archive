---
title: "eed help with programming in Python. Can you tell me what's wrong with this code?"
date: 2010-01-03
forum: Programming Talk
---

### Post by zosolm on 2010-01-03
I'm very new to programming, so please forgive me. It's a simple program I'm trying to make but I'm rubbish. When I run a module check, it doesn't show any errors, but when I actually try to run the program, a blank window appears.
Here's the code:

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
            self.vx = 0
            self.vy = -1
        elif event.key == pygame.K_DOWN:
                self.vx = 0
                self.vy = 1
        elif event.key == pygame.K_LEFT:
                self.vx = -1
                self.vy = 0
        elif event.key == pygame.K_RIGHT:
                self.vx = 1
                self.vy = 0

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
        for x, y in self.body:
            self.surface.set_at((x, y), self.color)
                        
    def position(self):
        return self.x, self.y

class food:
    def __init__(self, surface):
        self.surface = surface
        self.x = random.randint(0, surface.get_width())
        self.y = random.randint(0, surface.get_width())
        self.color = 255, 255, 255

    def draw(self):
        self.surface.set_at((self.x, self.y), self.color)

    def position(self):
        return self.x, self.y

w = 500
h = 500

screen = pygame.display.set_mode((w, h))
clock = pygame.time.Clock()

score = 0
worm = worm(screen)
food = food(screen)
running = True

while running:
    screen.fill((0, 0, 0))
    worm.move()
    worm.draw()
    food.draw()

    if worm.crashed:
        running = False
    elif worm.x <= 0 or worm.x >= w - 1:
        running = False
    elif worm.y <= 0 or worm.y >= h - 1:
        running = False
    elif worm.position() == food.position():
        score += 1
        worm.eat()
        print "Score %d" % score
        food = Food(screen)

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.KEYDOWN:
            worm.event(event)

    pygame.display.flip()
    clock.tick(240)





(And the original post: [http://ubuntuforums.org/showthread.php?t=1371301](http://ubuntuforums.org/showthread.php?t=1371301))
Help!
P.s. I posted this thread in Gaming and Leisure before i realized there was a programming forum, so sorry if this causes inconvenience. not sure how it would, but just in case...

---

### Post by froggyswamp on 2010-01-03
I know what's wrong with it! - it doesn't work as expected!

---

### Post by unknownPoster on 2010-01-03
I'd recommend that you wrap your code with the "code" tags.

With Python, formatting is paramount and that could be part of your issue but it's difficult to tell without your intended formatting...

---

### Post by wmcbrine on 2010-01-03
One trivial point: That first line, "#! usr/bin/env python", should instead be "#!/usr/bin/env python".

These lines:

```
worm = worm(screen)
food = food(screen)
```

trouble me -- by doing this, you render the original worm and food inaccessible. I'd suggest capitalizing the class names. But I don't think these are your problem.

Edit: Oh, it's even worse in event(). Seriously, stop reusing identifiers, it's bad.

Please describe in more detail what you expect the program to do.

---

### Post by wmcbrine on 2010-01-03
OK, where you have:

```

        if (self.x, self.y) in self.body:
            self.crashed = True

            self.body.insert(0, (self.x, self.y))

```

I believe what you were going for is:

```

        if (self.x, self.y) in self.body:
            self.crashed = True

        self.body.insert(0, (self.x, self.y))

```

The insert line is in the wrong block. With this change, it works for me.

---

### Post by zosolm on 2010-01-31
after changing the block, it works!! This is the first thing I've ever programmed, so i don't really understand why that made such a difference? And what's the alternative to using identifiers so often?
Actually, there seems to be another fault with it..
When I run it, the worm appears and can be controlled fine, but when he eats the food, the game just stops.
I'll post the code that runs with this fault.
Thanks!

---

### Post by zosolm on 2010-01-31
Here's the code that runs but crashes when the worm eats the food.
```

#! usr/bin/env python

# A simple worm game.

import pygame
import random

class worm:
    def __init__(self,surface):
        self.surface = surface
        self.x = surface.get_width() / 2
        self.y = surface.get_height() / 6
        self.length = 10
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
            self.vx = 0
            self.vy = -1
        elif event.key == pygame.K_DOWN:
                self.vx = 0
                self.vy = 1
        elif event.key == pygame.K_LEFT:
                self.vx = -1
                self.vy = 0
        elif event.key == pygame.K_RIGHT:
                self.vx = 1
                self.vy = 0

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
        for x, y in self.body:
            self.surface.set_at((x, y), self.color)
                        
    def position(self):
        return self.x, self.y

class food:
    def __init__(self, surface):
        self.surface = surface
        self.x = random.randint(0, surface.get_width())
        self.y = random.randint(0, surface.get_width())
        self.color = 0, 255, 255

    def draw(self):
        self.surface.set_at((self.x, self.y), self.color)

    def position(self):
        return self.x, self.y

w = 500
h = 500

screen = pygame.display.set_mode((w, h))
clock = pygame.time.Clock()

score = 0
worm = worm(screen)
food = food(screen)
running = True

while running:
    screen.fill((0, 0, 0))
    worm.move()
    worm.draw()
    food.draw()

    if worm.crashed:
        running = False
    elif worm.x <= 0 or worm.x >= w - 1:
        running = False
    elif worm.y <= 0 or worm.y >= h - 1:
        running = False
    elif worm.position() == food.position():
        score += 1
        worm.eat()
        print "Score %d" % score
        food = Food(screen)

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.KEYDOWN:
            worm.event(event)

    pygame.display.flip()
    clock.tick(240)


```

I've messed around with the colour of the worm and food but that's all.
Thanks.

---

### Post by Can+~ on 2010-01-31
Very difficult, the "food" is 1px and is really hard to hit.

Also, if you're moving in a direction, and click the exact opposite direction of movement (say, you're moving right, and you click 'left') you lose instantly.

And once I actually grabbed the "food" I got:

[PHP]Score 1
Traceback (most recent call last):
  File "worms.py", line 103, in <module>
    food = Food(screen)
NameError: name 'Food' is not defined[/PHP]

It's good for a first program, 'though.

---

### Post by zosolm on 2010-01-31
I have defined it, though  (haven't i?):

class food:
    def __init__(self, surface):
        self.surface = surface
        self.x = random.randint(0, surface.get_width())
        self.y = random.randint(0, surface.get_width())
        self.color = 0, 255, 255

    def draw(self):
        self.surface.set_at((self.x, self.y), self.color)

    def position(self):
        return self.x, self.
I don't understand. I've defined it here ( I think ) and Python tells us that 'Food' isn't defined?
Is it because i've not capitalised the word 'food' here?

---

### Post by zosolm on 2010-01-31
```
class food:
    def __init__(self, surface):
        self.surface = surface
        self.x = random.randint(0, surface.get_width())
        self.y = random.randint(0, surface.get_width())
        self.color = 0, 255, 255

    def draw(self):
        self.surface.set_at((self.x, self.y), self.color)

    def position(self):
        return self.x, self.
```

Sorry,  I keep forgetting to wrap the code.

---

### Post by Can+~ on 2010-01-31
Python is case sensitive, name your class like:

[PHP]class Food:[/PHP]

And since we're at it, you should always define classes as:

[PHP]class Food(object):[/PHP]

---

### Post by MaxIBoy on 2010-02-01
> **zosolm said:**
> after changing the block, it works!! This is the first thing I've ever programmed, so i don't really understand why that made such a difference? And what's the alternative to using identifiers so often?Python is NOT a free-form language, meaning that the indentation actually matters to how the code executes. (This is fairly unusual, but it's part of what makes Python so readable.)

In Python, if two lines come one after another (not counting blank lines,) and they have the same indentation amount, they are grouped together in the same ["block."]("http://en.wikipedia.org/wiki/Block_%28programming%29") The "if" statement is a [control structure]("http://en.wikipedia.org/wiki/Control_structure"), more specifically a [conditional statement]("http://en.wikipedia.org/wiki/Conditional_%28programming%29") which controls whether or not the following block is run.


So in this piece:```
        if (self.x, self.y) in self.body:
            self.crashed = True

            self.body.insert(0, (self.x, self.y))
```
This is the block:```
            self.crashed = True

            self.body.insert(0, (self.x, self.y))
```
This is the if statement:```
        if (self.x, self.y) in self.body:
```
Which checks if the result of this operation is "true," or "yes" if you prefer: ```
(self.x, self.y) in self.body
```
And if it is true, it will run the above block. 

That code doesn't do what you want it to, because the "self.body.insert" code will **only** run if (self.x, self.y) actually is in self.body.

---

### Post by zosolm on 2010-02-02
Thank you both! 
i'm learning much more about Python..
I've altered the code a little bit, making the food a little bigger and making the controls easier. I can't figure out why, but when the worm eats the food, it crashes and doesn't 'eat' the food as i thought i'd told it to. Also, the food doesn't 'erase' and 'return' eiyjther, even though i asked it to.
This is undoubtedly down to my error, but please help!
here's the new code. (I've marked some of the lines with a '#' so that they don't effect the program but allow me to see previous mistakes i made)

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
        elif event.key == pygame.K_DOWN:
            if self.vy == -1: return
            self.vx = 0
            self.vy = 1
        elif event.key == pygame.K_LEFT:
            if self.vx == 1: return
            self.vx = -1
            self.vy = 0
        elif event.key == pygame.K_RIGHT:
            if self.vx == -1: return
            self.vx = 1
            self.vy = 0

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

class food(object):
    def __init__(self, surface):
        self.surface = surface
        self.x = random.randint(0, surface.get_width())
        self.y = random.randint(0, surface.get_height())
        self.color = 0, 255, 255

    def draw(self):
        pygame.draw.rect(self.surface, self.color, (self.x, self.y, 3, 3), 0)

    def erase(self):
        pygame.draw.rect(self.surface, (0, 255, 255), (self.x, self.y, 3, 3), 0)

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
worm = worm(screen)
food = food(screen)
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

```


Can+~, where you told me to make ```
class Food:
``` into ```
class Food(object):  
```, that helped. I imagine i ought  to have  done a similar thing when i created the 'worm' class. is that (object) too? or something else?

I know there's probably a whole lot of other problems with it too :/
Thanks![COLOR=#000000][COLOR=#007700][/COLOR][COLOR=#0000BB][/COLOR][COLOR=#007700]
[/COLOR][/COLOR]

---

### Post by zosolm on 2010-02-02
just to clarify, the worm crashes into the food.

---

### Post by zosolm on 2010-02-07
i've fixed it up quite a bit and actually had it working fine for a short while.
then I altered something (i don't remember what :[ )  and now the worm is drawn already crashed.
:S

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

I can't figure out what's wrong with it

---

### Post by zosolm on 2010-03-14
I've got it working! prettier, too.

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
```

If there's anything wrong with it let me know

---

