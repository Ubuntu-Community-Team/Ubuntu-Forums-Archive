---
title: "Pygame: make images to fit screen"
date: 2009-04-27
forum: Programming Talk
---

### Post by matmatmat on 2009-04-27
Is there a way in pygame to make images to fit the screen:
```

from pygame import *
from pygame.locals import *
import time
def main():
    picture = pygame.image.load('Kubuntu_leaflet.jpg')
    pygame.display.set_mode((1280,1024),FULLSCREEN)
    main_surface = pygame.display.get_surface()
    a = 1
    while a == 1:
        main_surface.blit(picture, (0, 0))
        pygame.display.update()
        time.sleep(5)
        a = 0

if __name__ == "__main__":
    main()

```
?

---

### Post by unutbu on 2009-04-27
```
    picture = pygame.image.load('Examples/kubuntu-leaflet.jpg')
**    picture = pygame.transform.scale(picture,(1280,1024))**
    pygame.display.set_mode((1280,1024),FULLSCREEN)

```

I don't know if this is the best way, but this seems to work.

---

### Post by matmatmat on 2009-04-27
Thanks I now have this:
```

import pygame
from pygame import *
from pygame.locals import *
import time
import os
import sys

def main():
    images = []
    dirlist = os.listdir('/home/matio/Pictures/')
    for f in dirlist:
        if f.endswith('.jpg'):
            images.append('/home/matio/Pictures/' + f)
    main_surface = pygame.display.set_mode((1280,1024),FULLSCREEN)
    i = 0
    clock = pygame.time.Clock()
    print i
    print len(images)
    while i <= len(images):
        print i
        time_passed = clock.tick()
        time_passed = time_passed / 1000.0
        if time_passed >= 2:
            i += 1
            sys.exit()
        pressed_keys = pygame.key.get_pressed()
        if pressed_keys[K_RIGHT]:
            i += 1
        if i >= len(images):
            sys.exit()
        picture = pygame.image.load(images[i])
        picture = pygame.transform.scale(picture,(1280,1024))
        main_surface.blit(picture, (0, 0))
        pygame.display.update()

    sys.exit()

if __name__ == "__main__":
    main()

```
when I run it it hangs on the first image
also is there a way to center the image

---

### Post by unutbu on 2009-04-27
Again, I don't know if this is the best way to do it, but this seems to work for me:

PS. The code below uses pygame.time.set_timer(). This is what increments i every two seconds. I learned about it here:
[http://www.devshed.com/c/a/Python/A-PyGame-Working-Example-continued/](http://www.devshed.com/c/a/Python/A-PyGame-Working-Example-continued/)


[PHP]#!/usr/bin/env python
import pygame
from pygame import *
from pygame.locals import *
import time
import os
import sys

def main():
    images = []
    image_dir=os.path.join(os.environ['HOME'],'Pictures')
    dirlist = os.listdir(image_dir)
    for f in dirlist:
        if f.endswith('.jpg'):
            images.append(os.path.join(image_dir,f))
    main_surface = pygame.display.set_mode((1280,1024),FULLSCREEN)
    i = 0
    print i
    print len(images)

    #
    # Load an event into the timer
    # When this event occurs (every 2 seconds), i will be incremented
    #
    pygame.time.set_timer(pygame.USEREVENT + 1, 2000)
    while True:
        for event in pygame.event.get():
            if (event.type == pygame.QUIT): 
                sys.exit()
            elif (event.type == pygame.KEYDOWN and event.key == pygame.K_RIGHT): 
                i+=1
            elif event.type == pygame.USEREVENT + 1:
                i+=1
        print(i)
        if i >= len(images):
            sys.exit()
        picture = pygame.image.load(images[i])
        picture = pygame.transform.scale(picture,(1280,1024))
        main_surface.blit(picture, (0, 0))
        pygame.display.update()


if __name__ == "__main__":
    main()[/PHP]

---

### Post by hessiess on 2009-04-27
If you want your app to run resolution independent without lousing a lot of performance  you riley should look into using OpenGL as a renderer.

---

### Post by matmatmat on 2009-04-28
How much harder is OpenGL?

---

### Post by soltanis on 2009-04-28
It could be a lot harder. Chances are though, someone has done this before, and there is a library already out there to do it.

Quad-Ren is an example of one, but its for C++ unfortunately. Perhaps you could create python bindings?

---

### Post by hessiess on 2009-04-28
> 
How much harder is OpenGL?


OpenGL isn't that much harder to use than SDL (on which pygame is based), which indecently contains methods for creating an OpenGL rendering context. OpenGL can scale image and do alpha blits with very little performance loss (no more yucky aliasing). Though there are a number of limitations you should be awere of, All textures have to be powers of two for optimal compatibility and you need to catch the window resize event in SDL and resize the view port appropriately.

> 
Quad-Ren is an example of one, but its for C++ unfortunately. Perhaps you could create python bindings? 

Hay, what's wrong with C++ :P, Actually I have looked into creating a Python binding for QR using boost.python, but I couldn't even get boost to compile a simple single-function 'hello world' test app, so never took it any further :(.

Quad-Ren abstracts away almost everything related to actually drawing graphics, leaving you to worry about game logic and the like.

---

### Post by matmatmat on 2009-04-29
Thanks for the replies

---

