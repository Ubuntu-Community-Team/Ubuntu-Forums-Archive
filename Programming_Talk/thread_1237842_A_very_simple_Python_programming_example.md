---
title: "A very simple Python programming example"
date: 2009-08-11
forum: Programming Talk
---

### Post by phrostbyte on 2009-08-11
I was bored on a plane flight. A very simple number guessing game. Very well commented for people who want to start learning how to program.

To run, copy/paste this into a file like "guessthatnumber.py" and execute on the command line with ./guessthatnumber.py

```

#! /usr/bin/python
# Guess the number game
# A simple programming example

# Import Python's random number functionality into this program
from random import *

# Display the name of the game and instructions
print "GUESS THAT NUMBER! A number guessing game."
print "I, the computer, will pick a number from 1 to 100."
print "You will have to figure it out. You have six attempts. I will give you hints."

# The number of tries the user has tried so far.
# Since the game just started, this number is zero.
# Declare a variable and set it to zero
# A variable is just a container of memory that you can change and refer to
numTries = 0

# Have the computer randomly guess a number from 1-100 and keep it secret! 
# Save it into a variable
secretNum = randint(1,100)

# Loop around until the user had 6 tries
while numTries < 6:
	# The variable "readNum" will be equal to the number the user inputed
	readNum = int(raw_input("Guess a number: "))
	
	# Tell the user they guessed too high
	# Notice the mathematical relationship 
	# if readNum is GREATER THEN secretNum
	if readNum > secretNum:
		print "You guessed too high!"
	
	# elif means "else if"
	# This is the opposite of the above
	elif readNum < secretNum:
		print "You guessed too low!"
	
	# If readNum is neither GREARER THEN or LESS THEN secretNum
	# surely they are EQUAL
	# This means the user picked the correct secret number
	else:
		print "You gusssed correctly! You won!!"
		print "Hoooray you!! :D"
		
		# This exits the program
		exit(0)
	
	# Increase the number of tries, this takes the value in numTries
	# and increases it.
	numTries += 1

# This code only gets called if the loop ends
# Remember the program closes out manually when a user wins
# So this only gets executed when they lose
print "You had enough tries. You lost! :("
print "The number was " + str(secretNum)

```

---

### Post by pepperphd on 2009-08-12
Thank you! Python looks like fun.

---

### Post by days_of_ruin on 2009-08-12
FYI you will need to run ```
chmod +x guessthatnumber.py
``` before you can do ```
./guessthatnumber.py
```

---

### Post by bear24rw on 2009-08-12
or

```
python guessthatnumber.py
```

---

### Post by .Maleficus. on 2009-08-12
Looks good.  My only suggestions right now would be to work on your Python conventions (specifically your whitespace should be four spaces, not eight).  Here's a link to [PEP 8]("http://www.python.org/dev/peps/pep-0008/"), with some common conventions described by Guido van Rossum himself.

---

### Post by Bodsda on 2009-08-12
> **phrostbyte said:**
> I was bored on a plane flight. A very simple number guessing game. Very well commented for people who want to start learning how to program.

To run, copy/paste this into a file like "guessthatnumber.py" and execute on the command line with ./guessthatnumber.py

