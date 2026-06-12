---
title: "Please constructively criticise my langtons ant"
date: 2008-07-14
forum: Programming Talk
---

### Post by glolite on 2008-07-14
Hi everyone,

As a recent python adopter, I looked through some of the past challenges and had a go at the langtons ant challenge.

I created a class for the ant, and then upon clicking on the screen a new ant should be generated at that location.

I was after some consructive suggestions about my coding style / habits, to improve my code.

One thing I am particularly interested in, is keeping track of instances of a class, in this situation I created a list and everytime an ant was created I appended it to this list, is there a better way? the code is below

Main Program
```


import pygame
import random
import langant

# Window dimensions
width = 800
height = 800

screen = pygame.display.set_mode((width, height))
clock = pygame.time.Clock()
running = True

ant = langant.LangAnt()
ant.setxy(400,400, (255,255,255))
listofant = []

while running:
	
    ant.ant(screen)
    for i in listofant:
        i.ant(screen)

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
	elif event.type == pygame.MOUSEBUTTONDOWN and event.button == 1:
		print "You pressed the left mouse button at (%d, %d)" % event.pos
		x, y = event.pos
		x -= x%5
		y -= y%5
		z = langant.LangAnt()
		a = (random.randint(0,255))
		b = (random.randint(0,255))
		c = (random.randint(0,255))
		z.setxy(x,y, (a,b,c))
		listofant.append(z)

 
    pygame.display.flip()
    clock.tick(50)

```

Ant Class

```

class LangAnt:
	"Creates a langdon's ant"
	import pygame
	white = (255,255,255)
	black = (0,0,0)
	dirs = [(0,5),(5,0),(0,-5),(-5,0)]
	dircount = 0
	direction = dirs[dircount]
	x,y = 0,0
	color = (255,255,255)

	def ant(self, screen):
		def square(x,y,color):
    			for i in range(x,x+4):
        			for j in range(y,y+4):
            				screen.set_at((i,j),(color))

		if screen.get_at((self.x,self.y)) != (0,0,0,255):
        		square(self.x,self.y,self.black)
        		if self.dircount == 0:
            			self.dircount = 3
			else:
            			self.dircount -= 1 
        		self.direction = self.dirs[self.dircount]
    
    		else:
			square(self.x,self.y,self.color)
			if self.dircount == 3:
            			self.dircount = 0
			else:
            			self.dircount += 1 
        		self.direction = self.dirs[self.dircount]
    
    		j,k = self.direction
    		self.x += j
    		self.y += k
    
    		if self.x < 0:
        		self.x = 790
    		elif self.x > 795:
        		self.x = 0
    

    		if self.y < 0:
        		self.y = 790
    		elif self.y > 795:
        		self.y = 0
		
	def setxy(self, x, y, color):
		self.x = x
		self.y = y
		self.color = color


```

thanks!

---

