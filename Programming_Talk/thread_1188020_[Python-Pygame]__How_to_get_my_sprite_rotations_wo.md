---
title: "[Python-Pygame]  How to get my sprite rotations working properly."
date: 2009-06-15
forum: Programming Talk
---

### Post by xZachtmx on 2009-06-15
ok so im using pygame jto create a simple 2d game and i have a sprite (little triangle for now)  that is always in the center and only movement it does is rotate.  
here is the code:
```

import pygame
from pygame.locals import*
from sys import exit
pygame.init()


windowSize = 1024,768

frameRate = 50

    # initializing the game window
gameWindow = pygame.display.set_mode((windowSize)) #, FULLSCREEN ) 
pygame.display.set_caption('STARBOUND') 
screen = pygame.display.get_surface() 

#loading textures
    # ship sprites
podTex = 'shipPlaceholder.png'
podSprite = pygame.image.load(podTex).convert_alpha()



clock = pygame.time.Clock()

class ship:
    def __init__(self):
        self.shipName = "pod"

        self.xPos = 0

        self.yPos = 0

        self.position = (self.xPos, self.yPos)

        self.width = 120

        self.height = 120

        self.hull = 100

        self.hullMax = 1000

        self.energy = 1000

        self.energyMax = 1000

        self.engineSpeed = 5
        
        self.turningSpeed = 5

        self.thrustingSpeed = 0

        self.thrustingSpeedMax = 10

        self.primaryWeapon = 1

        self.secondaryWeapon = 0

        self.secondaryWeaponMax = 0

        self.angle = 0

        self.isComp = True;

        self.shipTexture = podSprite;
        

    def turn(self, amount):
        self.angle += amount
        self.shipTexture = pygame.transform.rotate(self.shipTexture, self.angle)        
       
        
    def draw(self):
        screen.blit(self.shipTexture, (self.position))
        
playerShip = ship()
playerShip.xPos = windowSize[0] / 2 - 60
playerShip.yPos = windowSize[1] / 2 - 60
playerShip.position = (playerShip.xPos, playerShip.yPos);
playerShip.turningSpeed = 90
playerShip.isComp = False


while True:
    # Limit frame speed to 50 FPS
    #
     time_passed = clock.tick(frameRate)
    
     
     ship.turn(playerShip, playerShip.turningSpeed)
    
     ship.draw(playerShip) 
            
     pygame.display.flip()


```


now.. i want the sprite so slowly spim at a speed of 90 degrees per second (playerShip.turningSpeed)
so it spins... but instead of it being centered... this happens: 

[IMG]http://www.dreamincode.net/forums/index.php?act=Attach&type=post&id=12345[/IMG]

How can i get it so that it stays in the middle instead of spiraling out of the window?

---

### Post by gnuman on 2009-06-16
The problem here is that when an object rotates in Pygame, it may change size and position.

What you should do is copy the current center of the sprite into a temp variable and then do the rotation.  You then have to recalculate the rectangle and recenter the image.

If you've never looked at it before, Andy Harris's book THE EXPRESS LINE TO LEARNING GAME PROGRAMMING is a really good book entirely about Python and Pygame.  Unfortunately the title doesn't include either, so I've seen these shelved in the strangest places in bookstores.  The book is [[COLOR="Blue"]here[/COLOR]]("http://www.amazon.com/Game-Programming-Line-Express-Learning/dp/0470068221/ref=pd_bxgy_b_img_a") on Amazon.

---

