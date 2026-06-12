---
title: "Bouncy ball (pygame)"
date: 2013-03-15
forum: Programming Talk
---

### Post by ceil210 on 2013-03-15
I am making a pong game and am putting it together a piece at a time.   Right now I am working on a simple bouncy ball.  I can make it move, but  it wont bounce back.  Basically I don't know how to set up walls [IMG]http://www.codingforums.com/images/smilies/frown.gif[/IMG].  Here is my code:

```
#!/usr/bin/python
import pygame
import sys
from pygame.locals import *

x_vel = 1
y_vel = 1
x = 1
y = 1

pygame.init()
screen = pygame.display.set_mode((600,600),0,32)
screen.blit(screen, (0,0))

ball_img = pygame.image.load('ball.png')
ball_cover = pygame.image.load('blank_ball.png')
clock = pygame.time.Clock() 
ball_rect = ball_img.get_rect()

while True:
     for event in pygame.event.get():
          if event.type == QUIT:
               sys.exit()

     bounds_rect = pygame.Rect(x,y,0,0)
     ball_rect.clamp_ip(bounds_rect)
     x += x_vel
     y += y_vel
     screen.blit(ball_img, ball_rect)
     pygame.display.update()
     clock.tick(50)
     screen.blit(ball_cover, ball_rect)
```

---

### Post by r-senior on 2013-03-15
I don't know pygame but I've done this sort of thing before. All you need to do is work out the where your horizontal and vertical walls are. Lets say x=0, x=800 and y=0, y=600. (I don't know the coordinate system for pygame, but basically you want the limits of the window/screen). Then you have to work out when your ball will collide with a wall. It will be if any of these conditions are true:

a. if the centre x + radius >= 800
b. if the centre x - radius <= 0
c. if the centre y + radius >= 600
d. if the centre y - radius <= 0

When it collides, you just reverse the x or y velocity depending on which wall you hit. So if it was a wall based on the x coordinate, you'd reverse the x velocity and vice versa.

This only works if you start your ball in the middle so that it's not colliding of course.

---

