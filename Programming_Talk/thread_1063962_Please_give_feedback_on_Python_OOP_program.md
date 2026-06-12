---
title: "Please give feedback on Python OOP program"
date: 2009-02-08
forum: Programming Talk
---

### Post by fiddler616 on 2009-02-08
Hello,

A few days ago, I asked where I should go with my programming. There was an overwhelming response to learn OOP, and jimi_hendrix kindly provided the following challenge:
> 
make a snowball fight game, using inheritance/polymorphism

the player faces an AI (i dont care if you use randoms or what to decide his moves)

you each have 5 health and snowballs must be made (you start with 3)

you can both move forward and back, and hit rate of snowballs depends on range

It's still under development(read: it's a little rough around the edges, and doesn't support moving or variable success rates based on position, and you forfeit your turn if you try to throw a snowball you don't own). I've also heard that global variables are frowned upon. But I'd be interested in what people have to say about the actual object-orientedness of it.

Note: I'm not quite sure where I'm going with the Stats superclass. I suppose it would've been more helpful if I'd made a separate AI class, but currently everything it does could've been done within the Snowballer class. I haven't removed it because it works, and I'm loathe to break working code with no other reason than "It reads nicer". And who knows, maybe I'll need it in the future.
[PHP]
version = .002
#With inheritance

import sys
class Stats:
	def __init__(self, health, ammo):
		self.health = health
		self.ammo = ammo
	def build(self):
		self.ammo += 1
class Snowballer(Stats):
	def __init__(self, health, ammo, name):
		Stats.__init__(self, health, ammo)
		self.name = name
	def printStats(self):
		'''Says how much health the player has'''
		print "%s has %s health, and %s snowballs" %(self.name, self.health, self.ammo)
	def throw(self, opponent):
		'''Throws a snowball at a given opponent, lowering the oponent's health and the throwers ammo.'''
		self.ammo -= 1
		opponent.health -= 1
		print "%s's enemy hit!"%self.name
	def build(self):
		print "Building a snowball..."
		Stats.build(self)
	def checkLife(self):
		ok = True
		if self.health == 0:
			print "%s has been killed!"%self.name
			ok = False
		return ok
	def checkAmmo(self):
		ok = True
		if self.ammo == 0:
			print "%s has no more snowballs!"%self.name
			ok = False
		return ok
#Initialize players:
AI_Player = Snowballer(5, 3, "AI")
player1 = Snowballer(5, 3, "Player 1")

#Prompt user
print "Snowballing version %s\n"%version
def check():
	global p1Ammo; p1Ammo = player1.checkAmmo()
	global AIAmmo; AIAmmo = AI_Player.checkAmmo()
	global p1HitPoints; p1HitPoints = player1.checkLife()
	global AIHitPoints; AIHitPoints = AI_Player.checkLife()
	if p1HitPoints:
		player1.printStats()
	if AIHitPoints:
		AI_Player.printStats()
	if not p1HitPoints:
		print "%s wins!"%AI_Player.name
		sys.exit()
	if not AIHitPoints:
		print "%s wins!"%player1.name
		sys.exit()
while True:
	check()
	print "Press 1 to make a snowball, 2 to throw one, 3 to move, and 4 to exit."
	success = False
	while not success:
		success = True
		#Player's turn:
		userInput = int(raw_input("=>"))
		if userInput == 1:
			player1.build()
		elif userInput == 2:
			if p1Ammo:
				player1.throw(AI_Player)
			else:
				print "You don't have any snowballs!"
		elif userInput == 3:
			print "Moving is not yet supported"
		elif userInput == 4:
			sys.exit()
		else:
			print "Invalid input. Try again."
			success = False
		#AI's turn:
		check()
		print "\nAI's turn:"
		if AIAmmo:
			AI_Player.throw(player1)
		else:
			AI_Player.build()	[/PHP]

---

### Post by Taidgh on 2009-02-08
I looked at that thread, and had an attempt myself. 
```

#!/usr/bin/env python

import random

class Player:
	def __init__(self, lives, balls):
		self.lives = lives
		self.balls = balls
	def throw(self, oppon):
		if random.random() > 0.5:
			self.lives -= 1
			print "You were hit!"
		else:
			print "You hit the other player!"
			oppon.lives -= 1
	def hide(self):
		if random.random() > 0.5:
			print "You were hit!"
			self.lives -= 1
		else:
			print "The other player missed!"
play = raw_input("Would you like to play a snowball game against the computer?")
play = play.lower()
if play == "y" or play == "yes":
	play = 1
	user = Player(3,10)
	comp = Player(3,10)
else:
	print "Goodbye."
while play == 1:
	choice = raw_input("Would you like to (T)hrow or (H)ide? [LIVES: %d]" %(user.lives))
	choice = choice.lower()
	if choice == "t":
		user.throw(comp)
	else:
		user.hide()
	if user.lives <= 0:
		print "You lose!"
		play = 0
	elif comp.lives <= 0:
		print "You win!"
		play = 0

```
But as you can see, I didn't get very far. I'm afraid I couldn't really critique your one, as I am an uber-noob.

