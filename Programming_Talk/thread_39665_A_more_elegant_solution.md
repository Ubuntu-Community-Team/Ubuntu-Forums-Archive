---
title: "A more elegant solution?"
date: 2005-06-06
forum: Programming Talk
---

### Post by darthsabbath on 2005-06-06
Hey all, I've been learning Python over the last few weeks, and I think I've come a good ways.  I've managed a few small, working programs, like the one below.  However, despite the fact that they work, they just don't seem... elegant.  I was basically just looking for some advice on making the code more efficient.

Any help would be greatly appreciated. :D

Thanks,
Phil  

```

#!/usr/bin/python
#  
# RSP.PY - A rock, paper, scissors game
# By Phil Moore
#
# TODO: For some reason, this looks ugly... look into making this a little more elegant. Also
# planning on adding a strategy for the computer, keeping track of a player's last 100 moves, 
# and looking for patterns... maybe when I'm a little more advanced. ;-)

import sys, string, random

# Constant value for winning throws, i.e., Rock beats Scissors, etc.
wins = {"r":"s", "s":"p", "p":"r"}

# Maps the simple character to the throw
throws = {"r":"Rock", "s":"String", "p":"Paper"}

# Just some insults the CPU throws out when it wins.
insults = ["Your mother smelt of elderberries!", \
	   "You got pwnzed!", \
	   "WOO HOO!  I r00l, u dr00l!", \
	   "What's that smell?  Smells like fear!", \
	   "PH34R MY 0WNZ4G3~!!!!111", \
	   "I am so great! I am so great! Everybody loves me 'cuz I am so great!"]

def victor(x, y, z):
	# Compares the throws of the player and the computer to WINNINGITEMS.  If the Player wins, return
	# True, if the CPU wins, return False.  Otherwise, we push.
	if (x, y) in z.iteritems():
		return True
	elif (y, x) in z.iteritems():
		return False
	else:
		return

def quitGame():
	# Just a little function to see if the player wants to continue the game.  Default is to 
	# play again
	quit = raw_input("Play again? (Y/n): ")
	while True:
		try:
			if quit in ("y", "Y"):
				rsp(player)
			elif quit in ("n", "N"):
				print "\nGoodbye!"
				sys.exit()
			else:
				rsp(player)
			break
		except ValueError: 
			print "\nInvalid input!"

def gameOver(x, y, z):
	# Simple function to determine if the game is over, i.e., does one player have the
	# required score for victory?
	if x == z:
		print "%s wins the game!\n\nCongratulations!!!" % player
		quitGame()
	elif y == z:		
		print "The Computer wins the game! \n\n%s" % (insults[random.randint(0, (len(insults)-1))])
		quitGame()

def rsp(player):
		# Initialize all the variables
		(cpuscore, playerscore, wincount) = (0, 0, 0)
		
		while True:
			try:
				wincount = int(raw_input("How many points to win? "))
				break
			except ValueError:
				print "\nInvalid input!"
		while gameOver(playerscore, cpuscore, wincount) != True:
			while True: 
				try:
					playerthrow = string.lower(raw_input("(R)ock, (P)aper, or (S)cissors? (R/S/P): "))
					if (playerthrow in wins.keys()) == False:
						print "Invalid Input: Please choose R, S, or P!"
					else:
						break
				except ValueError:	
					print "\nInvalid Input! Please choose R, S, or P!"
			# Get a random throw from the CPU
			cputhrow = wins.keys()[random.randint(0, 2)]
			print "%s: %s\tCPU: %s" % (player, throws[playerthrow], throws[cputhrow])
			if victor(playerthrow, cputhrow, wins) == True:
				playerscore = playerscore + 1
				print "\n%s wins this round! \n%s: %d\tCPU: %d" % (player, player, playerscore, cpuscore)
			elif victor(playerthrow, cputhrow, wins) == False:
				cpuscore = cpuscore + 1
				print "\nThe CPU wins this round! \n%s: %d\tCPU: %d \n%s" % (player, playerscore, cpuscore, insults[random.randint(0, (len(insults) - 1))])
			else:
				print "\nPush!"
		quitGame()	

while True:
	try: 
		player = raw_input("**** ROCK * PAPER * SCISSORS **** \n\nPress Ctrl-D to Quit \n\nPlease enter your name: ")
		rsp(player)
	except (KeyboardInterrupt, EOFError):
		print "\nGoodbye!"
		sys.exit()

```

---

### Post by thumper on 2005-06-06
Instead of just giving you a rewritten module, I'll try to give more constructive generalities...

