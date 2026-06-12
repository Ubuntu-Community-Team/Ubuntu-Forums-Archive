---
title: "Pygame Won't Open .jpg"
date: 2012-03-04
forum: Programming Talk
---

### Post by didinium on 2012-03-04
I have been programming in straight up python for a while now and I recently decided to try pygame. I looked up a tutorial and saw one of those cursor = ball kind of programs. I started to get to work on one but every time it runs it cant open a background jpg. This jpg was in my home folder so I have no idea what I'm doing wrong. Any help would be appreciated. Here is the script.
```
#!/usr/bin/python

bif="bg.jpg"
mif="ball.png"

import pygame, sys
from pygame.locals import *

pygame.init()
screen=pygame.display.set_mode((1000, 475),0,32)

background=pygame.image.load(bif).convert()
mousec=pygame.image.load(mif).convert_alpha()

while True:
 for event in pygame.event.get():
  if event.type == QUIT:
   pygame.quit()
   sys.exit()
 screen.blit(background, (0,0))
```

---

### Post by didinium on 2012-03-04
Solved it. My photo had to be in the file with my program.

---

### Post by Hetepeperfan on 2012-03-04
yes but the pictures do not really have to be in the same folder. But then you should provide a absolute pathname. eg. a picture can be loaded from you home folder like:

```
background = pygame.image.load( "~/" + bif)
``````
background = pygame.image.load( "/home/yourname/picturename.jpg" )
```good luck

---

