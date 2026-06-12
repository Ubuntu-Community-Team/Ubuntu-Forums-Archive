---
title: "Pygame Graph"
date: 2009-07-17
forum: Programming Talk
---

### Post by matmatmat on 2009-07-17
I have this code:
```

import pygame
from pygame.locals import *
from sys import exit, argv
from random import randint


class s:
	def __init__(self):
		self.sf = 0
		self.xi = 0
		self.yi = 0
		self.t = ""
		self.xt = ""
		self.yt = ""

SCREENX = 600
SCREENY = SCREENX

points = []
stuff = []
s = s()
def get_points():
	x = ""
	while x != "q":
		try:
			x = raw_input("Enter x co-ordinate (q to quit):")
			y = raw_input("Enter y co-ordinate (q to quit):")
		except:
			pass
		if x == "q":
			break
		x = int(x)
		y = int(y)	
		stuff.append(x)
		stuff.append(y)
	s.xi = int(raw_input("Please enter the x increase: "))
	s.yi = int(raw_input("Please enter the y increase: "))
	s.t = raw_input("Please enter the title: ")
	s.xt = raw_input("Please enter the x title: ")
	s.yt = raw_input("Please enter the y title: ")
	maxp = max(stuff)
	if maxp < (SCREENX / 100):
		s.sf = 100
	if maxp > (SCREENX / 100):
		s.sf = 50
	if maxp > (SCREENX / 50):
		s.sf = 25
	if maxp > (SCREENX / 25):
		s.sf = 10
	count = 0
	for i in range(len(stuff)):
		try:
			if stuff[count] == 0:
				stuff[count] = 1 
			if stuff[count + 1] == 0:
				stuff[count + 1] = 1
			x = stuff[count] * s.sf 
			y = SCREENY - (stuff[count + 1] * s.sf) 
			points.append((x, y))
		except:
			break
		count += 2
	

if len(argv) > 1:
	f = open(argv[1], "r")
	li = f.readlines()
	for l in range(len(li)):
		if li[l].strip() == "#":
			s.xi = int(li[l + 1])
			s.yi = int(li[l + 2])
			s.t = li[l + 3]	
			s.xt = li[l + 4]
			s.yt = li[l + 5]
			break
		else:
			if l % 2 == 0 or l == 0:
				x = int(li[l])
			else:
				y = int(li[l])
				stuff.append(x)
				stuff.append(y)
	maxp = max(stuff)
	if maxp < (SCREENX / 100):
		s.sf = 100
	if maxp > (SCREENX / 100):
		s.sf = 50
	if maxp > (SCREENX / 50):
		s.sf = 25
	if maxp > (SCREENX / 25):
		s.sf = 10
	count = 0
	for i in range(len(stuff)):
		try:
			if stuff[count] == 0:
				stuff[count] = 1
			if stuff[count + 1] == 0:
				stuff[count + 1] = 1
			x = stuff[count] * s.sf  
			y = SCREENY - (stuff[count + 1] * s.sf) 
			points.append((x, y))
		except:
			break
		count += 2
	

else: 
	get_points()
pygame.init()



screen = pygame.display.set_mode((SCREENX,SCREENY),0,32)
col = randint(1,255)
col2 = randint(1,255)
col3 = randint(1,255)
while True:
	screen.fill((255,255,255))
	pygame.draw.aaline(screen, (0, 0, 0), (30, 30), (30, SCREENY - 30)) 
	pygame.draw.aaline(screen, (0, 0, 0), (30, SCREENY - 30), (SCREENX - 10, SCREENY - 30))
	for i in range(len(points)):
		pygame.draw.circle(screen, (col, col2, col3), points[i - 1], 3)
		pygame.draw.circle(screen, (col, col2, col3), points[i], 3)
		pygame.draw.aaline(screen, (col, col2, col3), points[i - 1], points[i])
	font = pygame.font.SysFont("arial", 10)
	font_height = font.get_linesize()
	count = 0 
	for i in range(SCREENY - 35):
		   if (i % s.sf) == 0:
			count += 1
	for i in range(SCREENY - 35):
		   if (i % s.sf) == 0:
			text_surface = font.render(str(count), True, (0,0,0))
			screen.blit(text_surface, (25, i))
			count -= s.xi
	
	text_surface = font.render(s.xt.strip(), True, (0,0,0))
	screen.blit(text_surface, (SCREENX/2, SCREENY - 15))
	text_surface = font.render(s.yt.strip(), True, (0,0,0))
	text_surface = pygame.transform.rotate(text_surface, 90)
	screen.blit(text_surface, (0, SCREENY/2))
	count = 1
	for i in range(SCREENX - 30):
		   if i == 0:
			i += 30 
		   if (i % s.sf) == 0:
			text_surface = font.render(str(count), True, (0,0,0))
			screen.blit(text_surface, (i, SCREENY - 30))
			count += s.yi
	font = pygame.font.SysFont("arial", 20)
	font_height = font.get_linesize()
	text_surface = font.render(s.t.strip(), True, (0,0,0))
	screen.blit(text_surface, (SCREENX/2, SCREENY - (SCREENY - 5)))
	pygame.display.update()
    	for event in pygame.event.get():
            if event.type == QUIT:
		pygame.image.save(screen, s.t + ".jpg")
                exit()

```
when run with this file:
```

1
3
2
2
3
20
#
1
1
Number of volleys
Tries
Volleys

```
it gives the attached image, which is not lined up properly, but why?

---

### Post by bodyharvester on 2009-07-17
problemsolving with code, im totally new to this but id like to think...

the code is providing different output for positioning the graph (not data on graph) on the screen and the data for the graph is shown on the screen not graph like layers...

is that right? or clear?

what i mean is the graph is say x from side of screen but data on graph is y form screen not on the graph

am i close?

---

### Post by matmatmat on 2009-07-18
When the user enters a set of data - say (1,1) (2,2) (3,3) (4,4) - it chooses a number to multiply it with (in this case 100), then it draws the points.Then, every 100 pixels, it blits a number
What I need to find is the right numbers to multiply the user entered numbers with (I think)

---

