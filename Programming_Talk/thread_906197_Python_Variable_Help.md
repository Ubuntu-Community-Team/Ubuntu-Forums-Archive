---
title: "Python Variable Help"
date: 2008-08-31
forum: Programming Talk
---

### Post by jimjag on 2008-08-31
I'm having trouble trying to get the "Police" Class to read a Variable out of the "Car" class what do i need to do to use the variable self.rect.x from the Car class in the Police class
```

import pygame, random
pygame.init()

screen = pygame.display.set_mode((480, 480))

#----------------------------------------------------------------------------------------------------#
class Car(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.image.load("CAR.png")
        self.image = self.image.convert()
        transColor = self.image.get_at((1, 1))
        self.image.set_colorkey(transColor)
        self.rect = self.image.get_rect()
        
        self.rect.x = 163
        self.rect.y = 338

    def checkKeys(self):

        keys = pygame.key.get_pressed()

        if keys[pygame.K_a]:
            if (self.rect.x - 7) <= x:
                print "left boundry"
            else:
                self.rect.x -= 7

        elif keys[pygame.K_d]:
            if (self.rect.x + 7) >= 429:
                print "right boundry"
            else:
                self.rect.x += 7

        elif keys[pygame.K_s]:
            if (self.rect.y + 4) >= 406:
                print "bottom boundry"
            else:
                self.rect.y += 4

        elif keys[pygame.K_w]:
            if (self.rect.y - 4) <= 2:
                print "top Boundary"
            else:
                self.rect.y -= 4
        x = self.rect.x       
        print self.rect.x, self.rect.y
        print x
        
    def update(self):
        self.checkKeys()
        pygame.display.update

    def Boundry(self):
        self.checkKeys()
    
#----------------------------------------------------------------------------------------------------#
class Police(pygame.sprite.Sprite, value_transferred):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.image.load("POLICE.png")
        self.image = self.image.convert()
        transColor = self.image.get_at((1, 1))
        self.image.set_colorkey(transColor)
        self.rect = self.image.get_rect()
        self.reset()
        
    def follow(self):
        if (self.rect.centerx) > (car.self.x + 36):
            self.dx = -4
            print "to the right of the car"
        elif (self.rect.centerx) < (car.self.x):
            self.dx = 4
            print "to the left of the car"
        else:
            self.dx = 0
            self.dy = 0
            print "inline", " ", x
        
    
    def update(self):
        self.follow()
        self.rect.centerx += self.dx
        self.rect.centery += self.dy
        if self.rect.bottom <  0:
            self.reset()
    
    def reset(self):
        self.rect.top = 480
        self.rect.centerx = random.randrange(19, 128)
        self.dy = random.randrange(-3, -2)
        self.dx = 0
        self.follow()


#----------------------------------------------------------------------------------------------------#
class Road(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.image.load("ROAD.png")
        self.image = self.image.convert()
        self.rect = self.image.get_rect()
        self.dy = 8
        self.reset()
        
    def update(self):
        self.rect.bottom += self.dy
        if self.rect.top >= 0:
            self.reset() 
    
    def reset(self):
        self.rect.bottom = screen.get_height()
        


        
        
#----------------------------------------------------------------------------------------------------#        
def main():
    screen = pygame.display.set_mode((480, 480))
    pygame.display.set_caption("Get Away Car Escape")
    value_transferred = Car()
    background = pygame.Surface(screen.get_size())
    background.fill((0, 0, 255))
    screen.blit(background, (0, 0))
    car = Car()
    road = Road()
    
    allSprites = pygame.sprite.Group(road, police1, car)
    clock = pygame.time.Clock()
    keepGoing = True
    
    while keepGoing:
        clock.tick(30)
        pygame.mouse.set_visible(False)
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                keepGoing = False
                
        
        allSprites.update()
        allSprites.draw(screen)
        
        pygame.display.flip()
    
    #return mouse cursor
    pygame.mouse.set_visible(True) 
if __name__ == "__main__":
    main()
            

```

any help would be massively appreciated. I'm still very much a beginner at this thing

thanks

---

### Post by unutbu on 2008-08-31
I'm not sure that the logic of my changes is what you want, but below is an example of how to have the police object know about a car object's self.rect.x:

First change 
```
class Police(pygame.sprite.Sprite, value_transferred):
```
to
```

class Police(pygame.sprite.Sprite):
```

In a class declaration, the things listed in parentheses are base classes. Here, Police is a class that inherits from the pygame.sprite.Sprite class. This is not the place to pass variables. 

