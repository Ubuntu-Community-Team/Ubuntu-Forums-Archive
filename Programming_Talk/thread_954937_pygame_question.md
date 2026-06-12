---
title: "pygame question"
date: 2008-10-21
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-10-21
so since ive realized python gives me the best option for making my own game since i am very busy with school

but i am having a very silly and probably simple problem

when i try to import pygame it says it isnt found so i noticed i had to put it in a path that my compiler looked at

now i am looking at the entire pygame lib and there are a lot of files in there

my tutorial says i need to include:

```
include pygame
from pygame.locals include *
```

yet i cannot find a python object file in the lib but i can find a locals file...

this is very confusing

---

### Post by WW on 2008-10-21
> **jimi_hendrix said:**
> 

when i try to import pygame it says it isnt found
Are you using Ubuntu?  If so, all you should have to do is install the package **python-pygame**, either with Synaptic or with apt-get like this
```

sudo apt-get install python-pygame

```
and it should Just Work.

---

### Post by jimi_hendrix on 2008-10-21
ok ill try that when i go on ubuntu in a bit

---

### Post by WW on 2008-10-21
> **jimi_hendrix said:**
> 
```
include pygame
from pygame.locals include *
```

I just noticed those *include*s in there... they should be **import**, not *include*.

---

### Post by jimi_hendrix on 2008-10-21
gives syntax error

i would still like to know what im doing wrong so that i can avoid it in the future

---

### Post by WW on 2008-10-21
> **jimi_hendrix said:**
> gives syntax error


*What* gives a syntax error?  Show the command(s) that you used, and show the output.

---

### Post by jimi_hendrix on 2008-10-21
```

import os, sys
import pygame
from pygame.locals include *
```

thats the code...i just want this part to compile now

heres what the output is

```

from pygame.locals include *
                         ^

SyntaxError: invalid syntax

```

---

### Post by WW on 2008-10-21
**import**, not include. E.g.
```

from pygame.locals import *

```

---

### Post by jimi_hendrix on 2008-10-21
*sigh* now it cant find pygame...
understandable because in the file i downloaded i cant find a pygame object either...

---

