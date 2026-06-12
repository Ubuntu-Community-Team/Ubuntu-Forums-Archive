---
title: "Pygame Collision Detection Errors"
date: 2011-02-19
forum: Programming Talk
---

### Post by colts18 on 2011-02-19
Hey guys I am adding collision detection to my first game I am making and cannot figure out what these errors mean I also might be missing a line or two in my code.  Since this is my first time I am not sure if I am doing it right does any one know?

This is the error message:

Traceback (most recent call last):
  File "/home/bolt/Python/game.py", line 87, in <module>
    enemy_tank = Enemy_tank()
  File "/home/bolt/Python/game.py", line 52, in __init__
    self.rect = self.Enemy_Tank.get_rect()
AttributeError: 'Enemy_tank' object has no attribute 'Enemy_Tank'


This is my code:

```
import pygame
                                          
class Tank(pygame.sprite.Sprite):

        def __init__(self):                                     
                self.Tank = pygame.image.load("tank.png")       
                self.x = -200
                self.y = 20
                self.firecountdown=0
                self.rect = self.Tank.get_rect()

        def draw(self, surface):
                surface.blit(self.Tank, (self.x, self.y))                                           
        def update(self, dt):
                if(self.firecountdown > 0):
                        self.firecountdown-= dt
        def fire(self, bullet):
                if(self.firecountdown <=0) :
                        bullet.x = self.x
                        bullet.y = self.y
                        bullet.fired = True     
                        bullet.speed = 10
                        self.firecountdown = 1000
                        

class Bullet(pygame.sprite.Sprite):
        def __init__(self):
                self.bullet = pygame.image.load("tank_bullet.png")
                self.y = 0
                self.x = 0
                self.speed = 0
                self.forwardx = 1
                self.forwardy = 0
                self.fired = False      
        def draw(self, surface):
                surface.blit(self.bullet, (self.x, self.y))
        def update(self, dt):
                self.x += self.forwardx * self.speed 
                self.y += self.forwardy * self.speed 
                if self.x > 640:        
                        self.fired = False
                        
class Lvl_1:
        def __init__(self):
                self.floor = pygame.image.load("floor.png")
        def draw(self, surface):
                surface.blit(self.floor, (0, 0))

class Enemy_tank(pygame.sprite.Sprite):
        def __init__(self):
                self.enemy_tank = pygame.image.load("enemy_tank.png")
                self.rect = self.Enemy_Tank.get_rect()
        def draw(self, surface):
                surface.blit(self.enemy_tank, (200, -40))
        def update(self, dt):
                return
        
class Enemy_bullet:
        
        def __init__(self):
                self.enemy_bullet = pygame.image.load("enemy_bullet.png")
                self.y = 0
                self.x = 0
                self.speed = 0
                self.forwardx = 1
                self.forwardy = 0
                self.fired = False
        def draw(self, surface):
                surface.blit(self.enemy_bullet, (self.x, self.y))
        def update(self, dt):
                self.x += self.forwardx * self.speed
                self.y += self.forwardy * self.speed
                if self.x > 640:
                        self.fired = False

                        

pygame.init()                                                           
background_color = (0,0,0)                                              
(width, height) = (640, 480)                                    
screen = pygame.display.set_mode((width, height))                       
pygame.display.set_caption('Game Window')                       
clock = pygame.time.Clock()
dt = clock.tick(30)
lvl_1 = Lvl_1()
bullet = Bullet()
enemy_tank = Enemy_tank()
Tank = Tank()
enemy_bullet = Enemy_bullet()
pygame.key.set_repeat(1,50)                                     
running = True

while running:
        if pygame.sprite.collide_rect(Tank, Enemy_tank):
                tank.x =+ 0
                
        Tank.update(dt)           
        bullet.update(dt)       

        screen.fill (background_color)                          
        Tank.draw(screen)       
        lvl_1.draw(screen)
        if bullet.fired == True:        
                bullet.draw(screen)
        enemy_tank.draw(screen)
        if tank_collide == True:
                tank.x =+ 0

        pygame.display.flip()                                   
        clock.tick(30)                                          

        for event in pygame.event.get():                        


                if event.type == pygame.QUIT:                           
                        running = False
                elif event.type == pygame.KEYDOWN:
                        if event.key == pygame.K_RIGHT:
                                Tank.x += 5
                        if event.key == pygame.K_LEFT:
                                Tank.x -= 5                             
                        if event.key == pygame.K_SPACE:
                                Tank.fire(bullet)       


```

