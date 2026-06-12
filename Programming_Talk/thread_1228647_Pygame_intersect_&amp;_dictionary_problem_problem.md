---
title: "Pygame intersect &amp; dictionary problem problem"
date: 2009-08-01
forum: Programming Talk
---

### Post by matmatmat on 2009-08-01
I have this code:
```

import pygame
from pygame.locals import *
from sys import exit
from random import randint
from sys import argv
from gameobjects.vector2 import Vector2


def Intersect(s1_x, s1_y, s2_x, s2_y, image):
        if (s1_x > s2_x - image.get_width()):
		if(s1_x < s2_x + image.get_width()):	
			if(s1_y > s2_y - image.get_height()):
				if(s1_y < s2_y + image.get_height()):
                			return 1
	return 0

def doMenu(question, options, retur=False):
	font = pygame.font.SysFont("arial", 20)
	while True:		 
		text = font.render(question, True, (0,0,0))
		screen.fill((255,255,255))
		screen.blit(text, (10,10))
		i = 50
		for t in options:
			text = font.render(t, True, (0,0,0))
			screen.blit(text, (30,i))
			i += 50
		for event in pygame.event.get():
	    		if event.type == QUIT:
            			print score
				exit()
			if event.type == KEYDOWN:
				if event.key == K_1:
					return 1
				if event.key == K_2:
					return 2
				if event.key == K_3:
					return 3
				if event.key == K_4:
					return 4
				if event.key == K_5:
					return 5
				if event.key == K_6:
					return 6
				if retur:
					return
													
		pygame.display.update()

class map1:
	def __init__(self):
		self.d = {"tavern" : tavern(Tavern, Vector2(1,1), "You are in the tavern, what do you want to do?", ["1 - Buy beer", "2 - Rob a drinker", "3 - exit"]),"loanshark" : loanshark(Loanshark, Vector2(600 - Loanshark.get_width(),1), "You are in the loan shark's office, what do you want to do? ", ["(You have to pay back double on loans)","1 - Borrow 100", "2 - Borrow 250", "3 - Borrow 500", "4 - Borrow 1000", "5 - Borrow 10000", "6 - Rob the shark", "7 - Exit"])}
		self.back = pygame.image.load("data/map1.png")
		self.name = "map1"

class map2:
	def __init__(self):
		self.d = {"shop" : shop(Shop, Vector2(173,371), "You are in the shop, what do you want to do?",[]), "shipyard" : shipyard(Shipy, Vector2(232, 87), "You are in the shipyard, what do you want to do?", [])}
		self.back = pygame.image.load("data/map2.png")
		self.name = "map2"

class place:
	def __init__(self, image, pos, q, o):
		self.image = image
		self.pos = pos
		self.q = q
		self.o = o
	def blit(self, screen):
		screen.blit(self.image, (self.pos.x, self.pos.y))	

class tavern(place):
	def __init__(self, image, pos, q, o):
		place.__init__(self,image, pos, q, o)
		self.limit = randint(120, 480)
		self.last_rob = self.limit
	def check(self, position, heading, score):
		self.last_rob += 0.33
		if self.last_rob < self.limit:
			m = doMenu("Hey, you were here when my mate mick was robbed", ["You run away before he calls for guards", "Press any key"], True)
			position.x = 10 + self.image.get_width()
			heading = Vector2()
			return position, heading, score	
		m = doMenu(d.q, d.o)
		position.x = 10 + self.image.get_width()
		heading = Vector2()
		if m == 1:
			score -= 10	
		if m == 2:
			rand = randint(1,200)
			if rand % 5 == 0:
				rand = randint(1, 200)
				score += rand
				xxx = doMenu("You got: $" + str(rand), ["Press any key"], True)
				self.last_rob = 0
			elif rand == 1:
				xxx = doMenu("You were caught! You bribe the soldiers with $100", ["Press any key"], True)
				score -= 100
			else:
				xxx = doMenu("You didn't rob anyone, but you got away", ["Press any key"], True)
		return position, heading, score	

class shop(place):
	def __init__(self, image, pos, q, o):
		place.__init__(self,image, pos, q, o)
		self.limit = randint(120, 480)
		self.last_rob = self.limit
		self.items = {"silk" : 10, "wood" : 5, "gold" : 100, "chocolate" : 15}
		self.keys = ["silk", "wood", "gold", "chocolate"]
		self.pair = [10,5,100,15]
		self.reversed = {10 : "silk", 5 : "wood", 100 : "gold", 15 : "chocolate"}
		self.o = []
		i = 1
		for key, d in self.items.iteritems():
			self.o.append("%i - Buy %s at $%s" % (i, key, d))
			i += 1
		self.o.append("%i - Rob the shop keeper" % (i))
		self.o.append("%i - Exit" % (i + 1))
	def check(self, position, heading, score):
		self.last_rob += 0.33
		if self.last_rob < self.limit:
			m = doMenu("Hey, you robbed me", ["You run away before he calls for guards", "Press any key"], True)
			position.x = self.pos.x + 5 + self.image.get_width()
			heading = Vector2()
			return position, heading, score	
		m = doMenu(d.q, d.o)
		position.x = self.pos.x + 5 + self.image.get_width()
		heading = Vector2() 
		for i in self.keys:
			try:
				if i == self.reversed[self.pair[m - 1]]:
					if score - self.items[self.keys[m - 1]] < 0:
						m = doMenu("You don't have enough money for that!", ["Press any key"], True)
						print self.items[self.keys[m - 1]]
					else:
						score -= self.items[self.keys[m - 1]]
			except:
				pass
		l = len(self.keys)			
		if m == l + 1:
			rand = randint(1,200)
			if rand % 5 == 0:
				rand = randint(200, 1000)
				score += rand
				xxx = doMenu("You got: $" + str(rand), ["Press any key"], True)
				self.last_rob = 0
			elif rand == 1:
				xxx = doMenu("You were caught! You bribe the soldiers with $100", ["Press any key"], True)
				score -= 100
			else:
				xxx = doMenu("You didn't rob anyone, but you got away", ["Press any key"], True)						

		return position, heading, score

class shipyard(place):
	def __init__(self, image, pos, q, o):
		place.__init__(self,image, pos, q, o)
		self.limit = randint(120, 480)
		self.last_rob = self.limit
		self.items = {"rowing boat" : 150, "sloon" : 1400, "merchant ship" : 3650, "galleon" : 40000}
		self.keys = ["rowing boat", "sloon", "merchant ship", "galleon"]
		self.pair = [1400,150,3650,40000]
		self.reversed = {150 : "rowing boat", 1400 : "sloon", 3650 : "merchant ship", 40000 : "galleon"}
		print self.keys
		self.o = []
		i = 1
		for key, d in self.items.iteritems():
			self.o.append("%i - Buy %s at $%s" % (i, key, d))
			i += 1
		self.o.append("%i - Rob the ship builder" % (i))
		self.o.append("%i - Exit" % (i + 1))
		print self.o
		print self.items
	def check(self, position, heading, score):
		self.last_rob += 0.33
		if self.last_rob < self.limit:
			m = doMenu("Hey, you robbed me", ["You run away before he calls for guards", "Press any key"], True)
			position.x = self.pos.x + 5 + self.image.get_width()
			heading = Vector2()
			return position, heading, score	
		m = doMenu(d.q, d.o)
		position.x = self.pos.x + 5 + self.image.get_width()
		heading = Vector2() 
		for i in self.keys:
			try:
				if i == self.reversed[self.pair[m - 1]]:
					print self.items[self.keys[m - 1]]
					if score - self.items[self.keys[m - 1]] < 0:
						m = doMenu("You don't have enough money for that!", ["Press any key"], True)
					else:
						score -= self.items[self.keys[m - 1]]
			except:
				pass
		l = len(self.keys)			
		if m == l + 1:
			rand = randint(1,200)
			if rand % 5 == 0:
				rand = randint(200, 1000)
				score += rand
				xxx = doMenu("You got: $" + str(rand), ["Press any key"], True)
				self.last_rob = 0
			elif rand == 1:
				xxx = doMenu("You were caught! You bribe the soldiers with $100", ["Press any key"], True)
				score -= 100
			else:
				xxx = doMenu("You didn't rob anyone, but you got away", ["Press any key"], True)						

		return position, heading, score
				

class loanshark(place):
	def __init__(self, image, pos, q, o):
		place.__init__(self,pygame.image.load("data/loan.png"), pos, q, o)
		self.owed = 0
		self.limit = randint(120, 480)
		self.last_rob = self.limit

	def check(self, position, heading, score):
		self.last_rob += 0.33
		if self.last_rob < self.limit:
			m = doMenu("Hey, you robbed me", ["You run away before he calls for guards", "Press any key"], True)
			position.x = 10 + self.image.get_width()
			heading = Vector2()
			return position, heading, score	
		if self.owed == 0:
			m = doMenu(d.q, d.o)
			if m == 1:
				score += 100
				self.owed = 100
			if m == 2:
				score += 250
				self.owed = 250
			if m == 3:
				score += 500
				self.owed = 500
			if m == 4:
				score += 1000
				self.owed = 1000
			if m == 5:
				score += 10000
				self.owed = 10000
			if m == 6:
				rand = randint(1,200)
				if rand == 1:
					rand = randint(20000, 100000)
					score += rand
					xxx = doMenu("You got: $" + str(rand), ["Press any key"], True)
					self.last_rob = 0
				elif rand % 5 == 0:
					xxx = doMenu("You were caught! You bribe the soldiers with $" + str((score/100)*33), ["Press any key"], True)
					score -= (score/100)*33
				else:
					xxx = doMenu("You didn't rob anyone, but you got away", ["Press any key"], True)

		else:
			m = doMenu(d.q, ["1 - Pay money back", "2 - Rob the shark", "3 - Exit"])
			if m == 1:
				score -= self.owed * 2
				self.owed = 0
			if m == 2:
				rand = randint(1,200)
				if rand == 1:
					rand = randint(20000, 100000)
					score += rand
					xxx = doMenu("You got: $" + str(rand), ["Press any key"], True)
					self.last_rob = 0
				elif rand % 5 == 0:
					xxx = doMenu("You were caught! You bribe the soldiers with $" + str((score/100)*33), ["Press any key"], True)
					score -= (score/100)*33
				else:
					xxx = doMenu("You didn't rob anyone, but you got away", ["Press any key"], True)
		position.x = 575 - self.image.get_width()
		heading = Vector2()	
		return position, heading, score	
		
				

screen = pygame.display.set_mode((600,480), 0, 32)
pygame.init()
back = pygame.image.load("data/map1.png")
me = pygame.image.load("data/me.png")
Tavern = pygame.image.load("data/tavern.png")
Loanshark = pygame.image.load("data/loan.png")
Shop = pygame.image.load("data/shop.png")
Shipy = pygame.image.load("data/shipy.png")
clock = pygame.time.Clock()
score = 1000
x = 10
y = screen.get_height()/2 - me.get_height()
distance_moved = 0
speed = 100.
position = Vector2(400.0, 400.0)
heading = Vector2()
destination = Vector2()
left = False
top = False
map = map1()
while True:
	time_passed = clock.tick(30) / 1000.0
	screen.blit(map.back, (0,0))
	for event in pygame.event.get():
	    	if event.type == QUIT:
            		print score
			exit()
		if event.type == MOUSEBUTTONDOWN:
			destination = Vector2(*event.pos) - Vector2(*me.get_size())/2.
			heading = Vector2.from_points(position, destination)
			heading.normalize()
	
	heading2 = Vector2.from_points(position, destination)
	heading.normalize()
	if position.x < screen.get_width()/2:
		left = True
	if position.y < screen.get_height()/2:
		top = True
	if heading.x != 0 and heading.x != 0:
		if heading.x < 0:
			if heading.y < 0:
				if heading2.x > 0 and heading2.y > 0 :
					heading = Vector2()	
			else:
				if heading2.x > 0 and heading2.y < 0:
					heading = Vector2()	
		else:
			if heading.y < 0:
				if heading2.x < 0 and heading2.y > 0 :
					heading = Vector2()	
			else:
				if heading2.x < 0 and heading2.y < 0:
					heading = Vector2()	
	distance_moved = time_passed * speed
	position += heading * distance_moved
	screen.blit(me, (position))
	if map.name == "map1" and position.x <= 0:
		map = map2()
		position.x = 598 - me.get_width()
		heading = Vector2()
	if map.name == "map2" and position.x + me.get_width() >= 600:
		map = map1()
		position.x = 0 + me.get_width()
		heading = Vector2()
	for key, d in map.d.iteritems():
		d.blit(screen)
		if d.pos.x > screen.get_width()/2:
			i = Intersect(position.x, position.y, 600, d.pos.y, d.image)
		else:
			i = Intersect(position.x, position.y, d.pos.x, d.pos.y, d.image)
		if i == 1:
			position, heading, score = d.check(position, heading, score)					
	pygame.display.update()

```
when run the intersect doesn't always work and when entering the building marked "sy" on map2 and you try to buy a rowing boat it says you don't have enough money because the dictionary seams to be mixed up?

