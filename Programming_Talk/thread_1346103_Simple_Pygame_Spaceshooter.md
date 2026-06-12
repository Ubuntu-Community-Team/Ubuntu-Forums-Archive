---
title: "Simple Pygame Spaceshooter"
date: 2009-12-04
forum: Programming Talk
---

### Post by azurepancake on 2009-12-04
Hello!

I'm new to programming and have been playing with Python for a few months now. With an interest in game development, I thought I'd begin to learn some PyGame basics. So, I did the classic line-by-line Chimp tutorial and indeed learned a lot, but things are still a bit foggy.

I'm working on a simple Spaceshooter, Gradius style. You control the ship with the mouse while enemies come from the right side of the screen.

Here is the code:

```

#!/usr/bin/env python

import os, pygame
import random

from pygame.locals import *

from pygame.compat import geterror



if not pygame.font: print ('Warning, fonts disabled')

if not pygame.mixer: print ('Warning, sound disabled')



main_dir = os.path.split(os.path.abspath(__file__))[0]

data_dir = os.path.join(main_dir, 'data')



def load_image(name, colorkey=None):

    fullname = os.path.join(data_dir, name)

    try:

        image = pygame.image.load(fullname)

    except pygame.error:

        print ('Cannot load image:', fullname)

        raise SystemExit(str(geterror()))

    image = image.convert()

    if colorkey is not None:

        if colorkey is -1:

            colorkey = image.get_at((0,0))

        image.set_colorkey(colorkey, RLEACCEL)

    return image, image.get_rect()
    
def load_sound(name):

    class NoneSound:

        def play(self): pass

    if not pygame.mixer or not pygame.mixer.get_init():

        return NoneSound()

    fullname = os.path.join(data_dir, name)

    try:

        sound = pygame.mixer.Sound(fullname)

    except pygame.error:

        print ('Cannot load sound: %s' % fullname)

        raise SystemExit(str(geterror()))

    return sound
    
    
class Ship(pygame.sprite.Sprite):

    def __init__(self):

        pygame.sprite.Sprite.__init__(self)

        self.image, self.rect = load_image('ship.gif', -1)


    def update(self):

        pos = pygame.mouse.get_pos()
        self.rect.midtop = pos
        
class Alien(pygame.sprite.Sprite):

    def __init__(self):

        pygame.sprite.Sprite.__init__(self) 

        self.image, self.rect = load_image('aliens.png', -1)

        screen = pygame.display.get_surface()

        self.area = screen.get_rect()
        self.y = random.randrange(1, 600)

        self.rect.topleft = 800, self.y

        self.move = random.randrange(1, 5)



    def update(self):

        self._move()



    def _move(self):
        newpos = self.rect.move((-self.move, 0))

        self.rect = newpos
       
def main():    
#Initialize Everything

    pygame.init()

    screen = pygame.display.set_mode((800, 600))

    pygame.display.set_caption('Space Quest')

    pygame.mouse.set_visible(0)



#Create The Backgound

    background = pygame.Surface(screen.get_size())

    background = background.convert()

    background.fill((000, 000, 000))



#Display The Background

    screen.blit(background, (0, 0))

    pygame.display.flip()



#Prepare Game Objects

    clock = pygame.time.Clock()

    ship = Ship()
    alien = Alien()

    allsprites = pygame.sprite.RenderPlain((ship, alien))
    enemy = pygame.sprite.RenderPlain((alien))



#Main Loop

    going = True

    while going:

        clock.tick(60)



        #Handle Input Events

        for event in pygame.event.get():

            if event.type == QUIT:

                going = False

            elif event.type == KEYDOWN and event.key == K_ESCAPE:

                going = False



        allsprites.update()



        #Draw Everything

        screen.blit(background, (0, 0))

        allsprites.draw(screen)

        pygame.display.flip()



    pygame.quit()



#this calls the 'main' function when this script is executed

if __name__ == '__main__':

    main()

```

At the moment, you can control the ship and a single enemy comes from the right. There is no collision detection yet. As you can see, I stole a lot of code from the chimp-by-chimp tutorial. Now, what I am trying to do is have multiple instances of the Alien object coming from the right, not just one..

So basically, I want to be able to initialize the Alien object every 1-2 seconds or so, to keep a steady flux of enemies coming towards the player. I already have it set to generate at a random speed and random spot on the Y axis.

