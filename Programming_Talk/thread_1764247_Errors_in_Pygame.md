---
title: "Errors in Pygame"
date: 2011-05-21
forum: Programming Talk
---

### Post by colts18 on 2011-05-21
Hi,

I have been programming a game in pygame and python.  I recently added collision detection but now I get an error trying to draw the tank to the screen.  It was working fine until I added the collision detection.

Here is the error:

Traceback (most recent call last):
  File "/home/bolt/Python/tank_game/game.py", line 119, in <module>
    Tank.update(dt)
TypeError: unbound method update() must be called with Tank instance as first argument (got int instance instead)

Here is the code:

```
import pygame
import math
                                          
class Tank(pygame.sprite.Sprite):

        def __init__(self, init_pos, is_npc=True):

                pygame.sprite.Sprite.__init__(self)
                self.Tank = pygame.image.load("tank.png")       
                self.x = -200
                self.y = 20
                self.firecountdown=0

                self.center = init_pos
                self.rect = self.Tank.get_rect()

                self.velocity = [0, 0]

                self.is_npc = bool(is_npc)

        def _can_move_to(self, new_rect):
                for sprite in self.groups()[0]:
                        if sprite is not self:
                                return not sprite.rect.colliderect(new_rect)

        def draw(self, surface):
                surface.blit(self.Tank, (self.x, self.y))                                           
        def update(self, dt, t_passed, keys):
                if not self.is_npc:
                        if keys[pygame.K_RIGHT]:
                                self.velocity[0] = 250
                        elif keys[pygame.K_LEFT]:
                                self.velocity[0] = -250
                        else:
                                self.velocity[0] = 0

                velocity = [v * t_passed for v in self.velocity]

                if self._can_move_to(self.rect.move(*velocity)):
                        self.rect.move_ip(*velocity)
        
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
                pygame.sprite.Sprite.__init__(self)
                self.x = 200
                self.y = -40
                self.enemy_tank = pygame.image.load("enemy_tank.png")
                self.rect = self.enemy_tank.get_rect()
        def draw(self, surface):
                surface.blit(self.enemy_tank, (self.x, self.y))
        def update(self, dt):
                pass
        
class Enemy_bullet(pygame.sprite.Sprite):
        pass
                
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
enemy_bullet = Enemy_bullet()
pygame.key.set_repeat(1,50)                                     
running = True
speed = 100

t_accumalator = 0.0
t_step = 0.01

tanks = pygame.sprite.Group()
tanks.add (Tank((100, 150), False))
tanks.add (Tank((300, 150)))


while running:

        t_accumalator += clock.tick() / 1000.0          

        Tank.update(dt)
        bullet.update(dt)

        screen.fill (background_color)
        Tank.draw(screen)
        lvl_1.draw(screen)
        if bullet.fired == True:        
                bullet.draw(screen)
        enemy_tank.draw(screen)
        pygame.display.flip()                                   
        clock.tick(30)

        pygame.event.pump()
        
        for event in pygame.event.get():

                if event.type == pygame.QUIT:                           
                        running = False
                        exit()
                elif event.type == pygame.KEYDOWN:
                        if event.key == pygame.K_RIGHT:
                                Tank.x += 5
                        if event.key == pygame.K_LEFT:
                                Tank.x -= 5                             
                        if event.key == pygame.K_SPACE:
                                Tank.fire(bullet)

while t_accumalator >= t_step:
        for tank in tanks:
                tank.update(t_step, keys)

        t_accumalator -= t_step
        pygame.display.flip()


```

Does anyone know what is wrong?

---

### Post by simeon87 on 2011-05-21
You are calling Tank.update which means that you're calling update of the class Tank. That's not what you want because update is a method of instances of that class: it expects self as first argument. So you should be calling something like ```
tank.update(dt)
``` where tank is a Tank object.

---

### Post by cgroza on 2011-05-21
```
        
        Tank.update(dt)
        bullet.update(dt)
```You are calling the update method of the Tank class as a class method, not an instance method.

To make it a class method (static method in other languages ) you need to put a 
    @staticmethod
before your function declaration and remove self from the arguments.
Or, call it on an instance of the Tank, not the class definition itself.

---

