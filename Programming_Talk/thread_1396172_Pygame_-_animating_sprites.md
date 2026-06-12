---
title: "Pygame - animating sprites"
date: 2010-02-01
forum: Programming Talk
---

### Post by DanielJackins on 2010-02-01
Hello, I'm trying to implement some sort of top-down-walk around-hitting stuff game, and I'm unsure about how to animate my sprite. I couldn't really find anything online. (And I don't mean the sprite class pygame comes with, I mean I made 3 .bmp files which would show the character walking down, instead of just gliding everywhere)

```
import pygame, os, sys
from pygame.locals import *

window_width, window_height = 800, 600

def load_image(name, colorkey=None):
    fullname = os.path.join('data', name)
    try:
        image = pygame.image.load(fullname)
    except pygame.error, message:
        print 'Cannot load image:', name
        raise SystemExit, message
    image = image.convert()
    if colorkey is not None:
        if colorkey is -1:
            colorkey = image.get_at((0,0))
        image.set_colorkey(colorkey, RLEACCEL)
    return image, image.get_rect()

def attack(char, monster):
        monster.hp -= char.strength

class Character(pygame.sprite.Sprite):
    def __init__(self):
        pygame.sprite.Sprite.__init__(self)
        #self.image = pygame.Surface([15,15])
        #self.image.fill([255,255,255])
        #self.rect = self.image.get_rect()
        self.image, self.rect = load_image('sprite3.bmp', -1)
        self.position = [50,50]
        self.rect.topleft = self.position
        
        self.strength = 1
        self.magic = 1
        self.health = 5
        self.hp = self.health
        self.mp = self.magic*5        
        
    def update(self, key, monster):
        old_pos = self.rect.topleft
        if key[K_LEFT]:
            self.rect.left -= 1
        if key[K_RIGHT]:
            self.rect.left += 1
        if key[K_UP]:
            self.rect.top -= 1
        if key[K_DOWN]:
            self.rect.top += 1
        if pygame.sprite.collide_rect(self, monster):
            self.rect.topleft = old_pos
            if key[K_SPACE]:
                attack(self, monster)
            
class Monster(pygame.sprite.Sprite):
    def __init__(self, strength, magic, health):
        pygame.sprite.Sprite.__init__(self)
        self.image = pygame.Surface([15,15])
        self.image.fill([200,200,200])
        self.rect = self.image.get_rect()
        self.position = [100,100]
        self.rect.topleft = self.position
        
        self.strength = strength
        self.magic = magic
        self.health = health
        self.hp = self.health
        self.mp = self.magic
        

def main():

    pygame.init()    
    
    #Initializes the game window
    screen = pygame.display.set_mode((window_width,window_height))
    pygame.display.set_caption("RPG")
    
    char = Character()
    slime = Monster(1,1,3)
    monsters = []
    monsters.append(slime)
    
    #Main loop
    while 1:
        screen.fill([0,0,0])
        for event in pygame.event.get():
            if event.type == QUIT:
                return
        key_pressed = pygame.key.get_pressed()
        for monster in monsters:         
            char.update(key_pressed, monster)                
        screen.blit(char.image, char.rect)
        screen.blit(monster.image, monster.rect)
        pygame.display.update()
main()
```

Any suggestions/help? 

Thanks!

---

### Post by JDShu on 2010-02-02
I followed this tutorial which teaches animating, but in Allegro for C. However, it should be applicable to pygame, since many of the functions are similar. The important thing is the logic, which it teaches :)

[http://www.loomsoft.net/resources/alltut/alltut_index.htm](http://www.loomsoft.net/resources/alltut/alltut_index.htm)

---

