---
title: "First Python Project - code critique"
date: 2007-09-28
forum: Programming Talk
---

### Post by mutenewt on 2007-09-28
I haven't coded in 20 years but decided to give Python a try just for fun.  I always found programming games to be the best way for me to learn, so I thought I create a simple one vs one battle game.  After reading a couple of online tutorials and firing up Stani's Python Editor, I came up with the following after a few minutes of work/fun.

I know the game sucks - I'm just trying to learn.  What I'm looking for is feedback on the structure of the code.  I'd like to stop any bad habits before I continue.  Pls keep in mind, the bulk of my coding experience is with BASIC and the treaded GOTO statement - so this is my first while loop.  Yep - I'm that green.

Also, am I clearing the screen properly?  I had no clue how to do this but a quick google search gave the me the solution below.

Thx for the help!

```
# Monster Battle
# Very Simple One on One Battle Simulator

# fetch modules
import random
import os, sys

# initial variable values
wins = 0
HP = 10
MP = random.randrange(10) + 1

# Clear Screen / Intro
sys.stdout.write(os.popen('clear').read())
print "\nWelcome to Monster Battle v0.1"
print "\nHow many monsters can you defeat?"

# Battle

while HP > 0:
    print "\nWarrior HP: ", HP
    print "\nMonster HP: ", MP
    FH = raw_input("\n(f)ight or (h)eal? ")
# Fight
    if FH == "f":
        sys.stdout.write(os.popen('clear').read())
        print "\nThe warrior has chosen to Fight!  Good Luck Warrior."
        DMG = random.randrange(6) + 1
        MP = MP - DMG
        print "\nWarrior swings his mighting axe and does", DMG, "points of damage."
        if MP <= 0:
            print "\nThe Monster is slain."
            wins = wins + 1
            print "\nThe warrior has", wins, "wins"
            MP = random.randrange(10) + 1
        else:
            DMG = random.randrange(6) + 1
            print "\nThe Monster bites the Warrior for", DMG, "points of damage."
            HP = HP - DMG
            if HP <= 0:
                print "\nThe Warrior is dead.  He finished Monster Battle with", wins, "wins"
                print "\nThank you for playing Monster Battle v0.1\n"
            else:
                print "\nThe battle continues ..."
# Heal    
    else:
        sys.stdout.write(os.popen('clear').read())
        print "\nThe warrior has chosen to Heal!  Good Luck Warrior."
        HEAL = random.randrange(6) + 1
        print "\nThe Warrior heals", HEAL
        HP = HP + HEAL
        DMG = random.randrange(6) + 1
        print "\nThe Monster bites the Warrior for", DMG, "points of damage."
        HP = HP - DMG
        if HP <= 0:
            print "\nThe Warrior is dead.  He finished Monster Battle with", wins, "wins"
            print "\nThank you for playing Monster Battle v0.1\n"
        else:
            print "\nThe battle continues ..."
```

---

### Post by engla on 2007-09-29
The content is great :)

Here is some critique for the style.

1. Just some small python style things. Commonly, python files that are supposed to be run like a program (not included) usually start with
```
#!/usr/bin/env python
```
on the first line. Then, if they are marked with executable permissions they will run. 

The second part of this is that usually you don't have code free-flowing outside functions. You would typically have a main function:
```

def main():
	# here the application begins

```

And then you would have this strange idiom last in the file:
```
if __name__ == "__main__":
	main()
```
What this does? If this file is *run*, it has the python internal variable __name__ set, so main should be run. If the file is just imported, that if clause fails and main() is not run: ergo nothing happens. (This is if you import a file, you don't want an application starting, but you might want to borrow/use the possible classes or functions in the file).

2. Now to structure.
Define lots of functions! It's not silly to have many, short functions. They should have descriptive names and do one thing well. First, you perhaps want a main() function, as mentioned above (it could of course have any arbitrary name).

Your large if-else structure is a clear sign you can break that up into own functions. Also, you have the same code (to check if you live or die) two times -- that should be put together. In all, I often try to detect patterns; common things should be done together. A small piece of code should have one responsibility, and circumstances that do not relate to that task should not affect it. (for example the "output" functions should not depend on the type of terminal) etc.

I propose this structure
```
#!/usr/bin/env python

# Import modules

# define all the utility functions here
def fight_monster():
	pass

main():
	# set up warrior
	# print welcome message
	
	while HP > 0
		# print info
		# read action
		if action1
			fight_monster()
		else
			heal_warrior()
		
		# check health here


if __name__ == "__main__":
	main()
```

Thinking even more abstract, that battle loop should probably not be in main() but in its own function, let's call it battle_loop. Then you could probably define some kind of Warrior datastructure and use that to pass information around. For example main() could set up a warrior variable, then pass that to the battle() function...

3. There are tripe-quote strings in python that can span lines. So you can rewrite the heal message to
```
print """
The warrior has chosen to Heal!  Good Luck Warrior.

The Warrior heals %d

The Monster bites the Warrior for %d points of damage.""" % (HEAL, DMG)
```
if you want to.

---

### Post by mutenewt on 2007-09-30
Thx engla!!  Your post is exceptionally helpful.  I think the defining function idea is a great one.  Obviously not a big deal for a program as short as this but as I add more code it will keep things simple and also make it easier to reuse code in the future.  Really appreciate the help.

---