Instead of calling the same function multiple times with the same params and testing result, call once, and store result in a variable, then test the variable:
```
result = victor(playerthrow, cputhrow, wins)
if result == ...:
```

Part of the issue comes to how you are thinking about the problem.  How about instead of just having a **wins** structure, how about a result structure
```
result = { ('r','p') : 'Loose', ('r','r') : 'Draw', ('r','s') : 'Win', ...}
``` I think you can see where that is going.  This makes the victor function trivial.

Speaking of victor, you are passing in a global stucture (wins) into the function every time as the last parameter.  If the parameter never changes, then it is not really a parameter and you can just access the package global from inside the function.

Generally if you have a function that returns a boolean value, you test it like this:
```
def func():
   return some_bool_value

if func():
   # this is true

if not func():
   # this is false
``` This might be slightly controversial as some people to prefer explicit tests for bools, but I'm not one of them.

Python does have the += operator
```
>>> x = 1
>>> x += 1
>>> x
2

```

See how you go with these.
Tim

---

### Post by darthsabbath on 2005-06-06
[QUOTE=thumper]Instead of just giving you a rewritten module, I'll try to give more constructive generalities...
[/QUOTE]

Well, that's what I was wanting, just a general "push" in the right direction rather than someone saying "Okay, you wrote this, you should've written it like this" and rewriting it completely. I'll definitely play around with your suggestions... I've found another bug I've got to work out as well. :D 

Thanks,
Phil

---

### Post by jerome bettis on 2005-06-06
does python have the ternary operator ? yes : no

if it does there's several places where you could squeeze that in to clean the code up.  it wouldn't make your solution any more elegant i guess, but it's nice to say a lot and type less.

---

### Post by thumper on 2005-06-06
[QUOTE=jerome bettis]does python have the ternary operator ? yes : no

if it does there's several places where you could squeeze that in to clean the code up.  it wouldn't make your solution any more elegant i guess, but it's nice to say a lot and type less.[/QUOTE]

Nope.

---

### Post by Quest-Master on 2005-06-06
One word for you: classes. :)

---

### Post by Mike Buksas on 2005-07-15
[QUOTE=jerome bettis]does python have the ternary operator ? yes : no

if it does there's several places where you could squeeze that in to clean the code up.  it wouldn't make your solution any more elegant i guess, but it's nice to say a lot and type less.[/QUOTE]

Not as such, but you can get almost the same behavior with 

```
a and b or c
```
 This works as long as b does not evaluate to false, (e.g.: 0, '', [], (), or None) in which case you always get c, regardless of a. There's more on this at the [python.org FAQ](http://www.python.org/doc/faq/programming.html#is-there-an-equivalent-of-c-s-ternary-operator)

Mike

---

### Post by dataw0lf on 2005-07-15
[QUOTE=Quest-Master]One word for you: classes. :)[/QUOTE]

No.  

Beginning Python programmers like to throw everything in classes like X programming language they learned.  What they don't understand is that modules will supply most of the functionality you usually use classes for in other languages.

The only reason to use classes in Python is for specific uses of special methods, or when you know you'll need to derive children from it.  

As for cleaning up the code, some Pythonistas like to use the dict() built in function rather than the dict = {} format.  As well, in your functions, rather than documenting them with #, use docstrings.  That's an inherent Pythonic route that you'll get burned on by more experienced Python programmers. 

I like it though, it looks decent from my standpoint.

---

### Post by Mike Buksas on 2005-07-15
[QUOTE=darthsabbath]Hey all, I've been learning Python over the last few weeks, and I think I've come a good ways.  I've managed a few small, working programs, like the one below.  However, despite the fact that they work, they just don't seem... elegant.  I was basically just looking for some advice on making the code more efficient.

Any help would be greatly appreciated. :D

Thanks,
Phil  

[/QUOTE]

I'd change the # stlye comments to docstrings. Then if you ever turn the script into a module, you can examine docstrings from the intrepreter with >> help(function).

Also, go with some more descriptive variable names. Sure, their meaning is obvious to you now, but in a few short weeks of not working on the code you can look at a variable like 'x' and wonder what the heck it means.

Also, I think the computer should make excuses when it loses. 
```

excuses = ["The sun was in my eyes!",
                  "I was overpowered by your massive body odor!",
                  "You cheated!"
                  "I don't like this game anyway."];


```
I'm sure you can think of better ones.   ;-)

Anyway,  the code looks pretty pythonic to me. You're making use of Pythons more advanced data structures like dictionaries, which is a good sign. If you think it's inelegant however, keep at it until you get something you like more.

Mike

---

