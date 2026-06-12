---
title: "Cellular Automata with Pygame"
date: 2009-09-28
forum: Programming Talk
---

### Post by Mousie_kebabs on 2009-09-28
Hello everyone!

It's 4:32 am and I've just finished my first Pygame project, it's a recreation of Conway's Game of Life. This is also my first project with classes so please any tips would be helpful :)

Use the mouse to place cells and press space to cycle through generations.

Simply run the following script and it should work, enjoy.

[PHP]#!/usr/bin/python

import pygame, sys, random
from pygame.locals import *

Cells = {}

class classCell:
	def __init__(self, x, y, state):
		self.x = x
		self.y = y
		self.w = 10
		self.h = 10
		self.Lneigh = 0
		self.Dneigh = 0
		self.state = state

	def getState(self):
		return self.state
	def AddNeigh(self, state):
		if state == 1:
			self.Lneigh += 1
		elif state == 0:
			self.Lneigh += 0
	def getNeigh(self):
		return self.Lneigh
	def Draw(self, surf):
		if self.state == 0:
			self.col = (255, 255, 255)
		elif self.state == 1:
			self.col = (0, 0, 0)
		pygame.draw.rect(surf, self.col, (self.x * self.w, self.y * self.h, self.w, self.h), 0)

def UpdateNeighs():
	x = 0
	y = 0
	for y in range(0, (400 / 10)):
		for x in range(0, (400 / 10)):
			Cells[x, y].Lneigh = 0 
			if y - 1 > -1 and x - 1 > -1 and x + 1 < 40 and y + 1 < 40:
				Cells[x, y].AddNeigh(Cells[(x - 1), (y - 1)].state)   #Top Left
				Cells[x, y].AddNeigh(Cells[(x), (y - 1)].state)       #Top
				Cells[x, y].AddNeigh(Cells[(x + 1), (y - 1)].state)   #Top Right
				Cells[x, y].AddNeigh(Cells[(x - 1), (y + 1)].state)   #Bottom Left
				Cells[x, y].AddNeigh(Cells[(x), (y + 1)].state)       #Bottom
				Cells[x, y].AddNeigh(Cells[(x + 1), (y + 1)].state)   #Bottom Right
				Cells[x, y].AddNeigh(Cells[(x - 1), (y)].state)       #Left
				Cells[x, y].AddNeigh(Cells[(x + 1), (y)].state)       #Right

def UpdateStates():
	x = 0
	y = 0
	for y in range(0, (400 / 10)):
		for x in range(0, (400 / 10)):

			if Cells[x, y].Lneigh != 2 and Cells[x, y].Lneigh != 3:    # Under/Over populated
				Cells[x, y].state = 0
			elif Cells[x, y].Lneigh == 2 and Cells[x, y].Lneigh == 3:  #Lives to next cycle
				Cells[x, y].state = 1
			elif Cells[x, y].state == 0 and Cells[x, y].Lneigh == 3:  #Dead cell comes to life
				print "New Cell born"
				Cells[x, y].state = 1

class Cursor:
	def __init__(self, x, y, w, h, col):
		self.x = x
		self.y = y
		self.w = w
		self.h = h
		self.col = col
	def Move(self, x, y):
		self.x = x
		self.y = y
	def Draw(self, surf):
		pygame.draw.rect(surf, self.col, (self.x * self.w, self.y * self.h, self.w, self.h), 1)
		
		

def drawGrid(surf, size):
	surf.fill((255, 255, 255))
	x = 0
	y = 0
	for y in range(0, (400 / size)):
		for x in range(0, (400 / size)):
			Cells[x, y] = classCell(x, y, 0)
			pygame.draw.line(surf, (230, 230, 230), (x * size, 0), (x * size, 400))
			pygame.draw.line(surf, (230, 230, 230), (0, y * size), (400, y * size))