You can pass variables to functions and methods however. Here a variable called car will be expected whenever you make a new Police instance:  Police(car) instead of Police().
```

    def __init__(self,car):
```

This line saves the car variable in self.car, so that the Police instance can summon information from the car object whenever it wants.
```

        self.car = car

```
Change
 ```
       if (self.rect.centerx) > (car.self.x + 36):
```
to```

        if (self.rect.centerx) > (self.car.rect.x + 36):
```

I'm guessing this is what you want, though I'm not sure. 

```

#!/usr/bin/env python
import pygame, random
pygame.init()

screen = pygame.display.set_mode((480, 480))

#----------------------------------------------------------------------------------------------------#
class Car(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)

        self.image = pygame.image.load("CAR.png")
        self.image = self.image.convert()
        transColor = self.image.get_at((1, 1))
        self.image.set_colorkey(transColor)
        self.rect = self.image.get_rect()
        
        self.rect.x = 163
        self.rect.y = 338

    def checkKeys(self):

        keys = pygame.key.get_pressed()

        if keys[pygame.K_a]:
            if (self.rect.x - 7) <= x:
                print "left boundry"
            else:
                self.rect.x -= 7

        elif keys[pygame.K_d]:
            if (self.rect.x + 7) >= 429:
                print "right boundry"
            else:
                self.rect.x += 7

        elif keys[pygame.K_s]:
            if (self.rect.y + 4) >= 406:
                print "bottom boundry"
            else:
                self.rect.y += 4

        elif keys[pygame.K_w]:
            if (self.rect.y - 4) <= 2:
                print "top Boundary"
            else:
                self.rect.y -= 4
        x = self.rect.x       
        print self.rect.x, self.rect.y
        print x
        
    def update(self):
        self.checkKeys()
        pygame.display.update

    def Boundry(self):
        self.checkKeys()
    
#----------------------------------------------------------------------------------------------------#
class Police(pygame.sprite.Sprite):
    def __init__(self,car):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.image.load("POLICE.png")
        self.image = self.image.convert()
        transColor = self.image.get_at((1, 1))
        self.image.set_colorkey(transColor)
        self.rect = self.image.get_rect()
        self.car = car
        self.reset()
        
    def follow(self):
        if (self.rect.centerx) > (self.car.rect.x + 36):
            self.dx = -4
            print "to the right of the car"
        elif (self.rect.centerx) < (self.car.rect.x):
            self.dx = 4
            print "to the left of the car"
        else:
            self.dx = 0
            self.dy = 0
            print "inline", " ", self.car.rect.x
        
    
    def update(self):
        self.follow()
        self.rect.centerx += self.dx
        self.rect.centery += self.dy
        if self.rect.bottom <  0:
            self.reset()
    
    def reset(self):
        self.rect.top = 480
        self.rect.centerx = random.randrange(19, 128)
        self.dy = random.randrange(-3, -2)
        self.dx = 0
        self.follow()


#----------------------------------------------------------------------------------------------------#
class Road(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.image.load("ROAD.png")
        self.image = self.image.convert()
        self.rect = self.image.get_rect()
        self.dy = 8
        self.reset()
        
    def update(self):
        self.rect.bottom += self.dy
        if self.rect.top >= 0:
            self.reset() 
    
    def reset(self):
        self.rect.bottom = screen.get_height()
        


        
        
#----------------------------------------------------------------------------------------------------#        
def main():
    screen = pygame.display.set_mode((480, 480))
    pygame.display.set_caption("Get Away Car Escape")
    value_transferred = Car()
    background = pygame.Surface(screen.get_size())
    background.fill((0, 0, 255))
    screen.blit(background, (0, 0))
    car = Car()
    road = Road()
    police1 = Police(car)       # I added this since police1 had not yet been defined.

    allSprites = pygame.sprite.Group(road, police1, car)
    clock = pygame.time.Clock()
    keepGoing = True
    
    while keepGoing:
        clock.tick(30)
        pygame.mouse.set_visible(False)
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                keepGoing = False
                
        
        allSprites.update()
        allSprites.draw(screen)
        
        pygame.display.flip()
    
    #return mouse cursor
    pygame.mouse.set_visible(True) 
if __name__ == "__main__":
    main()

```

---

### Post by pmasiar on 2008-08-31
> **jimjag said:**
> I'm having trouble trying to get the "Police" Class to read a Variable out of the "Car" class what do i need to do to use the variable self.rect.x from the Car class in the Police class

any help would be massively appreciated. I'm still very much a beginner at this thing

Don't try to learn programming and OOP at the same time. Learn Python without OOP first - use it as plain procedural language.

---