---

### Post by Tony Flury on 2011-02-19
This is a pretty Simple error to fix.

Line 52 is in the __init__ method of the Enemy_tank class - so self is already an instance of the Enemy_tank class.

your Class has a enemy_tank attribute - and not Enemy_tank (case is relevant in python).

---

### Post by colts18 on 2011-02-19
Ok I got another error I think I screwed up this line:

```
self.rect = self.get_rect()
```

but I am not sure here is the error:

Traceback (most recent call last):
  File "/home/bolt/Python/game.py", line 87, in <module>
    enemy_tank = Enemy_tank()
  File "/home/bolt/Python/game.py", line 52, in __init__
    self.rect = self.get_rect()
AttributeError: 'Enemy_tank' object has no attribute 'get_rect'

---

### Post by cgroza on 2011-02-19
> **colts18 said:**
> Ok I got another error I think I screwed up this line:

```
self.rect = self.get_rect()
```but I am not sure here is the error:

Traceback (most recent call last):
  File "/home/bolt/Python/game.py", line 87, in <module>
    enemy_tank = Enemy_tank()
  File "/home/bolt/Python/game.py", line 52, in __init__
    self.rect = self.get_rect()
AttributeError: 'Enemy_tank' object has no attribute 'get_rect'

The class Enemy_tank has no method called get_rect, is that supposed to be inherited from pygame?
EDIT: just checked some documentation and get_rect is not a member of Sprite, so you need to define it.

---

### Post by Tony Flury on 2011-02-19
try : 

```

self.rect = self.enemy_tank.get_rect()

```

You might be getting confused as your enemy_tank attribute is the actually pygame surface of your Enemy_tank class - bad idea to have two similarly named things in my opinion.

---

### Post by colts18 on 2011-02-19
Well I have tried your line but still no luck and I have tried many other different changes but I still get this error I am thinking I have an entire line missing that defines something but I don't know what needs to be defined for it to create a rect.

Traceback (most recent call last):
  File "/home/bolt/Python/game.py", line 94, in <module>
    if pygame.sprite.collide_rect(Tank, Enemy_tank):
  File "/usr/lib/python2.6/dist-packages/pygame/sprite.py", line 1147, in collide_rect
    return left.rect.colliderect(right.rect)
AttributeError: type object 'Enemy_tank' has no attribute 'rect'

Here is the code:

