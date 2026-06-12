---
title: "Python and Pygame - Drawing 1000 Lines"
date: 2013-10-14
forum: Programming Talk
---

### Post by mhaggard25 on 2013-10-14
I am trying to learn Python and Pygame and I'm having a small problem. First, I'll explain what I am doing:

"Take one of the examples (which I will provide) and modify it so that 1,000 objects are drawn with random values. Look at the random library and the random.randint() function."

Here is the example:

```
# Drawing Lines

import pygame
from pygame.locals import *
pygame.init()


screen = pygame.display.set_mode((600, 500))
pygame.display.set_caption("Drawing Lines")


while True:
    for even in pygame.event.get():
        if even.type in (QUIT, KEYDOWN):
            sys.exit()
            
    screen.fill((0, 80, 0))
    
    #Draw the line
    color = 100, 255, 200
    width = 8
    pygame.draw.line(screen, color, (100, 100), (500, 400), width)
    
    pygame.display.update()
```

Here is what I have so far:

```
# Drawing Lines

import random
import pygame
from pygame.locals import *
pygame.init()


screen = pygame.display.set_mode((600, 500))
pygame.display.set_caption("Drawing Lines")


while True:
    for even in pygame.event.get():
        if even.type in (QUIT, KEYDOWN):
            sys.exit()
            
    screen.fill((0, 80, 0))
    
    #Draw the line
    color = 100, 255, 200
    width = 8
    
    pygame.draw.line(screen, color, (random.randint(0, 600), random.randint(0,500)), (random.randint(0, 500), random.randint(0, 400)), width)
        
    pygame.display.update()
```

I know what I have done isn't correct and I have made some changes since my original idea didn't work. This code just continues to create lines in random places, but seems to never have a stopping point. It just keeps creating and destroying forever. I'm not looking for a solution, I'm just looking for a point in the right direction. Thanks in advance!

---

### Post by r-senior on 2013-10-14
I pasted your code and it stopped on a keypress (Python 2.7.3 on Ubuntu 12.04). Not a graceful exit, but an exit:

```
$ python lines.py
Traceback (most recent call last):
  File "lines.py", line 14, in <module>
    sys.exit()
NameError: name 'sys' is not defined

```

Obviously that's easily fixed with an import.

Are you sure the window is focussed when you press a key?

---

### Post by mhaggard25 on 2013-10-16
Ha the exit thing is easily fixed with spelling "event.type" correctly. I only put "even. type" that's why that's there. Sorry about that one. I'll fixed that immediately. Thanks for pointing out that error though! I didn't even notice it.

---