---

### Post by nvteighen on 2009-02-08
@fiddler616: Those global variables are innecessary. You can get rid of them very easily. The sys.exit() is a bit unclean, as it raises an exception. It's really much better to put the whole main procedure into a function (call it main(), as you would do in C) and then make the script call main() at start. And then you can replace sys.exit() by a simple return statement.

@Taidgh: Good... now try to make the AI to be another player, as fiddler616 did.

---

### Post by fiddler616 on 2009-02-08
> **nvteighen said:**
> @fiddler616: Those global variables are innecessary. You can get rid of them very easily. The sys.exit() is a bit unclean, as it raises an exception. It's really much better to put the whole main procedure into a function (call it main(), as you would do in C) and then make the script call main() at start. And then you can replace sys.exit() by a simple return statement.
I feel like I tried it without the globals first, and it didn't work, though maybe that stemmed from a different error. I'll try it again, but once I've slept--I've had a long day, and I don't trust myself in front of my precious source code.
Good call on main(). I'll do that tomorrow too.
Also, for lack of a button: *thanks* :)

---

### Post by wmcbrine on 2009-02-08
Not that you shouldn't learn it, or won't use it, but the whole class inheritance thing is less needed in Python than in, say, C++. In Python, you can have polymorphism without inheritance.

Anyway, YES, break (then fix) working code for no other reason than "it reads nicer". Do this constantly. Don't leave useless code hanging around. That's my advice: Always Be Refactoring.

Speaking of reading nicer, I'd suggest a blank line after each function, and perhaps two after a class. You might want to read [PEP 8](http://www.python.org/dev/peps/pep-0008/) for more on this sort of detail.

Reducing the need for global variables is... I don't want to overstate this, but... kind of the whole point of OOP. So yeah, you might want to see if you can rework those.

Or not. Sometimes, against all odds, global variables are the most elegant way to do something. Go for elegance first, last and always. (Notice I'm not saying anything about whether that's the case here... I haven't really examined it.)

---

### Post by nvteighen on 2009-02-09
> **wmcbrine said:**
> N
Reducing the need for global variables is... I don't want to overstate this, but... kind of the whole point of OOP. So yeah, you might want to see if you can rework those.

Or not. Sometimes, against all odds, global variables are the most elegant way to do something. Go for elegance first, last and always. (Notice I'm not saying anything about whether that's the case here... I haven't really examined it.)

+1. And +2 for elegance :)

Globals are great for application meta-data that don't interfere with the program's normal working. For example, in C you sometimes use a global that's used to save error codes, but that's not data the program uses, but data that refers to the program itself... It's a different layer of information.

But generally, OOP doesn't need globals.

---

### Post by Quikee on 2009-02-10
```
#Initialize players:
AI_Player = Snowballer(5, 3, "AI")
player1 = Snowballer(5, 3, "Player 1")

#Prompt user
print "Snowballing version %sn"%version
def check():
    global p1Ammo; p1Ammo = player1.checkAmmo()
    global AIAmmo; AIAmmo = AI_Player.checkAmmo()
    global p1HitPoints; p1HitPoints = player1.checkLife()
    global AIHitPoints; AIHitPoints = AI_Player.checkLife()
    if p1HitPoints:
        player1.printStats()
    if AIHitPoints:
        AI_Player.printStats()
    if not p1HitPoints:
        print "%s wins!"%AI_Player.name
        sys.exit()
    if not AIHitPoints:
        print "%s wins!"%player1.name
        sys.exit()
while True:
    check()
    print "Press 1 to make a snowball, 2 to throw one, 3 to move, and 4 to exit."
    success = False
    while not success:
        success = True
        #Player's turn:
        userInput = int(raw_input("=>"))
        if userInput == 1:
            player1.build()
        elif userInput == 2:
            if p1Ammo:
                player1.throw(AI_Player)
            else:
                print "You don't have any snowballs!"
        elif userInput == 3:
            print "Moving is not yet supported"
        elif userInput == 4:
            sys.exit()
        else:
            print "Invalid input. Try again."
            success = False
        #AI's turn:
        check()
        print "\nAI's turn:"
        if AIAmmo:
            AI_Player.throw(player1)
        else:
            AI_Player.build()  

```

Make this part also as object(s) in that way that a mud throwing competition can be derived out from it. ;) 

Also you could do it even more interesting if you would do it like:
"Person with name which is a Player with health which is a SnowBaller that has a Bag that can hold snowballs..."

Where are the unit tests? :P

Forget globals. In all my time writing OO programs I never needed them (C is another story) unless I wanted to create something quick and dirty.

---

