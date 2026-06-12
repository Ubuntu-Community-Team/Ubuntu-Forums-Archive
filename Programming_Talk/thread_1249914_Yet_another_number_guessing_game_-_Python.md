---
title: "Yet another number guessing game - Python"
date: 2009-08-25
forum: Programming Talk
---

### Post by Mirge on 2009-08-25
```

import random

maxTries = 5
minRand = 1
maxRand = 10

# Generate random number & set totalTries to 0
randNumber = random.randint(minRand, maxRand)
totalTries = 0
userGuess = 0

while True:
    userGuess = int(input("Please enter your guess: "))
    
    if userGuess == randNumber:
        print("Congratulations! You guessed correctly!")
        break
    
    if userGuess > randNumber:
        print("You guessed too high!")
    elif userGuess < randNumber:
        print("You guessed too low!")
        
    totalTries = totalTries + 1
    if totalTries == maxTries:
        print("Game over! The correct number was: " + str(randNumber))
        break

```Be gentle, this is my first Python app -- ever.

Am I blind, or does Python not support an increment/decrement operator? Trying totalTries++ threw an error.

---

### Post by Mirge on 2009-08-25
I'm starting to enjoy Python though... only 27 lines of code, and it could have easily been shortened, but it was my first app :). Took a whopping 2-3 minutes to build, being a complete beginner to Python I don't consider that too bad!

Couple things that keep tripping me up...

1.) No semicolon to mark end of statement.
2.) No braces to mark blocks (indention instead).
3.) "Casting" I guess it could be called... I keep trying to do something like: (str)randNumber, instead of str(randNumber).

---

### Post by Mirge on 2009-08-25
Additional note: fails (obviously) when input contains non-numeric characters -- suppose I should read up on error/exception handling!

---

### Post by Mirge on 2009-08-25
Changed the user input portion to:

```

    try:
        userGuess = int(input("Please enter your guess: "))
    except ValueError:
        print("Please enter a valid number.")
        continue

```

Pretty neat how easy Python is to pick up actually...

---

### Post by DirtDawg on 2009-08-25
FYI: for increments, try '+=' rather than '++'
example: x += 1

Glad you're having fun. Python is really great.

---

### Post by Mirge on 2009-08-26
> **DirtDawg said:**
> FYI: for increments, try '+=' rather than '++'
example: x += 1

Glad you're having fun. Python is really great.

Ahh thanks! That's much better :).

---

### Post by sam191 on 2009-08-26
Nice! I remember doing something like this. 

One thing to note: use 'raw_input' instead of 'input' for safer coding. 

Other than that, I'm glad you're liking Python.

---

### Post by Mirge on 2009-08-26
> **sam191 said:**
> Nice! I remember doing something like this. 

One thing to note: use 'raw_input' instead of 'input' for safer coding. 

Other than that, I'm glad you're liking Python.

EDIT: Apparently raw_input() was replaced with input() in Python 3, which is what I'm using :). Thanks for pointing that out though, I wasn't aware of the difference there.

---