### Post by colts18 on 2011-05-21
I made the changes to the code and it told me 4 arguments are needed so I put in what I think are the arguments needed but I got this error:

Traceback (most recent call last):
  File "/home/bolt/Python/tank_game/game.py", line 120, in <module>
    Tank.update(Tank, dt, t_passed, keys)
NameError: name 't_passed' is not defined


Here is the code:

```
import pygame
import math
                                          
class Tank(pygame.sprite.Sprite):

        def __init__(self, init_pos, is_npc=True):

                pygame.sprite.Sprite.__init__(self)
                self.Tank = pygame.image.load("tank.png")       
                self.x = -200
                self.y = 20
                self.firecountdown=0

                self.center = init_pos
                self.rect = self.Tank.get_rect()

                self.velocity = [0, 0]

                self.is_npc = bool(is_npc)

        def _can_move_to(self, new_rect):
                for sprite in self.groups()[0]:
                        if sprite is not self:
                                return not sprite.rect.colliderect(new_rect)
        @staticmethod
        def draw(self, surface):
                surface.blit(Tank, (self.x, self.y))
        @staticmethod
        def update(self, dt, t_passed, keys):
                if not self.is_npc:
                        if keys[pygame.K_RIGHT]:
                                self.velocity[0] = 250
                        elif keys[pygame.K_LEFT]:
                                self.velocity[0] = -250
                        else:
                                self.velocity[0] = 0

                velocity = [v * t_passed for v in self.velocity]

                if self._can_move_to(self.rect.move(*velocity)):
                        self.rect.move_ip(*velocity)
        
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
                pygame.sprite.Sprite.__init__(self)
                self.x = 200
                self.y = -40
                self.enemy_tank = pygame.image.load("enemy_tank.png")
                self.rect = self.enemy_tank.get_rect()
        def draw(self, surface):
                surface.blit(self.enemy_tank, (self.x, self.y))
        def update(self, dt):
                pass
        
class Enemy_bullet(pygame.sprite.Sprite):
        pass
                
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
enemy_bullet = Enemy_bullet()
pygame.key.set_repeat(1,50)                                     
running = True
speed = 100

t_accumalator = 0.0
t_step = 0.01

tanks = pygame.sprite.Group()
tanks.add (Tank((100, 150), False))
tanks.add (Tank((300, 150)))


while running:

        t_accumalator += clock.tick() / 1000.0          

        Tank.update(Tank, dt, t_passed, keys)
        bullet.update(dt)

        screen.fill (background_color)
        Tank.draw(screen)
        lvl_1.draw(screen)
        if bullet.fired == True:        
                bullet.draw(screen)
        enemy_tank.draw(screen)
        pygame.display.flip()                                   
        clock.tick(30)

        pygame.event.pump()
        
        for event in pygame.event.get():

                if event.type == pygame.QUIT:                           
                        running = False
                        exit()
                elif event.type == pygame.KEYDOWN:
                        if event.key == pygame.K_RIGHT:
                                Tank.x += 5
                        if event.key == pygame.K_LEFT:
                                Tank.x -= 5                             
                        if event.key == pygame.K_SPACE:
                                Tank.fire(bullet)

while t_accumalator >= t_step:
        for tank in tanks:
                tank.update(t_step, keys)

        t_accumalator -= t_step
        pygame.display.flip()


```

---

### Post by cgroza on 2011-05-21
Are you sure you need a static method.
I am guessing you have to call that on an instance of Tank. Also, why are you passing the Tank class as an argument?

And the error is clear, there is no t_passed variable in that scope.

---

### Post by simeon87 on 2011-05-21
I don't think you need staticmethods because the Tank is a subclass of a class provided by PyGame. I think you want something like this. You already have a group of tanks:

```
tanks = pygame.sprite.Group()
tanks.add (Tank((100, 150), False))
tanks.add (Tank((300, 150)))
```

I think you want to apply collision detection to them, something like this:

```
for t in tanks:
    t.update(dt, t_passed, keys)
```

So all you need to do is provide the correct values of t_passed and keys. Those values are currently not defined in your main loop.

---

### Post by colts18 on 2011-05-21
I made a lot of changes and I got a new error and I don't really understand what it means:

