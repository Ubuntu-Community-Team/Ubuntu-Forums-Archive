---
title: "I'd like some feedback..."
date: 2007-01-21
forum: Programming Talk
---

### Post by fatsheep on 2007-01-21
I'm a newer programmer trying to learn python.  The practice problems from the python bibliotheca seemed pretty useful exercises so I'm attempted some of those: [http://www.ibiblio.org/obp/pyBiblio/practice/wilson/](http://www.ibiblio.org/obp/pyBiblio/practice/wilson/).  I know there's a more elegant way to do these exercises but I'm not sure exactly how so that is why I'm posting this.  Any feedback would be very valuable, I'm pretty new to python so some basic tips and pointers would be great.  

Here's what I did for the rock, paper, scissors game.  This one is probably the ugliest of the m all.  It works but there is a lot of repetition in the code, I'm not exactly sure how I could make it better though (which is why I'm posting this).

```

#!/usr/bin/python

import random

def findResult(choice_val, comp_choice):
	if choice_val == comp_choice:
		result = "Draw!"
	if (choice_val == 1 and comp_choice == 3) \
	or (choice_val == comp_choice +1):
		result = "Human wins!"
	if (choice_val == 3 and comp_choice == 1) \
	or (choice_val == comp_choice - 1):
		result = "Computer wins!"
	return result 

print "Welcome to rock, paper, scissors! \
You can type \'q\' at any time to exit."
print "-----------------"
print ""
choice = 0
while choice != "q" and choice != "Q":
	comp_choice = random.randint(1,3)
	choice = raw_input("Choose (R)ock, (P)aper, or (S)cissors? ")
	if choice == "r" or choice == "R":
		choice_val = 1
		user_choice = "Rock"
	elif choice == "p" or choice == "P":
		choice_val = 2
		user_choice = "Paper"
	elif choice == "s" or choice == "S":
		choice_val = 3
		user_choice = "Scissors"

	if comp_choice == 1:
		print "Computer: Rock",
	elif comp_choice == 2:
		print "Computer: Paper",
	elif comp_choice == 3:
		print "Computer: Scissors",
	print "\tHuman: %s\t" % user_choice,
	print findResult(choice_val, comp_choice)

```

Here's my loan calculator:

```

#!/usr/bin/python

# Principal * Interest Rate * Length of Loan

principal = float(raw_input("Amount borrowed: "))
rate = float(raw_input("Interest Rate (in %): ")) / 100
length = float(raw_input("Length of Loan: "))
print ""

print "Ammount borrowed: $%.2f" % principal 
print "Interest Rate: %.0f%%" % (rate * 100)
print ""
print "---------------"

print "Payment \t Amount \t Remaining"
print "Number  \t  Paid  \t  Balance "
print "--------\t--------\t----------"

balance = principal + (rate * principal * length)

monthly_payment = balance / (length * 12) 
print "0\t\t",
print "$0.00\t\t",
print "$%.2f" % balance

for i in range(12 * int(length)):
	balance -= monthly_payment
	print "%d\t\t" % (int(i) + 1),
	print "$%.2f\t\t" % monthly_payment,
	print "$%.2f" % balance

```

Here's the guessing game (you try to guess a random number 1 - 100):

```

#!/usr/bin/python

# Guessing game: computer generates a random int 1 - 100, you try
# to guess what it is.
import random

def guess(string):
	global user_guess
	user_guess = int(raw_input(string))

random_number = random.randint(1,100)
guess("Enter a number between 1 and 100: ")

iterations = 0
while(1):
	iterations += 1
	#print "Iteration #: ", "" + str(iterations) + ""
	if (user_guess > random_number):
		guess("Too high, guess again: ")
	elif (user_guess < random_number):
		guess("Too low, guess again: ")
	else:
		print "---------------------------------------"
		print "Congratulations you guessed the number on your " + str(iterations) + "th try!"
		print "---------------------------------------"
		break

```

And here's the leap year finder while I'm at it.  You enter a year, it tells you whether or not that year is a leap year:

```

#!/usr/bin/python

# User inputs a year, computer tells user whether or not
# the year is a leap year.

year = int(raw_input("Enter a year: "))
if (year % 4 == 0) and (year % 100 != 0) or (year % 400 == 0):
	print "" + str(year) + " is a leap year."
else:
	print "" + str(year) + " is NOT a leap year."

```

Again, any help is greatly appreciated.

---

### Post by jblebrun on 2007-01-21
These certainly aren't bad first attempts. Here are my comments:

1. Rock, Paper, Scissors.
*You can use a dictionary to make your implementation much easier.
*Your input reading loop should have feedback for an error condition. 

2. Loan Calculator
*For program maintainability, it's a good idea to separate the calculation and output portions of the program. (In particular, separating the model, the view, and the control.)

3. Guess a number
*This is a bad scenario in which to use global variables. since the guess function generates data that the caller is interested in, you should make theguess a return value of the guess function. 

4. Leap year
*Looks good to me!

---

### Post by fatsheep on 2007-01-21
Ok here's the modified rock, paper, scissors program with error checking, dictionaries, and it keeps records now too.  There's a couple really long statements in here like:
> if choice != 'r' and choice != 'R' and choice != 'p'\
	and choice != 'P' and choice != 's' and choice != 'S'\
	and choice != 'q' and choice != 'Q':
There *has* to be an easier way to say that...  Also,  since I want the program to accept lowercase or uppercase I have to define letters twice in the let_conv dictionary.  Is there a way just to tell python to ignore case?  

```
#!/usr/bin/python

import random
# number conversion 
num_conv = { 1 : "rock", 2 : "paper", 3 : "scissors" }

# letter conversion
let_conv = { 'r' : 1, 'p' : 2, 's' : 3, 'R' : 1, 'P' : 2, 'S' : 3 }

def findResult(choice_val, comp_choice):
	if choice_val == comp_choice:
		result = "Draw!", 0
	if (choice_val == 1 and comp_choice == 3) \
	or (choice_val == comp_choice +1):
		result = "Human wins!", 1
	if (choice_val == 3 and comp_choice == 1) \
	or (choice_val == comp_choice - 1):
		result = "Computer wins!", 2
	return result 

print "Welcome to rock, paper, scissors! \
You can type \'q\' at any time to exit."
print "-----------------"
print ""

compW = 0
humanW = 0
choice = 0
while choice != "q" and choice != "Q":
	choice = raw_input("Choose (R)ock, (P)aper, or (S)cissors? ")
	if choice != 'r' and choice != 'R' and choice != 'p'\
	and choice != 'P' and choice != 's' and choice != 'S'\
	and choice != 'q' and choice != 'Q':
		print "Error invalid option!"
		continue

	choiceVal = let_conv[choice]
	print "Human: " + num_conv[choiceVal] + "\t",
	comp_choice = random.randint(1,3)
	print "Computer: " + num_conv[comp_choice] + "\t",
	result = findResult(choiceVal, comp_choice)
	print "%s" % result[0]
	
	if result[1] == 0:
		pass
	elif result[1] == 1:
		humanW += 1
	elif result[1] == 2:
		compW += 1

	print "Human %d - %d\t" % (humanW, compW),
	print "Computer %d - %d\t" % (compW, humanW)
	print "--------"


```

Here's the rewritten loan calculator, did the best I could to keep the output seperate from the calculations:

```
#!/usr/bin/python

# Principal * Interest Rate * Length of Loan

def printVal(i, monthly_payment, balance):
	print "%d\t\t" % i,
	print "$%.2f\t\t" % monthly_payment,
	print "$%.2f" % balance
	if i % 13 == 0:
		print ""
		print "Year %d" % ((i / 13) + 1)
		print "---"




principal = float(raw_input("Amount borrowed: "))
rate = float(raw_input("Interest Rate (in %): ")) / 100
length = float(raw_input("Length of Loan: "))
print ""

print "Ammount borrowed: $%.2f" % principal 
print "Interest Rate: %.0f%%" % (rate * 100)
print ""
print "---------------"

print "Payment \t Amount \t Remaining"
print "Number  \t  Paid  \t  Balance "
print "--------\t--------\t----------"

balance = principal + (rate * principal * length)
monthly_payment = balance / (length * 12) 

printVal(0, 0.00, balance)
for i in range(12 * int(length)):
	balance -= monthly_payment
	printVal((i + 1), monthly_payment, balance)

```

And here's the slightly modified "guess a number" program:

```

#!/usr/bin/python

# Guessing game: computer generates a random int 1 - 100, you try
# to guess what it is.
import random

def guess(string):
	user_guess = int(raw_input(string))
	return user_guess

random_number = random.randint(1,100)
user_guess = guess("Enter a number between 1 and 100: ")

iterations = 0
while(1):
	iterations += 1
	#print "Iteration #: ", "" + str(iterations) + ""
	if (user_guess > random_number):
		user_guess = guess("Too high, guess again: ")
	elif (user_guess < random_number):
		user_guess = guess("Too low, guess again: ")
	else:
		print "---------------------------------------"
		print "Congratulations you guessed the number on your " + str(iterations) + "th try!"
		print "---------------------------------------"
		break

```

---

### Post by pmasiar on 2007-01-21
> **fatsheep said:**
> I'm a newer programmer trying to learn python.  The practice problems from the python bibliotheca seemed pretty useful exercises so I'm attempted some of those: [http://www.ibiblio.org/obp/pyBiblio/practice/wilson/](http://www.ibiblio.org/obp/pyBiblio/practice/wilson/). 

Thanks for the link. I am slowly creating another source, [http://learnpydia.pbwiki.com/](http://learnpydia.pbwiki.com/) with some more (and more advanced) tasks to solve - you might be interested to look there too.

---

### Post by jblebrun on 2007-01-22
pmasiar, you might be interested in this link, too:

[http://www.pythonchallenge.com/](http://www.pythonchallenge.com/)

It's a set of puzzles that gets pretty challenging, but lots of fun! It also requires learning about some of the python libraries available from third parties, so be warned in advance!

---

### Post by pmasiar on 2007-01-22
very good effort. Don't be discouraged I have suggestions - it took me years to get here ;-)

1) Avoid 'magic numbers and strings'. You will be much better of to use constants for them. Like ROCK = 'rock' etc., then use ROCK in your code. You can change later how to call them, translate to other language etc.

2) Think more about naming variables. It really helps in bigger programs. Ie. you could use variables **human** and **computer**, with possible values ROCK, PAPER SCISSORS.

3) function chaining can simplify your code. You can read input and convert it to uppercase: **human = raw_input("Choose (R)ock, (P)aper, or (S)cissors? ").upper()**

4) dictionaries can convert set of data to another: **names = dict(R=ROCK, P=PAPER, S=SCISSOR)** and you can add this transformation to input to deal with it once and for all:

```
PROMPT = "Choose (R)ock, (P)aper, or (S)cissors?"
human = names[raw_input( PROMPT ).upper()]
```

5) Dictionaries can be used also for evaluating like this: dictionary, where keys are choices (human+computer) and values (also constants) are scores: +1 for human win, -1 for computer win, 0 for draw:

