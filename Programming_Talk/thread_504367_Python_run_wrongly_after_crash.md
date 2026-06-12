---
title: "Python run wrongly after crash"
date: 2007-07-19
forum: Programming Talk
---

### Post by mocqueanh on 2007-07-19
i've write a litle code in Python. During the process, the code is error sometimes and i edited it. Each time code is error, Python run it and be crashed and my Windows has been freeze.

Finally, i have complete my program, but when i run in Python (after some crash), it is ran wrongly
(Please note: prreviously, each error time, Python has benn crash and i go to Task Manager of Windows, i kill all process called: python to make my Windows back to normally.)

My code:
```

# The game: User pick a random number from 0 to 100 and the computer has to guess

# The number of user

user_number = int(raw_input('My number: '))

# The number of computer guess

import random
computer_guess = random.randrange (101)
print "The computer guess your number is:", computer_guess

# All conditions

while computer_guess < user_number:
    raw_input('No, my number is ')
    computer_guess = random.randrange (computer_guess + 1, user_number + 1)
    print "The computer guess your number is", computer_guess
    if computer_guess < user_number:
        raw_input('No, my number is ')
        computer_guess = random.randrange (computer_guess + 1, user_number + 1)
        print "The computer guess your number is", computer_guess

while computer_guess  > user_number:
    raw_input('No, my number is ')
    computer_guess = random.randrange (user_number, computer_guess)
    print "The computer guess your number is", computer_guess
    if computer_guess > user_number:
        raw_input('No, my number is ')
        computer_guess = random.randrange (user_number, computer_guess)
        print "The computer guess your number is", computer_guess

# The computer has guess correctly

print "\nCongrate you, you have guessed correctly, my number is", user_number

# Exit the program

raw_input('\nPress Enter key to exit')      

```
When i run this code, sometimes, Python execute it correctly, sometimes wrongly

Run correctly:
[img]http://img178.imageshack.us/img178/2210/coderuncorrectup0.jpg[/img]
Run wrongly:
[img]http://img357.imageshack.us/img357/8742/runcodevq1.jpg[/img]

But after i restart Windows and run code again, it always run correctly.

Why ?

---

### Post by Quikee on 2007-07-19
Sorry I don't know why your code behaves in such a way but I just couldn't resist to clean up the code. 

```
# The game: User pick a random number from 0 to 100 and the computer has to guess

import random

user_number = None
computer_guess = None

while not user_number or user_number < 0 or user_number > 100:
	user_number = int(raw_input('My number: '))

while True:
	if not computer_guess:
		computer_guess = random.randrange(101)
	elif computer_guess < user_number:
		computer_guess = random.randrange(computer_guess + 1, user_number + 1)
	elif computer_guess > user_number:
		computer_guess = random.randrange(user_number, computer_guess)
	print "The computer guess your number is:", computer_guess
	
	if computer_guess == user_number:
		break
		
	raw_input('No, my number is ')

print "\nCongrate you, you have guessed correctly, my number is", user_number

raw_input('\nPress Enter key to exit')
```

It would also be better to store lowest guess and highest guess and do a new computer guess in between this interval because your implementation the interval is from guessed number and user number which looks like the computer knows the user number ;). 

You should do something like this:

```
# The game: User pick a random number from 0 to 100 and the computer has to guess

import random

user_number = None
computer_guess = None
lowest_guess = 0
highest_guess = 100

while not user_number or user_number < lowest_guess or user_number > highest_guess:
	user_number = int(raw_input('My number: '))

while True:
	computer_guess = random.randrange(lowest_guess, highest_guess)
	
	if computer_guess < user_number:
		lowest_guess = computer_guess
	elif computer_guess > user_number:
		highest_guess = computer_guess
	print "The computer guess your number is:", computer_guess
	
	if computer_guess == user_number:
		break
		
	raw_input('No, my number is ')

print "\nCongrate you, you have guessed correctly, my number is", user_number

raw_input('\nPress Enter key to exit')
```

Sorry to ruin all the fun..

---

### Post by ghostdog74 on 2007-07-19
```

user_number = int(raw_input('My number: '))
print "The computer guess your number is:",  user_number

```

---

