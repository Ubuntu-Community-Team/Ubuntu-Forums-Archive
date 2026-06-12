---
title: "python app crashes after launch"
date: 2012-06-27
forum: Programming Talk
---

### Post by gr8gui on 2012-06-27
when i run:

#!/usr/bin/env python

import pygame, sys
import pygame.camera
from pygame.locals import *

pygame.init()
pygame.camera.init()

screen = pygame.display.set_mode((640,480))

cam =pygame.camera.Camera("/dev/video0",(640,480))
cam.start()

while 1:
    image = cam.get_image()
    screen.blit(image,(0,0))
    pygame.display.update()
    for event in pygame.event.get():
	if event.type ==pygame.QUIT:
	    sys.exit()
_________________________________________________________________
window opens and then crashes returning:
(pygame parachute) Segmentation Fault
Aborted (core dumped)

---

### Post by Vaphell on 2012-06-27
use [code] [/co****de] tags, especially when you paste code. Indentation, especially in case of python, is crucial.
This one is not complicated so it's easy to guess but you shouldn't make it harder than necessary for people willing to help.

---

### Post by MG&amp;TL on 2012-06-27
Obvious question...you do have a webcam, and its device name is /dev/video0, right?

---

### Post by gr8gui on 2012-06-27
I see the webcam stream for a fraction of a second.

---

### Post by MG&amp;TL on 2012-06-27
Hm. Okay, what happens if you substitute "pygame.display.update()" with "pygame.display.flip"? To quote their manual, pygame.display.update() on pygame.OPENGL displays will "cause an exception".

---

### Post by gr8gui on 2012-06-27
same thing. now it lasts a little more but still crashes

---

### Post by MG&amp;TL on 2012-06-27
Sorry, no idea.

Hopefully someone else has an idea, or you could try one of the pygame forums.

---

### Post by greenpeace on 2012-06-28
Your code works fine on my machine... 

...does your webcam work well with cheese or any other webcam application?

---

### Post by Bodsda on 2012-06-28
It would be useful to have the traceback and any messages that are printed to stdout

---

### Post by MG&amp;TL on 2012-06-28
> **Bodsda said:**
> It would be useful to have the traceback and any messages that are printed to stdout

"(pygame parachute) Segmentation Fault
Aborted (core dumped)"

;)

---

### Post by gr8gui on 2012-06-29
yes my webcam works well in cheese. I will try another webcam and seeifit works

---