```

scores = {ROCK+PAPER: LOSE, ROCK+ROCK: DRAW, ROCK+SCISSORS: WIN,
                 PAPER+PAPER: DRAW, PAPER+ROCK: WIN, PAPER+SCISSORS: LOSE,
                 SCISSORS+PAPER: WIN, SCISSORS+ROCK: LOSE, SCISSORS+SCISSORS: DRAW,
                }

result = score[human+computer] 
```

So you have evaluation of any combination in 1 line!

In general, often you use dictionaries to create decision tables, and then you don't code - you put your logic into decision tables = dictionaries, away from your code. You can load decision table from database or config file to additional flexibility.

---

### Post by fatsheep on 2007-01-23
> **pmasiar said:**
> very good effort. Don't be discouraged I have suggestions - it took me years to get here ;-)

1) Avoid 'magic numbers and strings'. You will be much better of to use constants for them. Like ROCK = 'rock' etc., then use ROCK in your code. You can change later how to call them, translate to other language etc.

2) Think more about naming variables. It really helps in bigger programs. Ie. you could use variables **human** and **computer**, with possible values ROCK, PAPER SCISSORS.

3) function chaining can simplify your code. You can read input and convert it to uppercase: **human = raw_input("Choose (R)ock, (P)aper, or (S)cissors? ").upper()**

