---
title: "Pygame rect collision problem"
date: 2009-08-23
forum: Programming Talk
---

### Post by abraxas_swa on 2009-08-23
Hi folks. I'm sure this is going to be something embarrassingly simple, but I'm working my way through some Pygame tutorials and putting together a simple 2D game in the process and I'm running into some problems with collision detection.

the Tux.colcheck() method seems to constantly return True - if anyone can point out why I'd be really grateful.

```
#! /usr/bin/env python

import pygame
from pygame.locals import *
from sys import exit
from gameobjects.vector2 import Vector2
from random import randint

class Tux():
	def __init__(self):
		self.image = pygame.image.load("tux.png").convert_alpha()			# Image source
		self.position = Vector2(30, 450)									# Position on screen
		self.direction = Vector2(0, 0)										# Where are we heading? y not used.
		self.speed = 300													# Pixel speed
		self.rect = pygame.Rect(0, 0, 131, 143)
		self.collide = False

	def get_key(self):
		key_pressed = pygame.key.get_pressed()

		if key_pressed[K_LEFT]:
			if self.position.x >= 30:
				self.direction.x = -1
			else:
				self.direction.x = 0										# Prevent Tux moving off screen left
		elif key_pressed[K_RIGHT]:
			if self.position.x <= 770 - self.image.get_width():
				self.direction.x = 1
			else:
				self.direction.x = 0
		else:
			self.direction.x = 0											# Prevent Tux moving off screen right

		self.direction.normalise()

	def move(self):
		self.position += self.direction * self.speed * sec_passed

	def colcheck(self, target):
		if target.rect.colliderect(self.rect):
			self.collide = True
		else:
			self.collide = False


class Apple():
	def __init__(self, applespeed):
		self.image = pygame.image.load("apple.png").convert_alpha()
		self.xstart = randint(120, 680)
		self.position = Vector2(self.xstart, 0)
		self.speed = applespeed
		self.rect = pygame.Rect(0, 0, 64, 64)

	def move(self):
		self.position.y += sec_passed * self.speed
		
pygame.init()

screen = pygame.display.set_mode((800, 600), 0, 32)
pygame.display.set_caption("TuxCatch!")
background = pygame.image.load("background.jpg").convert()
applespeed = 150
lives = 3
score = 0
collide = False

sprite = Tux()
apple = Apple(applespeed)
game_font = pygame.font.SysFont("Comic Sans MS", 32)


clock = pygame.time.Clock()


while True:

	for event in pygame.event.get():

		if event.type == QUIT:
			exit()


	if lives > 0:
		sprite.get_key()

		screen.blit(background, (0, 0))
		screen.blit(sprite.image, (sprite.position))

		lives_display = game_font.render("Lives: %i" % lives, True, (255, 255, 0))
		screen.blit(lives_display, (20, 5))

		if apple.position.y < 600 and sprite.collide == True:
			score += 1
			apple.position = Vector2(randint(120, 680), 0)
		elif apple.position.y < 600 and sprite.collide == False:
			pass
		else:
			lives -= 1
			apple.position = Vector2(randint(120, 680), 0)

		screen.blit(apple.image, (apple.position))

		time_passed = clock.tick(30)
		sec_passed = time_passed / 1000.0
		sprite.move()
		apple.move()
		sprite.colcheck(apple)

		pygame.display.update()

	else:		
		screen.blit(background, (0, 0))
		over_msg = game_font.render("GAME OVER!", True, (225, 150, 225))
		screen.blit(over_msg, (300, 400))

		pygame.display.update()
```

---

### Post by dracule on 2009-08-23
im not familiar with pygame all too much (im more of a pyglet man) but it appears that you arent moving the Rectangles when you move the Tux and Apple pieces. thus they just at their default coords (0, 0) on top of each other so of course they will always collide

---

### Post by JordyD on 2009-08-23
Instead of defining your own rect, use the surface's (or sprite.image) get_rect method.

diff:
```
15c15
< 		self.rect = pygame.Rect(0, 0, 131, 143)
---
> 		self.rect = self.image.get_rect()
52c52
< 		self.rect = pygame.Rect(0, 0, 64, 64)
---
> 		self.rect = self.image.get_rect()

```

I would have tested it, but I did not have a gameobjects module.

---