Traceback (most recent call last):
  File "/home/bolt/Python/tank_game/game.py", line 128, in <module>
    Tank.draw(screen)
TypeError: unbound method draw() must be called with Tank instance as first argument (got Surface instance instead)

Here is the new code:

```
import pygame
import math
                                          
class Tank(pygame.sprite.Sprite):

        def __init__(self, init_pos, is_npc=True):

                pygame.sprite.Sprite.__init__(self)
                self.Tank = pygame.image.load("tank.png")       
                self.x = -200
                self.y = 20
                self.firecountdown=0

                self.center = init_pos
                self.rect = self.Tank.get_rect()

                self.velocity = [0, 0]
                
                self.is_npc = bool(is_npc)

        def _can_move_to(self, new_rect):
                for sprite in self.groups()[0]:
                        if sprite is not self:
                                return not sprite.rect.colliderect(new_rect)
        
        def draw(self, surface):
                surface.blit(Tank, (self.x, self.y))
        
        def update(self, dt,):
                keys = pygame.key.get_pressed()
                
                if not self.is_npc:
                        if keys[pygame.K_RIGHT]:
                                self.velocity[0] = 250
                        elif keys[pygame.K_LEFT]:
                                self.velocity[0] = -250
                        else:
                                self.velocity[0] = 0

                velocity = [v * t_passed for v in self.velocity]

                if self._can_move_to(self.rect.move(*velocity)):
                        self.rect.move_ip(*velocity)
        
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
                pygame.sprite.Sprite.__init__(self)
                self.x = 200
                self.y = -40
                self.enemy_tank = pygame.image.load("enemy_tank.png")
                self.rect = self.enemy_tank.get_rect()
        def draw(self, surface):
                surface.blit(self.enemy_tank, (self.x, self.y))
        def update(self, dt):
                pass
        
class Enemy_bullet(pygame.sprite.Sprite):
        pass
                
pygame.init()                                                           
background_color = (0,0,0)                                              
(width, height) = (640, 480)                                    
screen = pygame.display.set_mode((width, height))                       
pygame.display.set_caption('Game Window')                       
clock = pygame.time.Clock()
t_passed = clock.tick(30)
lvl_1 = Lvl_1()
bullet = Bullet()
enemy_tank = Enemy_tank()
enemy_bullet = Enemy_bullet()
pygame.key.set_repeat(1,50)                                     
running = True
speed = 100

t_accumalator = 0.0
t_step = 0.01

tanks = pygame.sprite.Group()
tanks.add (Tank((100, 150), False))
tanks.add (Tank((300, 150)))


while running:

        t_accumalator += clock.tick() / 1000.0          

        for t in tanks:
                t.update(t_passed)

        bullet.update(t_passed)

        screen.fill (background_color)
        Tank.draw(screen)
        lvl_1.draw(screen)
        if bullet.fired == True:        
                bullet.draw(screen)
        enemy_tank.draw(screen)
        pygame.display.flip()                                   
        clock.tick(30)

        pygame.event.pump()
        
        for event in pygame.event.get():

                if event.type == pygame.QUIT:                           
                        running = False
                        exit()
                elif event.type == pygame.KEYDOWN:
                        if event.key == pygame.K_RIGHT:
                                Tank.x += 5
                        if event.key == pygame.K_LEFT:
                                Tank.x -= 5                             
                        if event.key == pygame.K_SPACE:
                                Tank.fire(bullet)

while t_accumalator >= t_step:
        for tank in tanks:
                tank.update(t_step, keys)

        t_accumalator -= t_step
        pygame.display.flip()


```

---

### Post by cgroza on 2011-05-21
You are doing the same error as above. Call it on an instance, not the class itself.

---

### Post by colts18 on 2011-06-21
I have 1 final question, I got everything to work except it says this:

Traceback (most recent call last):
  File "/home/bolt/Python/tank_game/game.py", line 118, in <module>
    tanks.add (Tank(((tank.center)), False))
AttributeError: type object 'tank' has no attribute 'center'