```

#! /usr/bin/python
# Guess the number game
# A simple programming example

# Import Python's random number functionality into this program
from random import *

# Display the name of the game and instructions
print "GUESS THAT NUMBER! A number guessing game."
print "I, the computer, will pick a number from 1 to 100."
print "You will have to figure it out. You have six attempts. I will give you hints."

# The number of tries the user has tried so far.
# Since the game just started, this number is zero.
# Declare a variable and set it to zero
# A variable is just a container of memory that you can change and refer to
numTries = 0

# Have the computer randomly guess a number from 1-100 and keep it secret! 
# Save it into a variable
secretNum = randint(1,100)

# Loop around until the user had 6 tries
while numTries < 6:
	# The variable "readNum" will be equal to the number the user inputed
	readNum = int(raw_input("Guess a number: "))
	
	# Tell the user they guessed too high
	# Notice the mathematical relationship 
	# if readNum is GREATER THEN secretNum
	if readNum > secretNum:
		print "You guessed too high!"
	
	# elif means "else if"
	# This is the opposite of the above
	elif readNum < secretNum:
		print "You guessed too low!"
	
	# If readNum is neither GREARER THEN or LESS THEN secretNum
	# surely they are EQUAL
	# This means the user picked the correct secret number
	else:
		print "You gusssed correctly! You won!!"
		print "Hoooray you!! :D"
		
		# This exits the program
		exit(0)
	
	# Increase the number of tries, this takes the value in numTries
	# and increases it.
	numTries += 1

# This code only gets called if the loop ends
# Remember the program closes out manually when a user wins
# So this only gets executed when they lose
print "You had enough tries. You lost! :("
print "The number was " + str(secretNum)

```

Nice post, comments are always good for new programmers. My only issue is that when you start putting limits on things, like the ```
# Loop around until the user had 6 tries
while numTries < 6:
```
line, I like to give people the option to change it. The following code just has a few extra lines to allow people to enter a value at the command line to change the maximum number of tries from 6 to whatever they want.
```

#! /usr/bin/env python
import random
import sys                               # Imports the sys module
if len(sys.argv) <= 1:                   # If there is a command line argument
        max_tries = 6                    # Set tries to 6
else:
    try:                                 # Try statement (Error handling)
        max_tries = int(sys[1])          # Try to convert argument to an int
    except ValueError:                   # Catch the error if the entered value is not a valid integer
        print "Error, max tries argument is not a valid integer, defaulting to 6."
        max_tries = 6                    # Default to 6

numTries = 0
secretNum = randint(1,100)

while numTries < max_tries:              # Use new max_tries variable as the loop conditional

```
Just my 2 pennies.

regards,
Bodsda

---

### Post by tatrefthekiller on 2009-08-13
I noticed a problem on the shabang : there is no space between "#!" and "/usr/bin/python"
It should be :
```
#!/usr/bin/python
```

---

### Post by days_of_ruin on 2009-08-13
> **tatrefthekiller said:**
> I noticed a problem on the shabang : there is no space between "#!" and "/usr/bin/python"
It should be :
```
#!/usr/bin/python
```

Better yet:```
#!/usr/bin/env python
```

That is supposed to work if python is installed in different place.

---

### Post by Bodsda on 2009-08-13
> **tatrefthekiller said:**
> I noticed a problem on the shabang : there is no space between "#!" and "/usr/bin/python"
It should be :
```
#!/usr/bin/python
```

The space is not important, but good attention to detail :)

---

### Post by karlmp on 2009-08-14
there's a lot of typos in that program

---

### Post by .Maleficus. on 2009-08-14
I just reread the code and noticed there wasn't any error-checking done.  I would make sure to either note that the program assumes input is an integer (and will crash if the input isn't) or do error checking in a try/except block.  If you don't know how to use those, Bodsda's example should get you going.

---

### Post by phrostbyte on 2009-09-26
> **.Maleficus. said:**
> I just reread the code and noticed there wasn't any error-checking done.  I would make sure to either note that the program assumes input is an integer (and will crash if the input isn't) or do error checking in a try/except block.  If you don't know how to use those, Bodsda's example should get you going.

Yeah I intentionally left out error checking and configuration. I kind of wanted to make this an example that someone with 0 programming knowledge can modify to discover the behavior of stuff like loops and conditional statements without having to read a book. I don't know if I succeed in this, it probably could use some work. :)

---

### Post by simartem on 2009-09-27
Thank you very much for this example!! I had been learning, programming on windows platform for over 10 years.. Now i am quite familiar with PHP + mySQL, html, css, xml, ajax / js, delphi, visual basic.. It has been only 15 days that i switched to Linux/Ubuntu and i was looking a start for learning new languages like python.. This is a good start for me :) Thanks again.

---

