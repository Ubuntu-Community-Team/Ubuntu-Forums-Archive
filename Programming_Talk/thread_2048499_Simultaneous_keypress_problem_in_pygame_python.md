---
title: "Simultaneous keypress problem in pygame python"
date: 2012-08-26
forum: Programming Talk
---

### Post by Aqil on 2012-08-26
I'm trying to make a triangle move around in a top-down view environment. He (the triangle is a he) rotates when left or right arrow is pressed down. He moves in the direction he's facing when up arrow is pressed down. The below code is working fine except for when several arrows are held in simultaneously.

For example, when you hold up key and then also hold left key the little guy will spin around as he's supposed to, but he keeps moving in a fixed path, which he's not supposed to do. If he rotates while walking, then the direction in which he is walking should change continuously, so that he's always moving towards wherever he's facing.

Hope this makes sense. Otherwise, feel free to try it out with some little image of your own.

How can I make the triangle move around smoothly on the screen? What's wrong with my code below and how could I modify it to make the controls smoother?

```
import pygame, sys, math
from pygame.locals import *

pygame.init() # initiates the game
screen = pygame.display.set_mode((680,384),0,32) # screen settings
clock = pygame.time.Clock()
speed = 60 # puts and upper boandary for the speed of the game

blue = 0,0,255

protagonist0=pygame.transform.scale(pygame.image.load('triangle.jpg').convert_alpha(),(25,25)) # load, resize and name protagonist image

x,y = 340,192
newx,newy = 0,0
angle = 90 # initial angle, if 90 protagonist is facing upward
newangle = 0
turn_speed = 4 # the amount of degrees to rotate when pressing left or right key
walk_speed = 2 # the speed in which the protagonist moves over the map

while True:
	for event in pygame.event.get():
		keystate = pygame.key.get_pressed() # enbles sensing multiple key strokes
		if event.type == QUIT: # enables exiting the game
			pygame.quit()
			sys.exit()
		elif event.type == KEYDOWN: # all keydowns in this conditional statement
			if keystate[K_ESCAPE]:
				pygame.quit()
				sys.exit()			
			elif keystate[K_UP] and keystate[K_LEFT]:
				newx = +math.cos(math.radians(angle))*walk_speed
				newy = -math.sin(math.radians(angle))*walk_speed
				newangle = +turn_speed
			elif keystate[K_DOWN] and keystate[K_LEFT]:
				newx = -math.cos(math.radians(angle))*walk_speed
				newy = +math.sin(math.radians(angle))*walk_speed
				newangle = +turn_speed
			elif keystate[K_UP] and keystate[K_RIGHT]:
				newx = +math.cos(math.radians(angle))*walk_speed
				newy = -math.sin(math.radians(angle))*walk_speed
				newangle = -turn_speed
			elif keystate[K_DOWN] and keystate[K_RIGHT]:
				newx = -math.cos(math.radians(angle))*walk_speed
				newy = +math.sin(math.radians(angle))*walk_speed
				newangle = -turn_speed
			elif keystate[K_RIGHT]:
				newangle = -turn_speed
			elif keystate[K_LEFT]:
				newangle = +turn_speed
			elif keystate[K_UP]:
				newx = +math.cos(math.radians(angle))*walk_speed
				newy = -math.sin(math.radians(angle))*walk_speed
			elif keystate[K_DOWN]:
				newx = -math.cos(math.radians(angle))*walk_speed
				newy = +math.sin(math.radians(angle))*walk_speed
		elif event.type == KEYUP: # all keyups in this conditional statement
			if event.key == K_LEFT:
				newangle = 0
			elif event.key == K_RIGHT:
				newangle = 0
			elif event.key == K_UP:
				newx = 0
				newy = 0
			elif event.key == K_DOWN:
				newx = 0
				newy = 0
	x += newx # enables moving the protagonist
	y += newy # enables moving the protagonist
	angle += newangle # enables rotation of protagonist
	screen.fill(blue) # sets the background color
	protagonist1 = pygame.transform.rotate(protagonist0,angle-90) # rotates the protagonist image
	screen.blit(protagonist1,(x,y)) # insert the image of the protagonist at position x,y
	clock.tick(speed) # limits the speed of the game, where speed is a variable set outside of the loop
	pygame.display.flip() # prints/updates the game
	pygame.display.update() # makes the game run smoothly

```

I found [this old thread]("http://ubuntuforums.org/showthread.php?t=1436302") with someone who had a very similar problem. I tried playing his game ([which is still downloadable]("http://ubuntuforums.org/showpost.php?p=9061150&postcount=38")) and his car is running quite smoothly. But with all the different files, defs and classes, I can't get my head around how it works. I'm working on learning how to use those things, but first things first. Why is my guy not moving as smoothly and diligently as the car in this guy's game (yes, I'm jealous)? Which part should I look closer at?

---

