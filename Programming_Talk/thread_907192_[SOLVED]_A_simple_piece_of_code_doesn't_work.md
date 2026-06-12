---
title: "[SOLVED] A simple piece of code doesn't work"
date: 2008-09-01
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-09-01
This should draw two images, but it draws only one:
```
#!/usr/bin/python

import pygame
from pygame.locals import *

def main():
	# Initialise screen
	pygame.init()
	screen = pygame.display.set_mode((400, 400))
	pygame.display.set_caption('Basic Pygame program')

	# Fill background
	background = pygame.Surface(screen.get_size())
	background = background.convert()
	background.fill((250, 250, 250))

	# sprites
	global sprites
	sprites = []
	
	class Spr(object):
		pass
	
	def sprite_add(fname, position):
		global sprites
		sprite = Spr
		sprite.pos = position
		sprite.file = pygame.image.load(fname)
		sprites += [sprite]
		
	sprite_add("test.bmp", (0,0))
	
	sprite_add("test.bmp", (100,100))
	
	# Blit everything to the screen
	screen.blit(background, (0, 0))
	
	for x in sprites:
		screen.blit(x.file, (x.pos[0], x.pos[1]))
		
	pygame.display.flip()
	
	
	# Event loop
	while 1:
		for event in pygame.event.get():
			if event.type == QUIT:
				return

		screen.blit(background, (0, 0))

		for x in sprites:
			screen.blit(x.file, (x.pos[0], x.pos[1]))
		
		pygame.display.flip()

if __name__ == '__main__': main()
```
What is the problem? I don't get it.

---

### Post by y-lee on 2008-09-01
The problem is the way you are defining the class Spr try something like the below :

```
	class Spr(object):
		def __init__(self,position,fname):
			self.pos = position
			self.file = pygame.image.load(fname)
		
	
	def sprite_add(fname, position):
		global sprites
		sprite = Spr(position,fname)
		sprites += [sprite]
```

---

### Post by crazyfuturamanoob on 2008-09-01
Thank you! It works, but could somebody explain me, how it works?

---

### Post by WW on 2008-09-01
In your code posted above, in the sprite_add function, try changing
```

		sprite = Spr

```
to
```

		sprite = Spr()

```
The line "sprite = Spr" doesn't create an instance of the Spr class; it simply duplicates the class definition.  (y-lee has created an explicit initializer for the class, which is a nicer way to create the instances.)

---