### Post by WW on 2008-10-21
You are on Ubuntu, and you have the Ubuntu package [python-pygame](http://packages.ubuntu.com/hardy/python-pygame) installed?

What happens if, in a terminal, you run python with no arguments, and type **import pygame**?  For example,
```

$ python
Python 2.5.2 (r252:60911, Jul 31 2008, 17:28:52) 
[GCC 4.2.3 (Ubuntu 4.2.3-2ubuntu7)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import pygame
>>> 

```

---

### Post by jimi_hendrix on 2008-10-21
works...or at least for now

i will post any further problems as they come

---

### Post by jimi_hendrix on 2008-10-22
new problem but one not directly related to programming

im following the pygame tutorial where you make the "punch the monkey game" but one problem...i need to find a picture of a fist to punch the monkey with but am having trouble...ideas (ive tried google images)

---

### Post by sheto on 2008-10-22
Which tutorial are you following? I would be very interested to use Pygame.

---

### Post by fiddler616 on 2008-10-22
You can't just draw a fist that's good-enough?

---

### Post by jimi_hendrix on 2008-10-22
[http://www.pygame.org/docs/tut/chimp/ChimpLineByLine.html](http://www.pygame.org/docs/tut/chimp/ChimpLineByLine.html)

tell me if you get a good pic of a fist i can use...heres my monkey that i gimped

---

### Post by jimi_hendrix on 2008-10-22
> **fiddler616 said:**
> You can't just draw a fist that's good-enough?

you havnt seen my artwork...ill try though

---

### Post by fiddler616 on 2008-10-22
> **jimi_hendrix said:**
> you havnt seen my artwork...ill try though
I'd offer to help, but you haven't seen *my* artwork for a very good reason. I could probably do it with pencil/paper, but I don't have a scanner.
Anyway, the tutorial's sample seems to be a picture of the programmer's fist...you could try that...
*Googles*...hmm, you're right. Have you tried this: [http://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Fist.png/421px-Fist.png](http://upload.wikimedia.org/wikipedia/commons/thumb/1/17/Fist.png/421px-Fist.png)
?
Edit: There's also this: [http://www.istockphoto.com/file_thumbview_approve/5521201/2/istockphoto_5521201-sketch-fist.jpg](http://www.istockphoto.com/file_thumbview_approve/5521201/2/istockphoto_5521201-sketch-fist.jpg)

---

### Post by jimi_hendrix on 2008-10-22
those wouldnt work because of the angle of the game...but i was able to gimp it off of the screenshot :)

thanks anyway

---

### Post by WW on 2008-10-22
Looks like you can get fist.bmp and chimp.bmp [here](http://formation.bearstech.com/trac/browser/pygame/examples/data?rev=4).

---

### Post by jimi_hendrix on 2008-10-22
thanks

---

### Post by jimi_hendrix on 2008-10-22
now it says the load_image function is not defined but after even copying and pasting the entire source code from the site to check this i still get there error

heres the source code

[PHP] #/usr/bin/env python
"""
This simple example is used for the line-by-line tutorial
that comes with pygame. It is based on a 'popular' web banner.
Note there are comments here, but for the full explanation, 
follow along in the tutorial.
"""


#Import Modules
import os, pygame
from pygame.locals import *

if not pygame.font: print 'Warning, fonts disabled'
if not pygame.mixer: print 'Warning, sound disabled'


#functions to create our resources
def load_image(name, colorkey=None):
    fullname = os.path.join('data', name)
    try:
        image = pygame.image.load(fullname)
    except pygame.error, message:
        print 'Cannot load image:', fullname
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
    if not pygame.mixer or not pygame.mixer.get_init():
        return NoneSound()
    fullname = os.path.join('data', name)
    try:
        sound = pygame.mixer.Sound(fullname)
    except pygame.error, message:
        print 'Cannot load sound:', fullname
        raise SystemExit, message
    return sound


#classes for our game objects
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
        if self.rect.left < self.area.left or \
           self.rect.right > self.area.right:
            self.move = -self.move
            newpos = self.rect.move((self.move, 0))
            self.image = pygame.transform.flip(self.image, 1, 0)
        self.rect = newpos

    def _spin(self):
        "spin the monkey image"
        center = self.rect.center
        self.dizzy = self.dizzy + 12
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


def main():
    """this function is called when the program starts.
       it initializes everything it needs, then runs in
       a loop until the function returns."""
#Initialize Everything
    pygame.init()
    screen = pygame.display.set_mode((468, 60))
    pygame.display.set_caption('Monkey Fever')
    pygame.mouse.set_visible(0)

#Create The Backgound
    background = pygame.Surface(screen.get_size())
    background = background.convert()
    background.fill((250, 250, 250))

#Put Text On The Background, Centered
    if pygame.font:
        font = pygame.font.Font(None, 36)
        text = font.render("Pummel The Chimp, And Win $$$", 1, (10, 10, 10))
        textpos = text.get_rect(centerx=background.get_width()/2)
        background.blit(text, textpos)

#Display The Background
    screen.blit(background, (0, 0))
    pygame.display.flip()

#Prepare Game Objects
    clock = pygame.time.Clock()
    whiff_sound = load_sound('whiff.wav')
    punch_sound = load_sound('punch.wav')
    chimp = Chimp()
    fist = Fist()
    allsprites = pygame.sprite.RenderPlain((fist, chimp))

#Main Loop
    while 1:
        clock.tick(60)

    #Handle Input Events
        for event in pygame.event.get():
            if event.type == QUIT:
                return
            elif event.type == KEYDOWN
	    and event.key == K_ESCAPE:
                return
            elif event.type == MOUSEBUTTONDOWN:
                if fist.punch(chimp):
                    punch_sound.play() #punch
                    chimp.punched()
                else:
                    whiff_sound.play() #miss
            elif event.type is MOUSEBUTTONUP:
                fist.unpunch()

        allsprites.update()

    #Draw Everything
        screen.blit(background, (0, 0))
        allsprites.draw(screen)
        pygame.display.flip()

#Game Over


#this calls the 'main' function when this script is executed
if __name__ == '__main__': main()
[/PHP]

---

### Post by WW on 2008-10-22
In the directory in which you are working, create a subdirectory called "data", and put the .bmp files in there.

---

### Post by jimi_hendrix on 2008-10-22
i get this

```

ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Traceback (most recent call last):
  File "test.py", line 92, in <module>
    chimp = Chimp()
  File "test.py", line 40, in __init__
    self.image, self.rect = load_image("monkey.bmp")
NameError: global name 'load_image' is not defined

```

---

### Post by WW on 2008-10-22
The function load_image is defined earlier in the file; it starts like this:
```

#functions to create our resources
def load_image(name, colorkey=None):
    fullname = os.path.join('data', name)
    try:
.
.
.

```
Does your python file have that definition?

---

### Post by jimi_hendrix on 2008-10-22
wow me == not enough sleep or control + A + control + C lied to me...

well last error i think

```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```

---

### Post by WW on 2008-10-22
That has something to do with sound.  Sorry, I'm not sure what to do about that.

---

### Post by jimi_hendrix on 2008-10-22
ok thanks anyway

just curious (i know how hard it is to make games and that it takes teams of professionals years to make a real game) but what language would i be able to make games in with the least amount of time since my time is so limited now...

---