```
import pygame
import math
                                          
class tank(pygame.sprite.Sprite):

        def __init__(self, init_pos, is_npc=True):

                pygame.sprite.Sprite.__init__(self)
                self.Tank = pygame.image.load("tank.png")       
                self.x = -200
                self.y = 20
                self.firecountdown=0

                self.center = init_pos
                self.rect = self.Tank.get_rect()

                self.velocity = [0, 0]
                
                self.is_npc = bool(is_npc)

        def _can_move_to(self, new_rect):
                for sprite in self.groups()[0]:
                        if sprite is not self:
                                return not sprite.rect.colliderect(new_rect)
        
        def draw(self, surface):
                surface.blit(self.Tank, (self.x, self.y))
        
        def update(self, t_passed,):
                keys = pygame.key.get_pressed()
                
                if not self.is_npc:
                        if keys[pygame.K_RIGHT]:
                                self.velocity[0] = 250
                        elif keys[pygame.K_LEFT]:
                                self.velocity[0] = -250
                        else:
                                self.velocity[0] = 0

                self.update(velocity[0])

                velocity = [v * t_passed for v in self.velocity]

                if self._can_move_to(self.rect.move(*velocity)):
                        self.rect.move_ip(*velocity)
        
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
                pygame.sprite.Sprite.__init__(self)
                self.x = 200
                self.y = -40
                self.enemy_tank = pygame.image.load("enemy_tank.png")
                self.rect = self.enemy_tank.get_rect()
        def draw(self, surface):
                surface.blit(self.enemy_tank, (self.x, self.y))
        def update(self, dt):
                pass
        
class Enemy_bullet(pygame.sprite.Sprite):
        pass
                
pygame.init()                                                           
background_color = (0,0,0)                                              
(width, height) = (640, 480)                                    
screen = pygame.display.set_mode((width, height))                       
pygame.display.set_caption('Game Window')                       
clock = pygame.time.Clock()
t_passed = clock.tick(30)
Tank = tank(pygame.sprite.Sprite)
lvl_1 = Lvl_1()
bullet = Bullet()
enemy_tank = Enemy_tank()
enemy_bullet = Enemy_bullet()
pygame.key.set_repeat(1,50)                                     
running = True
speed = 100
t_accumalator = 0.0
t_step = 0.01

tanks = pygame.sprite.Group()
tanks.add (Tank(((tank.center)), False))


while running:

        t_accumalator += clock.tick() / 1000.0          

        for t in tanks:
                t.update(t_passed)

        bullet.update(t_passed)

        screen.fill (background_color)
        Tank.draw(screen)
        lvl_1.draw(screen)
        if bullet.fired == True:        
                bullet.draw(screen)
        enemy_tank.draw(screen)
        pygame.display.flip()                                   
        clock.tick(30)

        pygame.event.pump()
        
        for event in pygame.event.get():

                if event.type == pygame.QUIT:                           
                        running = False
                        exit()
                elif event.type == pygame.KEYDOWN:
                        if event.key == pygame.K_RIGHT:
                                Tank.x += 5
                                Tank.velocity[0] = 250
                        if event.key == pygame.K_LEFT:
                                Tank.x -= 5
                                Tank.velocity[0] = -250
                        if event.key == pygame.K_SPACE:
                                Tank.fire(bullet)
                        

while t_accumalator >= t_step:
        for tank in tanks:
                tank.update(t_step, keys)

        t_accumalator -= t_step
        pygame.display.flip()


```

I understand I am getting very needy but I have wasted a lot of time on this and I really need to finish it soon, I will not bother you guys after this is fixed.:D

---

### Post by cgroza on 2011-06-21
Well, the error says it all, there is no member called "center" in your tank class.
2 possibilities:

1. You define it in the Tank class.
2. You stop using it.

I suggest you take a look at python classes before continuing.

---

### Post by colts18 on 2011-06-24
I looked over a few tutorials but I couldn't find any good ones over pygame groups.  Should I create a function in the tank class to find the position of the tank and put that in where I currently have tank.center?  Or is that not a good way to do that?

---

### Post by cgroza on 2011-06-24
> **colts18 said:**
> I looked over a few tutorials but I couldn't find any good ones over pygame groups.  Should I create a function in the tank class to find the position of the tank and put that in where I currently have tank.center?  Or is that not a good way to do that?
Yes, the Tank does not have a center attribute, so you need to create one and manage it by yourself.

---

### Post by colts18 on 2011-06-24
Ok I will start working on that thanks for your help

---