4) dictionaries can convert set of data to another: **names = dict(R=ROCK, P=PAPER, S=SCISSOR)** and you can add this transformation to input to deal with it once and for all:

```
PROMPT = "Choose (R)ock, (P)aper, or (S)cissors?"
human = names[raw_input( PROMPT ).upper()]
```

5) Dictionaries can be used also for evaluating like this: dictionary, where keys are choices (human+computer) and values (also constants) are scores: +1 for human win, -1 for computer win, 0 for draw:

```

scores = {ROCK+PAPER: LOSE, ROCK+ROCK: DRAW, ROCK+SCISSORS: WIN,
                 PAPER+PAPER: DRAW, PAPER+ROCK: WIN, PAPER+SCISSORS: LOSE,
                 SCISSORS+PAPER: WIN, SCISSORS+ROCK: LOSE, SCISSORS+SCISSORS: DRAW,
                }

result = score[human+computer] 
```

So you have evaluation of any combination in 1 line!

In general, often you use dictionaries to create decision tables, and then you don't code - you put your logic into decision tables = dictionaries, away from your code. You can load decision table from database or config file to additional flexibility.

Thanks for the suggestions, below is the further improved rock paper scissors game.  One thing I'd like to point out is that this version no longer catches invalid options like it did in the last program for some reason (I believe this is because the user's choice is accessing a dictionary before being parsed for an invalid option).  Further comments?