def main():
	pygame.init()
	screen = pygame.display.set_mode((400, 400))
	pygame.display.set_caption('Cellular Automata')
	grid = pygame.surface.Surface((400, 400))
	surf_buf = pygame.surface.Surface((400, 400))

	CursRect = Cursor(0, 0, 10, 10, (255, 0, 0))

	drawGrid(grid, 10)
	Cycle = 0
	while 1:
		for event in pygame.event.get():
			if event.type == QUIT:
				sys.exit()
				return
			elif event.type == MOUSEMOTION:
				mx, my = pygame.mouse.get_pos()
				mx = (mx / 10)
				my = (my / 10)
				
				CursRect.Move(mx, my)
			elif event.type == pygame.MOUSEBUTTONUP:
				if event.button == 1:
					print "Cell %i, %i = 1" % (mx, my) 
					Cells[mx, my].state = 1
				elif event.button == 3:
					print Cells[mx, my].Lneigh
			elif event.type == pygame.KEYUP:
				if event.key == 32:
					Cycle = Cycle + 1
					print "Cycle ", Cycle
					UpdateNeighs()
					UpdateStates()
					#print Cells[0, 0].state
		
		x = 0
		y = 0
		for y in range(0, (400 / 10)):
			for x in range(0, (400 / 10)):
				Cells[x, y].Draw(screen)

		CursRect.Draw(screen)
		pygame.display.flip()

if __name__ == '__main__': main()[/PHP]

---

### Post by nvteighen on 2009-09-29
It's really good.

The thing is that you could eliminate that Cells dictionary from global namespace. Create it at main and pass it around.

Then, the getState method is completely redundant, as you can more easily access the cell's state by using cell.state.

There might be a weird interface issue there too, but I'm not sure what it lies on... I mean, the UpdateNeighs and UpdateStates functions are a bit weird to me at first sight... My intuition leads me to try to rewrite that into a method and to take away anything related to interface from them (that print statement in UpdateStates) by making them return something the interface code can understand.

But besides that, it's pretty cool :)

---

### Post by Mousie_kebabs on 2009-09-29
Thanks :)

I will keep the globalNamespace of Cells in mind, that was part of a quick complete rewrite of the program when I changed from a list to a dictionary.

The UpdateNeigh and UpdateState functions were the only way I could think of looping through each cell, I originally just had a list of cells and used something like,

[PHP]for cell in Cells
     for cell2 in Cells[/PHP]

But this caused the whole program to lock up while it was updating each cell, so I went about it a different way.

How would you go about looping through a large amount of classes?

---

### Post by nvteighen on 2009-09-29
> **Mousie_kebabs said:**
> Thanks :)

The UpdateNeigh and UpdateState functions were the only way I could think of looping through each cell, I originally just had a list of cells and used something like,

[PHP]for cell in Cells
     for cell2 in Cells[/PHP]

But this caused the whole program to lock up while it was updating each cell, so I went about it a different way.

How would you go about looping through a large amount of classes?

I'm not sure... I've got a weird idea that might/might not work... Let me work on it a bit and I'll tell you. :P

Something you should work about too is the usage of "magic numbers"... Specially those "400/10" you use in xrange()... I guess you can transform that into a general formula by taking the window's size. Try always to code as most generalwise as possible.

Of course, magic numbers like (255, 255, 255), which have a clear meaning (#FFFFFF) can stay there :)

Another thing is that you're mixing implementation and interface at drawGrid... You better not create the cells while drawing them... create them first and then draw them independently. Imagine it this way: You create a library, a set of functions used to create Conway's Life game... a sort of "language" that you can use at Python's shell independently. Then, the (G)UI should act as a user typing at the shell. That's called the Model-View-Controller design... The Controller part in this care are under pygame's procedures to update screen and to poll events, so don't worry.

---

### Post by A_Fiachra on 2009-09-29
> **nvteighen said:**
> 

...

Of course, magic numbers like (255, 255, 255), which have a clear meaning (#FFFFFF) can stay there :)

..


Would that count as a black magic number?

( oh my sides!)

---

