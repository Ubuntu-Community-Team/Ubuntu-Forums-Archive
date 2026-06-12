---
title: "Python Class help"
date: 2011-09-07
forum: Programming Talk
---

### Post by 42f87d89 on 2011-09-07
So, I've been trying to perfect my first ever "game" but I stumbled on a problem, whenever I try to call a class' function I get the error "TypeError: unbound method CharUpdate() must be called with Character instance as first argument (got nothing instead)" and I could find anything I could understand on how should I go about calling it, most of what I found where people "explaining" what is happening in programmer jargon. If anyone is willing to help here is the code.
```

import pygame, sys, os
from pygame.locals import *



isTrue = True
x = y = 0
screenX = 640
screenY = 360
screen = pygame.display.set_mode((screenX, screenY), 0, 32)

background = pygame.image.load("BG.png").convert()
background2 = pygame.image.load("BG2.png").convert()
background3 = pygame.image.load("BG3.png").convert()
background4 = pygame.image.load("BG4.png").convert()


pygame.init()

class Character:
    def __init__(self):
        #x22 y70
        UP = DOWN = LEFT = RIGHT = False
        xVel = yVel = 3
        self.CharRect =  pygame.Rect(x, y, 22, 70)
        self.Front = pygame.image.load("man.png").convert_alpha()
        self.Right = pygame.image.load("manRight.png").convert_alpha()
        self.Left = pygame.image.load("manLeft.png").convert_alpha()

    def Update():
        self.screen.blit(self.Front, (y ,x))
        if UP == True:
            x -= xVel

        if DOWN == True:
            x += xVel

        if LEFT == True:
            y -= yVel

        if RIGHT == True:
            y += yVel

while isTrue:
    screen.blit(background, (0 ,0))
    pygame.time.Clock().tick(40)
    Character.Update()

    for event in pygame.event.get(): #All the input of the game goes here

        if event.type == QUIT:
            isTrue = False
            sys.exit()

        if event.type == KEYDOWN:

            if event.key == K_w or event.key == K_UP:
                UP = True

            if event.key == K_s or event.key == K_DOWN:
                DOWN = True

            if event.key == K_a or event.key == K_LEFT:
                LEFT = True

            if event.key == K_d or event.key == K_RIGHT:
                RIGHT = True

        if event.type == KEYUP:

            if event.key == K_w or event.key == K_UP:
                UP = False

            if event.key == K_s or event.key == K_DOWN:
                DOWN = False

            if event.key == K_a or event.key == K_LEFT:
                LEFT = False

            if event.key == K_d or event.key == K_RIGHT:
                RIGHT = False

        
    pygame.display.update()

```

---

### Post by ziekfiguur on 2011-09-07
To use a class function you have to instantiate an object of that class and call the function on that object, like so:```
c = Character()
c.Update()
```
You'll probably want to create the object outside of the while loop and update it inside the loop.

---

### Post by 42f87d89 on 2011-09-07
> **ziekfiguur said:**
> To use a class function you have to instantiate an object of that class and call the function on that object, like so:```
c = Character()
c.Update()
```You'll probably want to create the object outside of the while loop and update it inside the loop.
Wow! Thank you for the quick response. I did what you said but it gave me an error, so I removed the parenthesis on "C.Update" and it seemingly fixed it.

---

### Post by 42f87d89 on 2011-09-07
[QUOTE=ziekfiguur]snip[/QUOTE]
Ok, now it seems like it doesn't do anything at all, is doesn't add x and xvel nor blits the screen. Can you help me once again?```
import pygame, sys, os
from pygame.locals import *



isTrue = True
x = y = 0
screenX = 640
screenY = 360
screen = pygame.display.set_mode((screenX, screenY), 0, 32)

background = pygame.image.load("BG.png").convert()
background2 = pygame.image.load("BG2.png").convert()
background3 = pygame.image.load("BG3.png").convert()
background4 = pygame.image.load("BG4.png").convert()


pygame.init()

class Character:
    def __init__(self):
        #x22 y70
        UP = DOWN = LEFT = RIGHT = False
        xVel = yVel = 3
        self.CharRect =  pygame.Rect(x, y, 22, 70)
        self.Front = pygame.image.load("man.png").convert_alpha()
        self.Right = pygame.image.load("manRight.png").convert_alpha()
        self.Left = pygame.image.load("manLeft.png").convert_alpha()

    def Update(self):
        self.screen.blit(Front, (y ,x))
        if UP == True:
            x -= xVel

        if DOWN == True:
            x += xVel

        if LEFT == True:
            y -= yVel

        if RIGHT == True:
            y += yVel
Character = Character()

while isTrue:
    screen.blit(background, (0 ,0))
    pygame.time.Clock().tick(40)
    Character.Update

    for event in pygame.event.get(): #All the input of the game goes here

        if event.type == QUIT:
            isTrue = False
            sys.exit()

        if event.type == KEYDOWN:

            if event.key == K_w or event.key == K_UP:
                UP = True

            if event.key == K_s or event.key == K_DOWN:
                DOWN = True

            if event.key == K_a or event.key == K_LEFT:
                LEFT = True

            if event.key == K_d or event.key == K_RIGHT:
                RIGHT = True

        if event.type == KEYUP:

            if event.key == K_w or event.key == K_UP:
                UP = False

            if event.key == K_s or event.key == K_DOWN:
                DOWN = False

            if event.key == K_a or event.key == K_LEFT:
                LEFT = False

            if event.key == K_d or event.key == K_RIGHT:
                RIGHT = False

        
    pygame.display.update()

```

---

### Post by Smart Viking on 2011-09-07
In the class, preface variables that are used outside of __init__ with "self.".

How does self.update know what UP, DOWN and LEFT and RIGHT are? It doesn't. They aren't defined in the class.

"Character.Update" does *nothing*, you need to use "Character.Update()". It gives an error because self.Update does not work, so that was more of a ditch than a fix.

---

### Post by cgroza on 2011-09-07
When you removed the brackets, you did not fixed it. You just did not call the function.
The expression:
```

c.Update

```
returns a function.
The expression:
```

c.Update()

```
calls the function, which is what you want.

---

### Post by 42f87d89 on 2011-09-08
Thanks everyone, now I have only one last problem, even though the blitting works, the character doesn't move

EDIT: Never mind, I figured it out.

---

