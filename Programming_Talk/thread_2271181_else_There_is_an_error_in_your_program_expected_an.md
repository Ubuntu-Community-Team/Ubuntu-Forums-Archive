---
title: "else: There is an error in your program: expected an indented block.  Then syntax err"
date: 2015-03-28
forum: Programming Talk
---

### Post by JPython on 2015-03-28
# This tells the computer to import the information required to run random
import random
# This tells the computer that random is in the .randit area of python
secret = random.randit (1, 99)
# guess = 0 and tries = 0 means that the smallest number that the guess or tries can be is 1 (the 0 number in the series)
guess = 0
tries = 0
# The following prints will be printed at the beginning of the game.
print ("AHOY! I'm the Dreaded Pirate Roberts and I have a secret!")
print ("it is a number from 1 to 99. I'll give you 6 tries. ")
# the following gives the criteria of what the results might be.
# This statement says - Until the guess is not secret and there must be less that 6 guesses (remembering 0 is the first so there will be 6 guesses)
while guess != secret and tries <6:
# This is asking for the player to input their guess
    guess = input("What's yer guess?")
# The int(guess) converts the following text to an integer (whole number)
    guess = int(guess)
# Once input this statement asks if the guess is less than the secret then print "Too low, ye scurvy dog!)
    if guess < secret:
        print ("Too low, ye scurvy dog!")
# This states that else if the guess is greater than secret print the following statement
    elif guess > secret:
        print ("Too high, landlubber!")
# 
    tries = tries + 1
# This states that if the guess is not secret then print "Avast ..........."
if guess == secret:
# Else: tells us that finally if none of the above happen then print "No .................." and print "The secret ..............." with the number that the random secret number was
else:
        print ("No more guesses!")
        print ("The secret number was", secret)

---

### Post by JPython on 2015-03-28
Hi, I have input my coding where I am making many comments.  When I run the code I get an error suggesting I indent the else: but when I do this I then get a syntax error.  Can anyone help?

---

### Post by sisco311 on 2015-03-28
Moved to [B]Programming Talk.
[/B]
Please use [noparse]```
[/noparse] tags: 
[noparse][code]
your code here
...

```[/noparse] 

Which programming language are you using?

---

### Post by spjackson on 2015-03-28
It looks like Python, in which case the problem is that you cannot have an empty block for the if branch.

```

# This is OK.
if 1 == 2:
    print ("truth")
else:
    print ("lie")

# but this is a syntax error.
if 1 == 2:
#    print ("truth")
else:
    print ("lie")

```

If you really want a block that does nothing, use "pass", e.g.
```

if 1 == 2:
    pass
else:
    print ("lie")

```

---

### Post by ofnuts on 2015-03-28
> 
This tells the computer that random is in the .randit area of python


*cough*

You logic is a bit flawed, you have coded, roughly
```

if too high:
    mocking anwers 1
elif too low:
   mocking answer 2

bump the tries count

if gotit:

else:
   dismiss

```
Si you have an 'elif' without an 'else' and I don't think this is allowed. Correct and simplre logic:
```

[code]
bump the tries count
if too high:
    mocking anwers 1
elif too low:
   mocking answer 2
else: # got it....
  congratulations
  exit loop

if nomoretries:
   dismiss
   exit loop

```

---

