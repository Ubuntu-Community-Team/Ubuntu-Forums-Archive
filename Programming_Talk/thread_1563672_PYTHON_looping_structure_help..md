---
title: "PYTHON looping structure help."
date: 2010-08-29
forum: Programming Talk
---

### Post by MikeVaughanG on 2010-08-29
I'm making a dice roller. 
The goal is to have the user chose how many dice to roll,

And then they choose how many sides each dice will have 
(each dice would have a different number of sides)

I've written a function to get the number of sides for a dice, but how do I run it a specific amount of times (variable 'dice') and use it to define a specific amount of variables (dice1,dice2,dice3, etc.)?

Here's what I've got so far. 
```

#Getting Number Of Dice
dice = raw_input("NUMBER OF DICE: ")

#Function to get Number of sides
def get_Sides():
	sides = raw_input("Number of Sides")
	return sides

```

Any help would be appreciated, or any input at all. 
Or if you think there's a completely better way to do this, lemme know. :D

Thanks in Advance
MikeVaughanG

---

### Post by Bachstelze on 2010-08-29
You don't really need a function for that:

```

import random

dice = []
n_dice = int(raw_input("Number of dice? "))
n_sides = int(raw_input("Number of sides? "))

for i in range(n_dice):
    n = random.randint(1, n_sides)
    dice.append(n)
    print("Dice %s is %s." % (i, n))

```

---

### Post by MikeVaughanG on 2010-08-29
That is probably a better way to go, but the code you wrote doesnt allow the user to input a different amount of sides for each dice.

---

### Post by Bachstelze on 2010-08-29
You should be able to figure that out: just move the "Number of sides?" input line into the loop.

---

### Post by worksofcraft on 2010-08-29
Instead of thinking about loops and other stone-age constructs, why not make a dice class? Then create instances of these dice objects with number of sides as specified by the user.

Put all your dice in a container... a list will do.

Then your code interates the dice container calling the "throw" method... um... no make that a "throw_dice" method or no doubt the Python interpreter will think there is some kind of exception being generated ;)

---

### Post by Bachstelze on 2010-08-29
> **worksofcraft said:**
> Instead of thinking about loops and other stone-age constructs, why not make a dice class? Then create instances of these dice objects with number of sides as specified by the user.

Put all your dice in a container... a list will do.

Then your code interates the dice container calling the "throw" method... um... no make that a "throw_dice" method or no doubt the Python interpreter will think there is some kind of exception being generated ;)

Oh, the joys of over-engineering.  You're ready to become a Java programmer.  :)

---

### Post by wmcbrine on 2010-08-29
> **worksofcraft said:**
> Instead of thinking about loops and other stone-age constructs, why not make a dice class?Because it's pointless? The fact that everything has to be a class in Java is a bug, not a feature.

What would that look like, anyway?

```
class Die:
    def __init__(self, sides):
        self.sides = sides

    def roll(self):
        return random.randint(1, self.sides)
```

...maybe? Like I said, pointless.

> *Then your code interates the dice container calling the "throw" method... um... no make that a "throw_dice" method or no doubt the Python interpreter will think there is some kind of exception being generated ;)*Python says "raise", not "throw".

---

### Post by worksofcraft on 2010-08-29
> **wmcbrine said:**
> Because it's pointless? The fact that everything has to be a class in Java is a bug, not a feature.

What would that look like, anyway?

```
class Die:
    def __init__(self, sides):
        self.sides = sides

    def roll(self):
        return random.randint(1, self.sides)
```

...maybe? Like I said, pointless.

Python says "raise", not "throw".

Lol - yeah I wasn't advocating Java. I heard it was designed for programming pop-up toasters :P

However while this particular application may seem trivial I have had to work on programs consisting of nested loops within loops and conditionals and so on that indent all the way to the right hand margin... and their perpetrators thought they were wonderful structured code but absolutely nobody else could follow the logic anymore.

IMHO it helps to start think OO from the inception and using things like polymorphism and constructors and destructors instead of setting flags and putting in conditionals.

Oh well, was just an idea... after all... I learnt my programming techniques in assembler, they might not be suitable to high level languages like Python :shock:

---

### Post by MikeVaughanG on 2010-08-29
Thank you, this has been helpful and entertaining. lol

Seriously, thanks. 

:D

---