---

### Post by smartbei on 2009-08-01
I try to run the code, but I get:
```

Traceback (most recent call last):
  File "ahoy.py", line 6, in <module>
    from gameobjects.vector2 import Vector2
ImportError: No module named gameobjects.vector2

```
Could you include that in the tarfile?

Also, I find that checking if a variable is between two values on one line is usually much clearer:
```

def Intersect(s1_x, s1_y, s2_x, s2_y, image):
    if (s2_x - image.get_width()) < s1_x < (s2_x + image.get_width()):
        if (s2_y - image.get_height()) < s1_y < (s2_y + image.get_height()):
            return True
    return False

```
Lastly, in your code you mix tabs and spaces. Python Best Practice is 4 spaces per indentation level - If others look at and edit your code it is a good idea to have it consistent. Your editor should support this setting (idle does by default).

---

### Post by matmatmat on 2009-08-01
[http://code.google.com/p/gameobjects/]("http://code.google.com/p/gameobjects/")

---

### Post by smartbei on 2009-08-01
Ok - I found the rowing boat bug - you have the 'keys' list in the wrong order. However, I think there is a better way for storing the data. How about a list of tuples:
```

self.items = [("rowing boat", 150), ("sloon", 1400), ("merchant ship", 3650), ("galleon", 40000)]

```
And here are the changes propogated over the shipyard class:
```

class shipyard(place):
    def __init__(self, image, pos, q, o):
        place.__init__(self,image, pos, q, o)
        self.limit = randint(120, 480)
        self.last_rob = self.limit
        self.items = [("rowing boat", 150), ("sloon", 1400), ("merchant ship", 3650), ("galleon", 40000)]
        self.o = []
        i = 1
        for name, price in self.items:
            self.o.append("%i - Buy %s at $%d" % (i, name, price))
            i += 1
        self.o.append("%i - Rob the ship builder" % (i))
        self.o.append("%i - Exit" % (i + 1))
        print self.o
        print self.items
    def check(self, position, heading, score):
        self.last_rob += 0.33
        if self.last_rob < self.limit:
            m = doMenu("Hey, you robbed me", ["You run away before he calls for guards", "Press any key"], True)
            position.x = self.pos.x + 5 + self.image.get_width()
            heading = Vector2()
            return position, heading, score
        m = doMenu(d.q, d.o)
        position.x = self.pos.x + 5 + self.image.get_width()
        heading = Vector2()
        if 1 <= i < len(self.items) + 1:
            if self.items[m-1][1] > score:
                m = doMenu("You don't have enough money for that!", ["Press any key"], True)
            else:
                score -= self.items[m - 1][1]
        
        if m == len(self.items) + 1:
            rand = randint(1,200)
            if rand % 5 == 0:
                rand = randint(200, 1000)
                score += rand
                xxx = doMenu("You got: $" + str(rand), ["Press any key"], True)
                self.last_rob = 0
            elif rand == 1:
                xxx = doMenu("You were caught! You bribe the soldiers with $100", ["Press any key"], True)
                score -= 100
            else:
                xxx = doMenu("You didn't rob anyone, but you got away", ["Press any key"], True)                        

        return position, heading, score

```

I hope that helps.

several other things I noticed (general tips):
[list]
[*] You can use elif (else-if):
```

a = 4
if a == 3:
    print 'aaa'
elif a == 4:
    print 'aaaa'
elif a == 5:
    print 'aaaaa'
else:
    print "oh comon..."

```
[*] Robbing the shop looks like it has the same behavior in every building... maybe that could be in the 'place' class that you inherit from?
[/list]

---

### Post by matmatmat on 2009-08-01
Thanks, but the intersect doesn't seem to be working all the time

---

### Post by smartbei on 2009-08-01
Yes, I didn't get to that one yet...

Anyway, had another look at it and I think I found the problem. You don't need to subtract the image height or width when doing intersection checking, because you are comparing the top left corners of the objects. Therefore, if you use this as your Intersect function:
```

def Intersect(s1_x, s1_y, s2_x, s2_y, image):
    if s2_x < s1_x < (s2_x + image.get_width()):
        if s2_y < s1_y < (s2_y + image.get_height()):
            return True
    return False

```
It works. The bug it fixes is on map2 where you walk above the shop and it still enters the shop.

Note that intersections occur only when the top-left corner of the player is inside the building. If you want intersections to occur whenever any part of the player is inside the building, you will need to take the player's size into account.

Good job with the game by the way - I can really see improvement compared to the games you posted some days ago (Breakout, etc.).

---

### Post by matmatmat on 2009-08-01
Thanks!

---

### Post by matmatmat on 2009-08-01
How would I check if the player is on the "sea" (blue bit)?

---

### Post by matmatmat on 2009-08-04
Anyone

---