```
import pygame
                                          
class Tank(pygame.sprite.Sprite):

        def __init__(self):                                     
                self.Tank = pygame.image.load("tank.png")       
                self.x = -200
                self.y = 20
                self.firecountdown=0
                self.rect = self.Tank.get_rect()

        def draw(self, surface):
                surface.blit(self.Tank, (self.x, self.y))                                           
        def update(self, dt):
                if(self.firecountdown > 0):
                        self.firecountdown-= dt
        def fire(self, bullet):
                if(self.firecountdown <=0) :
                        bullet.x = self.x
                        bullet.y = self.y
                        bullet.fired = True     
                        bullet.speed = 10
                        self.firecountdown = 1000
                        

class Bullet(pygame.sprite.Sprite):
        def __init__(self):
                self.bullet = pygame.image.load("tank_bullet.png")
                self.y = 0
                self.x = 0
                self.speed = 0
                self.forwardx = 1
                self.forwardy = 0
                self.fired = False      
        def draw(self, surface):
                surface.blit(self.bullet, (self.x, self.y))
        def update(self, dt):
                self.x += self.forwardx * self.speed 
                self.y += self.forwardy * self.speed 
                if self.x > 640:        
                        self.fired = False
                        
class Lvl_1:
        def __init__(self):
                self.floor = pygame.image.load("floor.png")
        def draw(self, surface):
                surface.blit(self.floor, (0, 0))

class Enemy_tank(pygame.sprite.Sprite):
        def __init__(self):
                self.enemy_tank = pygame.image.load("enemy_tank.png")
                self.rect = self.enemy_tank.get_rect()
        def draw(self, surface):
                surface.blit(self.enemy_tank, (200, -40))
        def update(self, dt):
                return
        
class Enemy_bullet(pygame.sprite.Sprite):
        
        def __init__(self):
                self.enemy_bullet = pygame.image.load("enemy_bullet.png")
                self.y = 0
                self.x = 0
                self.speed = 0
                self.forwardx = 1
                self.forwardy = 0
                self.fired = False
        def draw(self, surface):
                surface.blit(self.enemy_bullet, (self.x, self.y))
        def update(self, dt):
                self.x += self.forwardx * self.speed
                self.y += self.forwardy * self.speed
                if self.x > 640:
                        self.fired = False

                        

pygame.init()                                                           
background_color = (0,0,0)                                              
(width, height) = (640, 480)                                    
screen = pygame.display.set_mode((width, height))                       
pygame.display.set_caption('Game Window')                       
clock = pygame.time.Clock()
dt = clock.tick(30)
lvl_1 = Lvl_1()
bullet = Bullet()
enemy_tank = Enemy_tank()
Tank = Tank()
enemy_bullet = Enemy_bullet()
pygame.key.set_repeat(1,50)                                     
running = True

while running:
        if pygame.sprite.collide_rect(Tank, Enemy_tank):
                tank.x =+ 0
                
        Tank.update(dt)           
        bullet.update(dt)       

        screen.fill (background_color)                          
        Tank.draw(screen)       
        lvl_1.draw(screen)
        if bullet.fired == True:        
                bullet.draw(screen)
        enemy_tank.draw(screen)
        if tank_collide == True:
                tank.x =+ 0

        pygame.display.flip()                                   
        clock.tick(30)                                          

        for event in pygame.event.get():                        


                if event.type == pygame.QUIT:                           
                        running = False
                elif event.type == pygame.KEYDOWN:
                        if event.key == pygame.K_RIGHT:
                                Tank.x += 5
                        if event.key == pygame.K_LEFT:
                                Tank.x -= 5                             
                        if event.key == pygame.K_SPACE:
                                Tank.fire(bullet)       


```

---

### Post by Tony Flury on 2011-02-20
If you look at the error message - the error is moving - which is good - it means that you are fixing the errors - one at a time and the python interpreter is hitting the next one

The pygame documentation is here : 

[http://www.pygame.org/docs/ref/index.html](http://www.pygame.org/docs/ref/index.html)

For your error : 

The line that is wrong is here (as shown in the error : 

if pygame.sprite.collide_rect(Tank, Enemy_tank): 

Neither Tank or Enemy_tank are sprites - are they - they are of the right type - but you have not intialised the base sprite class so that might well be a problem.

Guessing from your code - that line maybe should be : 

if pygame.sprite.collide_rect(Tank.Tank, Enemy_tank.enemy_tank):

My suggestions : 
1) Use different names for your attributes (rather than just using different case) - the name should say something about what it is - a sprite (for instance).

2) You might want to re-read the tutorials on sub-classing - i am pretty sure that your code does not do what you think it does - it terms of your Tanks being sub-classed sprites, and this could be another source of confusion if you are still learning. I would even go so far as to suggest that you don't worry about sub-classing for now.

Good luck.

---

### Post by Tony Flury on 2011-02-21
You have marked this as solved - did you want to say how you fixed it ?

---