```

#!/usr/bin/python

## IMPORTS ##
import random

## CONSTANTS ##
ROCK = "ROCK"
SCISSORS = "SCISSORS"
PAPER = "PAPER"
QUIT = "QUIT"

DRAW = "DRAW"
WIN = "WIN"
LOSE = "LOSE"

PROMPT = "Choose (R)ock, (P)aper, or (Scissors): "

## DICTIONARIES AND LISTS ##
conv = { 'R' : ROCK, 'P' : PAPER, 'S' : SCISSORS, 'Q' : QUIT }
num_conv = { 1 : ROCK, 2 : PAPER, 3 : SCISSORS }
# human + computer 
score = { ROCK+PAPER: LOSE, ROCK+ROCK: DRAW, ROCK+SCISSORS: WIN,
	  PAPER+ROCK: WIN, PAPER+PAPER: DRAW, PAPER+SCISSORS: LOSE,
	  SCISSORS+ROCK: LOSE, SCISSORS+SCISSORS: DRAW, SCISSORS+PAPER: WIN }

### FUNCTONS ###

def print_records(humanW, compW):
	print "----- RECORDS -----"
	print "Human: %s - %s, Computer: %s - %s" % (humanW, compW, compW, humanW)
	print ""	

## VARIABLE DECLARATIONS ##
human = 0
humanW = 0
compW = 0
while True:
	human = conv[raw_input(PROMPT).upper()]

	if human != ROCK and human != SCISSORS and human != PAPER and human != QUIT:
		"Invalid Option!"
		continue
	if human == QUIT:
		break

	computer = num_conv[random.randint(1,3)]
	print "Human: %s\t" % human,
	print "Computer: %s\t" % computer,
	results = score[human+computer]
	
	
	if results == WIN:
		humanW += 1
		print "Human wins!"
	elif results == LOSE:
		compW += 1
		print "Computer wins!"
	else:
		print "Draw!"
	print_records(humanW, compW)	

```

---

### Post by pmasiar on 2007-01-23
Another way to define dictionaries is: conv = dict(R=ROCK, P=PAPER, S=SCISSORS)

Another trick: you can assign multiple values and create 1-character variables: 
r, p , s, q  = ROCK, PAPER, SCISSORS, QUIT
R, P, S, Q = ROCK, PAPER, SCISSORS, QUIT
then you can use input() instead of raw_input. Python will *evaluate* input (replacing variable name with value). Of course, humans being humans will enter something invalid, so you need to catch exception (wrong input)

```
try:
    human = input(PROMPT)
except:
    print 'Valid input is:', PROMPT
    continue
```

---

### Post by pmasiar on 2007-01-23
OK here is my solution, just FYI

```
import random

## Constants 
ROCK, PAPER, SCISS, QUIT = "Rock", "Paper", "Scissors", "Quit"
DRAW, WIN, LOSE = "Draw", "Win", "Lose"
PROMPT = "Choose (R)ock, (P)aper, (S)cissors, or (Q)uit: "

r, p, s, q = ROCK, PAPER, SCISS, QUIT
R, P, S, Q = ROCK, PAPER, SCISS, QUIT

# Scoring: human + computer: ==> human wins/loses
score = { 
          ROCK+PAPER: LOSE, ROCK+ROCK: DRAW,    ROCK+SCISS: WIN,
	  PAPER+ROCK: WIN,  PAPER+PAPER: DRAW,  PAPER+SCISS: LOSE,
	  SCISS+ROCK: LOSE, SCISS+SCISS: DRAW,  SCISS+PAPER: WIN,
          }

HumanWins = 0
ComputerWins = 0
TotalGames = 0

while True:
    try:
        human = input(PROMPT)
    except:
        print 'Valid input is:', PROMPT
        continue
    if human == QUIT:
        break
    computer = random.choice([ROCK, PAPER, SCISS])
    result = score[human+computer]        
    TotalGames += 1
    print 'Human: ',  human, '\tComputer: ', computer, '\t You ', result
    if result == WIN:
        HumanWins += 1
    elif result == LOSE:
        ComputerWins += 1
    
print '\n\nSummary:', TotalGames, 'games'
print 'Human won',  HumanWins, 'games'
print 'Computer won',  ComputerWins, 'games'
```

---

