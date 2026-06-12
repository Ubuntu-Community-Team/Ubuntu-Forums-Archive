---
title: "Python Indention Error"
date: 2012-02-05
forum: Programming Talk
---

### Post by Treyonator56 on 2012-02-05
Error: (Colored Text)
Not sure if its the only mistake either...=S

trey@trey-pc:~$ ~/Desktop/game.py
  File "/home/trey/Desktop/game.py", line 83
    if self.rect.left < self.area.left or \
     ^
IndentationError: expected an indented block


```
#! /usr/bin/python
import os, sys
import pygame
from pygame.locals import *
if not pygame.font: print 'Warning, fonts disabled'
if not pygame.mixer: print  'Warning, sound disabled'

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

def load_sound(name):
    class NoneSound:
        def play(self): pass
    if not pygame.mixer:
        return NoneSound()
    fullname = os.path.join('data', name)
    try:
        sound = pygame.mixer.Sound(fullname)
    except pygame.error, message:
        print 'Cannot load sound:', wav
        raise SystemExit, message
    return sound

class Fist(pygame.sprite.Sprite):
    """moves a clenched fist on the screen, following the mouse"""
    def __init__(self):
        pygame.sprite.Sprite.__init__(self) #call Sprite initializer
        self.image, self.rect = load_image('fist.bmp', -1)
        self.punching = 0

    def update(self):
        "move the fist based on the mouse position"
        pos = pygame.mouse.get_pos()
        self.rect.midtop = pos
        if self.punching:
            self.rect.move_ip(5, 10)

    def punch(self, target):
        "returns true if the fist collides with the target"
        if not self.punching:
            self.punching = 1
            hitbox = self.rect.inflate(-5, -5)
            return hitbox.colliderect(target.rect)

    def unpunch(self):
        "called to pull the fist back"
        self.punching = 0

class Chimp(pygame.sprite.Sprite):
    """moves a monkey critter across the screen. it can spin the
       monkey when it is punched."""
    def __init__(self):
        pygame.sprite.Sprite.__init__(self) #call Sprite intializer
        self.image, self.rect = load_image('chimp.bmp', -1)
        screen = pygame.display.get_surface()
        self.area = screen.get_rect()
        self.rect.topleft = 10, 10
        self.move = 9
        self.dizzy = 0

    def update(self):
        "walk or spin, depending on the monkeys state"
        if self.dizzy:
            self._spin()
        else:
            self._walk()

    def _walk(self):
        "move the monkey across the screen, and turn at the ends"
        newpos = self.rect.move((self.move, 0))
        if not self.area.contains(newpos):
  [COLOR=Red]  if self.rect.left < self.area.left or \[/COLOR]
        self.rect.right > self.area.right:
        self.move = -self.move
            newpos = self.rect.move((self.move, 0))
        self.image = pygame.transform.flip(self.image, 1, 0)
        self.rect = newpos

    def _spin(self):
        "spin the monkey image"
        center = self.rect.center
        self.dizzy += 12
        if self.dizzy >= 360:
            self.dizzy = 0
            self.image = self.original
        else:
            rotate = pygame.transform.rotate
            self.image = rotate(self.original, self.dizzy)
        self.rect = self.image.get_rect(center=center)

    def punched(self):
        "this will cause the monkey to start spinning"
        if not self.dizzy:
            self.dizzy = 1
            self.original = self.image

pygame.init()
screen = pygame.display.set_mode((468, 60))
pygame.display.set_caption('Monkey Fever')
pygame.mouse.set_visible(0)

background = pygame.Surface(screen.get_size())
background = background.convert()
background.fill((250, 250, 250))

if pygame.font:
    font = pygame.font.Font(None, 36)
    text = font.render("Pummel The Chimp, And Win $$$", 1, (10, 10, 10))
    textpos = text.get_rect(centerx=background.get_width()/2)
    background.blit(text, textpos)


screen.blit(background, (0, 0))
pygame.display.flip()

whiff_sound = load_sound('whiff.wav')
punch_sound = load_sound('punch.wav')
chimp = Chimp()
fist = Fist()
allsprites = pygame.sprite.RenderPlain((fist, chimp))
clock = pygame.time.Clock()


while 1:
    clock.tick(60)


for event in pygame.event.get():
    if event.type == QUIT:
        return
    elif event.type == KEYDOWN and event.key == K_ESCAPE:
        return
    elif event.type == MOUSEBUTTONDOWN:
        if fist.punch(chimp):
            punch_sound.play() #punch
            chimp.punched()
        else:
            whiff_sound.play() #miss
    elif event.type == MOUSEBUTTONUP:
        fist.unpunch()

allsprites.update()


screen.blit(background, (0, 0))
allsprites.draw(screen)
pygame.display.flip()
```

---

### Post by trent.josephsen on 2012-02-05
Not without the rest of the code, they don't

---

### Post by MadCow108 on 2012-02-05
indent the code you marked read + a few lines below that
how many? no idea, its your code.
my guess is just the one line below the if

---

### Post by epicoder on 2012-02-05
There are a couple of problems with your code, all of them indentation problems.
first is the walk() function under the class Chimp. The changed lines are marked in red:
```
    def _walk(self):
        "move the monkey across the screen, and turn at the ends"
        newpos = self.rect.move((self.move, 0))
        if not self.area.contains(newpos):
[COLOR=Red]            if self.rect.left < self.area.left or \
            self.rect.right > self.area.right:
                self.move = -self.move[/COLOR]
            newpos = self.rect.move((self.move, 0))
        self.image = pygame.transform.flip(self.image, 1, 0)
        self.rect = newpos
```Then the main loop of the program is not actually in a loop. To fix this, increase the indentation of everything below the clock.tick line by 1 level. You can then just leave it in the "while 1:" loop but I added some error handling by first removing the loop and wrapping it in a function, named main():
```
def main():
    clock.tick(60)
    for event in pygame.event.get():
        if event.type == QUIT:
            return
        elif event.type == KEYDOWN and event.key == K_ESCAPE:
            return
        elif event.type == MOUSEBUTTONDOWN:
            if fist.punch(chimp):
                punch_sound.play() #punch
                chimp.punched()
            else:
                whiff_sound.play() #miss
        elif event.type == MOUSEBUTTONUP:
            fist.unpunch()

    allsprites.update()
    screen.blit(background, (0, 0))
    allsprites.draw(screen)
    pygame.display.flip()
```...And then writing a main loop with basic error handling.
```
if __name__=="__main__": #If the program is being run directly, and not imported as a module:
    while 1:
        try:
            main()
        except:
            print "Unexpected error:", sys.exc_info()[0]
            exit(1)
```As I don't have the required images, the code posted here is untested.

---

