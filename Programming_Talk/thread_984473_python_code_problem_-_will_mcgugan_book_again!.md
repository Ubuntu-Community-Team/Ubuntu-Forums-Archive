---
title: "python code problem - will mcgugan book again!"
date: 2008-11-16
forum: Programming Talk
---

### Post by farrell2k on 2008-11-16
Hi, guys.  I am a complete newb to python.  I have a it of exp with java that does help, but I am lost on something.  I am working on the tank game project in will mcgugan's book, and I am being stopped by an error and I don't understand why.  I am getting: 

tanks = { "a":Tank("Alice"), "b":Tank("Bob"), "c":Tank("Carol") }
python typeError: this constructor takes no arguments, when python tries to create this dictionary with these keys.

Is it something completely noobish I am just not getting?

Here are my two files.

```


class Tank:
	def _init_(self, name):
		self.name = name
		self.alive = true
		aelf.armor = 60
		self. ammo = 5

	def _str_(self):
		if self.alive:
			return "%s (%i armor, %i shells)" % (self.name, self.armor, self.ammo)

	def fire_at(self, enemy):
		if self.ammo >=1:
			self.ammo -=1
			print self.name, " fires on", enemy.name
			enemy.hit()
		else:
			print self.name, " has no shells"
	
	def hit(self):
		self.armor -=20
		print self.name, " is hit."
		if self.armor <=0:
			self.explode()
	
	def explode(self):
		self.alive = false
		print self.name, " explodes."


```

```

from tank import Tank

tanks = { "a":Tank("Alice"), "b":Tank("Bob"), "c":Tank("Carol") }
alive_tanks = len(tanks)

while alive_tanks > 1:
	
	for tank_name in sorted( tanks.keys() ):
		print tank_name, tanks[tank_name]
		
	first = raw_input("Who fires? ").lower()
	second = raw_input("at whom? ").lower()
	
	try:
		first_tank = tanks[first]
		second_tank = tanks[second]
	except KeyError, name:
		print "no such tank. ", name
		continue
	
	if not first_tank.alive or not second_tank.alive:
		print "One of those tanks is dead."
		continue
	
	print 
	print "*" * 30

	first_tank.fire_at(second_tank)
	if not second_tank.alive:
		alive_tanks -=1
	
	print "*" * 30
	
for tank in tanks.values():
	if tank.alive:
		print tank.name, "is the winner."
		break

```

---

### Post by chronographer on 2008-11-16
More info on the error message would be good, what line does it point to?

Ok i ran it, you need 2 __ in your init function! that is two underscored either side:

---

### Post by chronographer on 2008-11-16
```
class Tank:
	def __init__(self, name):
		self.name = name
		self.alive = 1
		self.armor = 60
		self. ammo = 5

	def _str_(self):
		if self.alive:
			return "%s (%i armor, %i shells)" % (self.name, self.armor, self.ammo)

	def fire_at(self, enemy):
		if self.ammo >=1:
			self.ammo -=1
			print self.name, " fires on", enemy.name
			enemy.hit()
		else:
			print self.name, " has no shells"
	
	def hit(self):
		self.armor -=20
		print self.name, " is hit."
		if self.armor <=0:
			self.explode()
	
	def explode(self):
		self.alive = 0
		print self.name, " explodes."
```

```
from tank import Tank

tanks = { "a":Tank("Alice"), "b":Tank("Bob"), "c":Tank("Carol") }
alive_tanks = len(tanks)

while alive_tanks > 1:
	
	for tank_name in sorted( tanks.keys() ):
		print tank_name ,":", tanks[tank_name].name
		
	first = raw_input("Who fires? ").lower()
	second = raw_input("at whom? ").lower()
	
	try:
		first_tank = tanks[first]
		second_tank = tanks[second]
	except KeyError, name:
		print "no such tank. ", name
		continue
	
	if not first_tank.alive or not second_tank.alive:
		print "One of those tanks is dead."
		continue
	
	print 
	print "*" * 30

	first_tank.fire_at(second_tank)
	if not second_tank.alive:
		alive_tanks -=1
	
	print "*" * 30
	
for tank in tanks.values():
	if tank.alive:
		print tank.name, "is the winner."
		break
```

---

### Post by farrell2k on 2008-11-16
Thanks.  I should have seen that.   It opened up 2 more errors that I was able to correct.   Thanks again!

---

