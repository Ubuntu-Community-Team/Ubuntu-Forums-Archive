---
title: "PyGame all sprites from one image"
date: 2010-07-05
forum: Programming Talk
---

### Post by slooksterpsv on 2010-07-05
Ok, I'm having trouble wrapping my brain around this one, with the tutorials on this one. In Python and PyGame, I want to take an image and only use a specific Rectangle of it for my sprite, but it's not working - it loads the entire image and not just the sprite area I want.

Where it gets tricky, I'm going through the Chimp tutorials where the create the load image function, so I'll post all my code, granted it's just basic right now - and some of it you may argue I don't need to do that it's just a waste, but I'm doing it for a reason so I just need help with getting a portion of an image as a sprite if I were to have all my sprites on one image.

[php]
#helpers.py
import os, sys
import pygame
from pygame.locals import *

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
[/php]

[PHP]
#main.py
import os, sys
import pygame
from pygame.locals import *
from helpers import *

class STKEngine:
    def __init__(self, width=640,height=480):
        """Initialize"""
        """Initialize PyGame"""
        pygame.init()
        """Set the window Size"""
        self.width = width
        self.height = height
        """Create the Screen"""
        self.screen = pygame.display.set_mode((self.width, self.height))
    
    def MainLoop(self):
        """This is the Main Loop of the Game"""
        self.LoadSprites()
        pygame.key.set_repeat(500, 30)

        self.background = pygame.Surface(self.screen.get_size())
        self.background = self.background.convert()
        self.background.fill((0,0,0))
        
        while 1:
            for event in pygame.event.get():
                if event.type == pygame.QUIT: 
                    sys.exit()
                elif event.type == KEYDOWN:
                    if ((event.key == K_RIGHT)
                        or (event.key == K_LEFT)
                        or (event.key == K_UP)
                        or (event.key == K_DOWN)):
                            self.testsprite.Move(event.key)
                            
            self.screen.blit(self.background, (0,0))
            
            self.DrawSprites()
            pygame.display.flip()

    def DrawSprites(self):
        self.testsprite_sprites.draw(self.screen)
    
    def LoadSprites(self):
        self.testsprite = STKSprite("myimage.bmp")
        #self.testsprite_sprites = self.testsprite.CreateGroup()
        self.testsprite_sprites = pygame.sprite.RenderPlain((self.testsprite))
        #self.testsprite_sprites.add(STKSprite("myimage.bmp", pygame.Rect(10, 20, 0, 0)))
                    
class STKSprite(pygame.sprite.Sprite):
   ###Sprite Loading Function###
    def __init__(self, filename, Rect=None):
        pygame.sprite.Sprite.__init__(self)
        self.image, self.rect = load_image(filename, -1)
        if Rect != None:
            self.rect = Rect
        self.SetMoveSpeed()
        
    def CreateGroup(self):
        return pygame.sprite.Group()
    
    def Move(self, key):
        xMove = 0
        yMove = 0
        
        if (key == K_RIGHT):
            xMove = self.x_dist
        elif (key == K_LEFT):
            xMove = -self.x_dist
        elif (key == K_DOWN):
            yMove = self.y_dist
        elif (key == K_UP):
            yMove = -self.y_dist
        self.rect.move_ip(xMove, yMove)
        print key
        
    def SetMoveSpeed(self, speedX=5, speedY=5):
        self.x_dist = speedX
        self.y_dist = speedY
        
    def CreateSpriteFromImage(self, image, rect):
        #image1 = pygame.image.load("data/myimage.bmp").convert()
        print "Attempting to create"
        
if __name__ == "__main__":
    Game1 = STKEngine()
    Game1.MainLoop()
[/PHP]

---

### Post by Asday on 2010-07-23
I've not yet had the pleasure of working with sprites, but I regularly use subsurfaces.

You might be able to use something like:

```
surf_spritesheet = pygame.image.load("lol.png").convert()
surf_spritesheet.set_colorkey((255,0,255))

rect_subsurf_area = pygame.Rect(0,0,64,64) #left top with height, I think
surf_sprite_benjy = surf_spritesheet.subsurface(rect_subsurf_area)
rect_subsurf_area.move(0,64)
surf_sprite_jessy = surf_spritesheet.subsurface(rect_subsurf_area)
```

This could be automated/made much prettier with a multidimensional array, and some "*64"s scattered liberally around.

(Did I help?)  :D[PHP][/PHP]

---

