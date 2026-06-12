---
title: "Python text based game help please."
date: 2007-11-15
forum: Programming Talk
---

### Post by Mr.popo on 2007-11-15
Hey, ive just set my self a task to make a text based game which can load a save game file and create one.

Im haveing a problem though.

Here is the programs source code.
```
 
# input and output functions.
def savefile(tries):
	# Create game save file.
	out_file = open("score.txt", "w")
	out_file.write(tries)
	out_file.close()
	
def readfile():
	# Read pre made file.
	in_file = open("score.txt", "r")
	score = in_file.read()
	in_file.close()
	
print "Welcome to guessgame .v2"
print "1. View previous scores"
print "2. New game"
choice = input("What do you want to do: ")
# if user chooses option 1
if choice == 1:
	readfile()

# if user chooses option 2
elif choice == 2:
	import random
	num = random.randint(0, 99)
	guess = 0
	tries = 1
	while guess != num:
		guess = input("Enter your guess: ")
		if guess < num:
			print "That is too low!"
		elif guess > num:
			print "Too high!"
		tries = tries + 1
			  
print "Correct the random number was, ", num ,". You took:  ", tries, "tries."

choice = 0

print "Do you want to: "
print "1. Save your score"
print "2. Quit"

choice = input("What do you want to do: ")
if choice == 1:
	print "1. Create a new game save file"
	print "2. Save in score file"
	choice = 0
	choice = input("What do you want to do: ")
	if choice == 1:
		savefile()
	   
	else:
		print "Error"

```

i keep getting an error for the 'savefile()'
i dont understand it though and dont have a clue on what i should fd to fix it.
Please can i have help
.
thanks

---

### Post by LaRoza on 2007-11-15
What is the error?

---

### Post by Mr.popo on 2007-11-15
Traceback (most recent call last):
  File "C:\Users\Richard\Desktop\guess game v2.py", line 51, in <module>
    savefile()
TypeError: savefile() takes exactly 1 argument (0 given)

error^^

---

### Post by LaRoza on 2007-11-15
> **Mr.popo said:**
> ```
 
if choice == 1:
	print "1. Create a new game save file"
	print "2. Save in score file"
	choice = 0
	choice = input("What do you want to do: ")
	if choice == 1:
		savefile()
	   
	else:
		print "Error"

```


The error is, savefile() is never given arguments. You should pass the value to the functions.

Fun game though, took me 7 tries.

---

### Post by Mr.popo on 2007-11-15
lol thanks,
ill try it now.


edit: im stuck , ive done this

savefile(tries)

so should that work?

---

### Post by LaRoza on 2007-11-15
Just so you know, it is not a guessing game, it is a game testing the users ability to think logically. Just do a binary search.

---

### Post by LaRoza on 2007-11-15
> **Mr.popo said:**
> lol thanks,
ill try it now.


edit: im stuck , ive done this

savefile(tries)

so should that work?

No, it must be a string that is written, so convert tries to a string.

---

### Post by LaRoza on 2007-11-15
Here it is:

[php]
# input and output functions.
def savefile(tries):
    # Create game save file.
    out_file = open("score.txt", "w")
    out_file.write(tries)
    out_file.close()
    
def readfile():
    # Read pre made file.
    in_file = open("score.txt", "r")
    score = in_file.read()
    in_file.close()
    
print "Welcome to guessgame .v2"
print "1. View previous scores"
print "2. New game"
choice = input("What do you want to do: ")
# if user chooses option 1
if choice == 1:
    readfile()

# if user chooses option 2
elif choice == 2:
    import random
    num = random.randint(0, 99)
    guess = 0
    tries = 1
    while guess != num:
        guess = input("Enter your guess: ")
        if guess < num:
            print "That is too low!"
        elif guess > num:
            print "Too high!"
        tries = tries + 1
              
print "Correct the random number was, ", num ,". You took:  ", tries, "tries."

choice = 0

print "Do you want to: "
print "1. Save your score"
print "2. Quit"

choice = input("What do you want to do: ")
if choice == 1:
    print "1. Create a new game save file"
    print "2. Save in score file"
    choice = 0
    choice = input("What do you want to do: ")
    if choice == 1:
        savefile(str(tries))
       
    else:
        print "Error"
[/php]

You might want to put some error handling in this, so no errors get through.

---

### Post by Mr.popo on 2007-11-15
> **LaRoza said:**
> Here it is:

[php]
# input and output functions.
def savefile(tries):
    # Create game save file.
    out_file = open("score.txt", "w")
    out_file.write(tries)
    out_file.close()
    
def readfile():
    # Read pre made file.
    in_file = open("score.txt", "r")
    score = in_file.read()
    in_file.close()
    
print "Welcome to guessgame .v2"
print "1. View previous scores"
print "2. New game"
choice = input("What do you want to do: ")
# if user chooses option 1
if choice == 1:
    readfile()

# if user chooses option 2
elif choice == 2:
    import random
    num = random.randint(0, 99)
    guess = 0
    tries = 1
    while guess != num:
        guess = input("Enter your guess: ")
        if guess < num:
            print "That is too low!"
        elif guess > num:
            print "Too high!"
        tries = tries + 1
              
print "Correct the random number was, ", num ,". You took:  ", tries, "tries."

choice = 0

print "Do you want to: "
print "1. Save your score"
print "2. Quit"

choice = input("What do you want to do: ")
if choice == 1:
    print "1. Create a new game save file"
    print "2. Save in score file"
    choice = 0
    choice = input("What do you want to do: ")
    if choice == 1:
        savefile(str(tries))
       
    else:
        print "Error"
[/php]

You might want to put some error handling in this, so no errors get through.



thanks mate. It worked.
Please can tell me what the str() function does
thanks

---

### Post by LaRoza on 2007-11-15
It converts the argument to a string and returns it. 

Also important are:

float()
int()
hex()
oct()
long()
unicode()

ord()   --  converts to ascii text, it only accepts one character.

---

### Post by Mr.popo on 2007-11-15
ok thanks.

---

