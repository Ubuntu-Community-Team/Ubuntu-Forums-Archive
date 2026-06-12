---
title: "Python and pygame"
date: 2006-09-21
forum: Programming Talk
---

### Post by Tomosaur on 2006-09-21
Hi guys, I decided to get my feet wet with pygame. I like the idea of being able to make games, but I've never bothered with animation etc, usually just text-based games or stuff where all of the low-level animation processes are done automatically. For this reason, I need to learn about how animation works at this low level, and so that's what I'm trying to do:
```

import pygame
from pygame.locals import *

screen = pygame.display.set_mode((800,600))
background = pygame.image.load("/home/tom/workspace/Undercover/data/bark.jpg")
running = 1
pygame.mouse.set_visible(0)
light = pygame.Rect(0,0, 20, 20)
screen.blit(background, light)
while running:
    for event in pygame.event.get():  
        if event.type == MOUSEMOTION:
            light.center = pygame.mouse.get_pos()
        elif event.type == KEYDOWN:
            if event.key == K_ESCAPE:
                running = 0
      
        pygame.display.update(light)

```

What I'm trying to do is have the user reveal only a small portion of the underlying background image. I've tried a multitude of different things, and nothing has worked properly yet. Don't be fooled about how this code LOOKS like it won't do what I want - I know that, I just stripped out all of the stuff I know doesn't work. What this code does do is load a black screen, where the underlying image is revealed bit by bit as the user moves the mouse. However, the mouse 'trail' is still left behind. I need the screen to be black except for where the current mouse cursor is. I know there must be some way to do this, so if anybody colud help me out here I'd be very grateful.

---