I have idea on how this would work, but I just don't know how to put it down. Can anyone give me a hint or two? 

I really apprecaite it. If you need anymore info, please just ask.

Thanks & Mett&#257;!

---

### Post by ib.lundgren on 2009-12-05
Another pygame tutorial seem to cover a similar problem, 

[http://inventwithpython.com/chapter19.html](http://inventwithpython.com/chapter19.html) (dodge things coming from top of screen)

You might want to start with:

- A list of enemies
- At a given or random interval, add an enemy to the list
- Display all enemies at their current position

---

### Post by azurepancake on 2009-12-05
Whoa, nice tutorial! I think I'm gonna start from Chapter 15, where it covers PyGame basics. I still need to cover the simple stuff some more.

Also, thanks for the advice, I hope after a little more practice, I'll be able to execute your advice.

---

### Post by azurepancake on 2009-12-08
Well, I've worked on this project and little more and took your advice. You can now control the ship with the keyboard and multiple enemies come out from the right hand-side of the screen.

But, now I want some interaction between the ship and the aliens. I'd like to implement laser beams, but I'm just not sure how to go about it yet. The questions I'm facing are:

Should I create the laser as its own object? When one hits the spacebar, how does one program the laser to appear, fly forwards and collide with an enemy? I'm guessing you'll need to add the laser object to a list, to be rendered on the fly, but I'm not too sure what in the actual code makes the laser shoot forward and reset back at the ship..

Here is the updated code:

**main.py**
```
#!/usr/bin/env python

from helpers import *
from aliens import *


class Ship(pygame.sprite.Sprite):

    def __init__(self):

        pygame.sprite.Sprite.__init__(self)

        self.image, self.rect = load_image('ship.gif', -1)
        self.x_dist = 5
        self.y_dist = 5
        self.firing = 0
        
    def update(self):
        key = pygame.key.get_pressed()
        if key[K_UP]:
            self.rect.centery += -3
        if key[K_DOWN]:
            self.rect.centery += 3
        if key[K_RIGHT]:
            self.rect.centerx += 3
        if key[K_LEFT]:
            self.rect.centerx += -3

        if self.rect.bottom > 600:
            self.rect.bottom = 600
        if self.rect.top < 0:
            self.rect.top = 0
        if self.rect.right > 800:
            self.rect.right = 800  
        if self.rect.left < 0:
            self.rect.left = 0
                                                                                                 
def main():    
# Initialize Everything

    pygame.init()

    screen = pygame.display.set_mode((800, 600))

    pygame.display.set_caption('Space Quest')

    pygame.mouse.set_visible(0)



# Create The Backgound

    background = pygame.Surface(screen.get_size())

    background = background.convert()

    background.fill((000, 000, 000))



# Display The Background

    screen.blit(background, (0, 0))

    pygame.display.flip()



# Prepare Game Objects

    clock = pygame.time.Clock()

    ship = Ship()
    alien1 = Alien1()
    alien2 = Alien2()
    alien3 = Alien3()   
    #alien4 = Alien4()
    #alien5 = Alien5()
    #alien6 = Alien6()
    
    # List Objects
    alienSprites = [alien1, alien2, alien3]

    # Render Objects     
    player = pygame.sprite.RenderPlain((ship))
    aliens = pygame.sprite.RenderPlain((alienSprites))
            

# Main Loop

    going = True
    pygame.key.set_repeat(1, 30)

    while going:

        clock.tick(60)



        # Input Events

        for event in pygame.event.get():

            if event.type == QUIT:

                going = False

            elif event.type == KEYDOWN and event.key == K_ESCAPE:

                going = False

        # Update
        player.update()
        aliens.update()



        screen.blit(background, (0, 0))


        # Draw        
        player.draw(screen)
        aliens.draw(screen)
        

        pygame.display.flip()



    pygame.quit()



if __name__ == '__main__':

    main()
```


**aliens.py**
```
#!/usr/bin/env python
# Load Enemy Objects

from helpers import *

class Alien1(pygame.sprite.Sprite):

    def __init__(self):

        pygame.sprite.Sprite.__init__(self) 

        self.image, self.rect = load_image('aliens.png', -1)

        screen = pygame.display.get_surface()

        self.area = screen.get_rect()
        self.y = random.randrange(1, 600)

        self.rect.topleft = 800, self.y

        self.move = random.randrange(1, 5)



    def update(self):

        self._move()


    def _move(self):
        newpos = self.rect.move((-self.move, 0))
        if self.rect.right == 0:
            self.y = random.randrange(100, 500)
            self.rect.topleft = 800, self.y
            self.move = random.randrange(1, 5)
            newpos = self.rect.move((-self.move, 0))

        self.rect = newpos
        
class Alien2(pygame.sprite.Sprite):

    def __init__(self):

        pygame.sprite.Sprite.__init__(self) 

        self.image, self.rect = load_image('aliens2.png', -1)

        screen = pygame.display.get_surface()

        self.area = screen.get_rect()
        self.y = random.randrange(1, 600)

        self.rect.topleft = 800, self.y

        self.move = random.randrange(1, 5)



    def update(self):

        self._move()



    def _move(self):
        newpos = self.rect.move((-self.move, 0))
        if self.rect.right == 0:
            self.y = random.randrange(100, 500)
            self.rect.topleft = 800, self.y
            self.move = random.randrange(1, 5)
            newpos = self.rect.move((-self.move, 0))

        self.rect = newpos
        
class Alien3(pygame.sprite.Sprite):

    def __init__(self):

        pygame.sprite.Sprite.__init__(self) 

        self.image, self.rect = load_image('aliens3.png', -1)

        screen = pygame.display.get_surface()

        self.area = screen.get_rect()
        self.y = random.randrange(1, 600)

        self.rect.topleft = 800, self.y

        self.move = random.randrange(1, 5)



    def update(self):

        self._move()



    def _move(self):
        newpos = self.rect.move((-self.move, 0))
        if self.rect.right == 0:
            self.y = random.randrange(100, 500)
            self.rect.topleft = 800, self.y
            self.move = random.randrange(1, 5)
            newpos = self.rect.move((-self.move, 0))

        self.rect = newpos
```


**helpers.py**
```
#!/usr/bin/env python

import os, sys, pygame, random
from pygame.locals import *
from pygame.compat import geterror

if not pygame.font: print ('Warning, fonts disabled')

if not pygame.mixer: print ('Warning, sound disabled')



main_dir = os.path.split(os.path.abspath(__file__))[0]

data_dir = os.path.join(main_dir, 'data')



def load_image(name, colorkey=None):

    fullname = os.path.join(data_dir, name)

    try:

        image = pygame.image.load(fullname)

    except pygame.error:

        print ('Cannot load image:', fullname)

        raise SystemExit(str(geterror()))

    image = image.convert()

    if colorkey is not None:

        if colorkey is -1:

            colorkey = image.get_at((0,0))

        image.set_colorkey(colorkey, RLEACCEL)

    return image, image.get_rect()
    
def load_sound(name):

    class NoneSound:

        def play(self): pass

    if not pygame.mixer or not pygame.mixer.get_init():

        return NoneSound()

    fullname = os.path.join(data_dir, name)

    try:

        sound = pygame.mixer.Sound(fullname)

    except pygame.error:

        print ('Cannot load sound: %s' % fullname)

        raise SystemExit(str(geterror()))

    return sound
```

I've gone through several tutorials and have looked at other peoples code for similar projects, but I'm still just not getting something. I was hoping someone here could give me a little hint or advice to get me in right path for shooting some lazer beamz!

Thank you!

---

### Post by OgreProgrammer on 2009-12-09
Hey azurepancake, can I show you a trick?

I rewrote part of your function. This simplifies things. 

If you also know the size of the rectangle(or sprite?), and its assigned to a halfSpriteS var, you can slim it down even more. 



```

def update(self):
        key = pygame.key.get_pressed()
        if key[K_UP]:
            self.rect.centery += -3
        if key[K_DOWN]:
            self.rect.centery += 3
        if key[K_RIGHT]:
            self.rect.centerx += 3
        if key[K_LEFT]:
            self.rect.centerx += -3

        self.rect.bottom = min(self.rect.bottom, 600)
        self.rect.top = max(self.rect.top, 0)
        self.rect.right = min(self.rect.right, 800)
        self.rect.left = max(self.rect.left, 0)

```You can even combine them sometimes.

```

#generic code
something = max(min(something, bigNum), smallNum)
# always returns a value inside valid limits

```bigNum would be the right side of the screen or the bottom. SmallNum is the other two sides. You'll want to subtract half the size of the sprite from those numbers if you dont want to draw outside the screen.

So that could be 2 lines instead of 8 if you can rework things.

You can do some interesting things to the key pressed stuff too, in a similar way. I'll let you figure that out. Or you can ask me again if I am being unclear.

Good work so far. Keep going!

---

### Post by OgreProgrammer on 2009-12-09
> **azurepancake said:**
> I was hoping someone here could give me a little hint or advice to get me in right path for shooting some lazer beamz!

Thank you!

You need to know about targeting or collisions between beams and target?

---

### Post by ib.lundgren on 2009-12-09
The lazerbeam is nothing more complicated than a spaceship with another sprite, or just a painted rectangle with another size and a location.

For example if you have the battlefield:


```
     1  2  3  4  5  6  7  8  9  (Y)
     __ __ __ __ __ __ __ __ __
1 |
2 | 
3 |  (ship) -    -       (alien)
4 |
5 |
(X)
```

Then you have 3 objects, with 3 sizes and 3 positions.

The ship with height = 1 and width = 2 at position (1,3)
A lazerbeam with height and width = 1 at position (3,3)
Another lazerbeam with height and width = 1 at position (5,3)
The alien with height=1, width=2, at position (8, 3)

You need to find out when the **right** edge of the lazerbeam is at the same location as the **left** edge of the alien.

If in this example the alien ship stays in position the second beam need to travel from position (5,3) to (8,3). 

Add an appropriate collision detection function near your update functions. Also, try and think about what should happen when a collision is detected? How do you remove the alien and the lazerbeam?

---

### Post by azurepancake on 2009-12-09
Thank you all very much! I finally gots some lazer-beemz! I also was able to implement collision detection and setup a scrolling background.

I found my biggest obstacle was that I didn't even think about adding sprite objects to a list, to be rendered on the fly (at the press of a key).

Here is the updated code, if your interested:

```
#!/usr/bin/env python

from helpers import *

class Space(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        self.image, self.rect = load_image("space.png", -1)
        self.dx = -5
        self.reset()
        
    def update(self):
        self.rect.left += self.dx
        if self.rect.right <= 800:
            self.reset() 
    
    def reset(self):
        self.rect.right = 1600

class Player(pygame.sprite.Sprite):

    def __init__(self):

        pygame.sprite.Sprite.__init__(self)

        self.image, self.rect = load_image('ship.gif', -1)
        self.x_dist = 5
        self.y_dist = 5
        self.lasertimer = 0
        self.lasermax = 5
        self.rect.centery = 400
        self.rect.centerx = 50
        
    def update(self):
        key = pygame.key.get_pressed()
        
        # Movement
        if key[K_UP]:
            self.rect.centery += -3
        if key[K_DOWN]:
            self.rect.centery += 3
        if key[K_RIGHT]:
            self.rect.centerx += 3
        if key[K_LEFT]:
            self.rect.centerx += -3
        
        # Lasers
        if key[K_SPACE]:
            self.lasertimer = self.lasertimer + 1
            if self.lasertimer == self.lasermax:
                laserSprites.add(Laser(self.rect.midtop))
                self.lasertimer = 0
       
        # Restrictions
        self.rect.bottom = min(self.rect.bottom, 600)
        self.rect.top = max(self.rect.top, 0)
        self.rect.right = min(self.rect.right, 800)
        self.rect.left = max(self.rect.left, 0)
                                                     
class Laser(pygame.sprite.Sprite):
    def __init__(self, pos):
        pygame.sprite.Sprite.__init__(self)
        self.image, self.rect = load_image("laser.png", -1)
        self.rect.center = pos
    
    def update(self):
        if self.rect.right > 800:
            self.kill()
        else:
            self.rect.move_ip(15, 0)
            

class Enemy(pygame.sprite.Sprite):
    def __init__(self, centerx):
        pygame.sprite.Sprite.__init__(self)
        self.image, self.rect = load_image("alien.png", -1)
        self.rect = self.image.get_rect()
        self.dy = 8
        self.reset()
        
    def update(self):
        self.rect.centerx += self.dx
        self.rect.centery += self.dy
        if self.rect.top > 600:
            self.reset()
        
        # Laser Collisions    
        if pygame.sprite.groupcollide(enemySprites, laserSprites, 1, 1):
           explosionSprites.add(EnemyExplosion(self.rect.center))
           
        # Ship Collisions
        if pygame.sprite.groupcollide(enemySprites, playerSprite, 1, 1):
           explosionSprites.add(EnemyExplosion(self.rect.center))
           explosionSprites.add(PlayerExplosion(self.rect.center))
           
    def reset(self):
        self.rect.bottom = 0
        self.rect.centerx = random.randrange(0, 600)
        self.dy = random.randrange(5, 10)
        self.dx = random.randrange(-2, 2)
                                                           
class EnemyExplosion(pygame.sprite.Sprite):
    def __init__(self, pos):
        pygame.sprite.Sprite.__init__(self)
        self.image, self.rect = load_image("enemyexplosion.png", -1)
        self.rect.center = pos        
        self.counter = 0
        self.maxcount = 10
        
    def update(self):
        self.counter = self.counter + 1
        if self.counter == self.maxcount:
            self.kill()
            
class PlayerExplosion(pygame.sprite.Sprite):
    def __init__(self, pos):
        pygame.sprite.Sprite.__init__(self)
        self.image, self.rect = load_image("enemyexplosion.png", -1)
        self.rect.center = pos        
        self.counter = 0
        self.maxcount = 10
        
    def update(self):
        self.counter = self.counter + 1
        if self.counter == self.maxcount:
            self.kill()
            exit()
                                                                                                              
def main():    
# Initialize Everything

    pygame.init()

    screen = pygame.display.set_mode((800, 600))

    pygame.display.set_caption('Space Quest')

    pygame.mouse.set_visible(0)



# Create The Backgound

    background = pygame.Surface(screen.get_size())

    background = background.convert()

    background.fill((000, 000, 000))



# Display The Background

    screen.blit(background, (0, 0))

    pygame.display.flip()
        
# Start Music   
    music = pygame.mixer.music.load ("data/spacequest.mp3")
    pygame.mixer.music.play(-1)



# Initialize Game Objects
    global clock

    clock = pygame.time.Clock()
    space = Space()
    global player

    player = Player()


# Render Objects
    # Space
    space = pygame.sprite.RenderPlain((space))
    
    # Player
    global playerSprite   
    playerSprite = pygame.sprite.RenderPlain((player))
    
    # Enemy
    global enemySprites
    enemySprites = pygame.sprite.RenderPlain(())
    enemySprites.add(Enemy(200))
    enemySprites.add(Enemy(300))
    enemySprites.add(Enemy(400))    

    # Projectiles    
    global laserSprites
    laserSprites = pygame.sprite.RenderPlain(())   
    
    # Collisions   
    global enemyExplosion
    enemyExplosion = pygame.sprite.RenderPlain(())
    global playerExplosion
    playerExplosion = pygame.sprite.RenderPlain(())
    global explosionSprites
    explosionSprites = pygame.sprite.RenderPlain(())
            

# Main Loop

    going = True

    while going:

        clock.tick(60)



        # Input Events

        for event in pygame.event.get():

            if event.type == QUIT:

                going = False

            elif event.type == KEYDOWN and event.key == K_ESCAPE:

                going = False

        # Update
        space.update()
        player.update()
        enemySprites.update()
        laserSprites.update()
        enemyExplosion.update()
        playerExplosion.update()
        explosionSprites.update()



        screen.blit(background, (0, 0))


        # Draw
        space.draw(screen)   
        playerSprite.draw(screen)
        enemySprites.draw(screen)
        laserSprites.draw(screen)
        enemyExplosion.draw(screen)
        playerExplosion.draw(screen)
        explosionSprites.draw(screen)
        

        pygame.display.flip()



    pygame.quit()



if __name__ == '__main__':

    main()

```

Again, thanks for your wonderful explanations. It helped me get the juices flowing a little bit! I also spent a lot of time reading other peoples code, with more experience than I. I found lots of ways to rearrange, rewrite and clean up my own program through doing this.

And thanks for the rework of the ship object's update function. Anything to slim code down is great. I find the larger it is, the more confused I get!

---

