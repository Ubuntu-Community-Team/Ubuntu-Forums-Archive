---
title: "Learning Python"
date: 2009-05-20
forum: Programming Talk
---

### Post by P=NP on 2009-05-20
I'm trying to teach myself programming and need an abstract real world example to help me along. Could someone please provide me with an outline of a basic program that runs in the background and checks if there are files in trash and automatically deletes them. Thank you.

---

### Post by jimi_hendrix on 2009-05-20
do you want a program or psuedo-code (a program that doesnt run, but is an outline for a program)

---

### Post by P=NP on 2009-05-20
No code, I want to figure that out on my own. I'm not sure I'm going to use the right terminology here but, what modules or functions need to be used and a general way of putting it together. 

I know all a program does is manipulate data. I don't know what makes a program run in the background (loop?). When does a program become a process? I don't know what functions are needed to read/write files. What's the best way to search through modules to find the ones you need?

I'm sorry if this is too basic,

Thanks again.

---

### Post by phrostbyte on 2009-05-20
You should probably start somewhere here:
[http://wiki.python.org/moin/BeginnersGuide](http://wiki.python.org/moin/BeginnersGuide)

or get a book. It will take some time and understanding to be able to write what you want. Start with something more simple, like program that can add two numbers together and print the result. :)

---

### Post by phrostbyte on 2009-05-20
Also a better begginer program would be a guess the number game eg:

Hello, welcome to guess-a-number
Guess a number: 14
Too low!
Guess a number: 25
Too high!
Guess a number: 20
You got it, the number was 20.

This will require understanding conditional loops and logic, but very little API except for like Math.random() to start with the number and print and read. I think I started programming by making a similar game to this.

---

### Post by P=NP on 2009-05-20
> or get a book. It will take some time and understanding to be able to write what you want. Start with something more simple, like program that can add two numbers together and print the result.

I already know how to do that. I know you need to learn the basics first, but I'm just not getting it. I can follow examples that teach syntax, but I don't know why I'd want to use it.

I'm trying something different. Maybe I don't have the patience, I'm not sure. But I'd really like to try, and I have been trying for awhile now. Everything I know about computers I've taught myself. This has been my first real stumbling block. 

This post is coming to you from my own web server that I set up. I'm going to need to learn MySQL and PHP if I want to go any further there.

Python is supposed to be a great beginner language - and I can't get it :(

---

### Post by phrostbyte on 2009-05-20
> **P=NP said:**
> I already know how to do that. I know you need to learn the basics first, but I'm just not getting it. I can follow examples that teach syntax, but I don't know why I'd want to use it.

I'm trying something different. Maybe I don't have the patience, I'm not sure. But I'd really like to try, and I have been trying for awhile now. Everything I know about computers I've taught myself. This has been my first real stumbling block. 

This post is coming to you from my own web server that I set up. I'm going to need to learn MySQL and PHP if I want to go any further there.

Python is supposed to be a great beginner language - and I can't get it :(

Of any programming, even experts, writing the first line of code is often the hardest thing. The first line of code is a process in itself.

You should start small though, with simple 10 line program. But the thing you requested is actually not very beginner, it's very API heavy. For first program you should think of things that does console input and output. That's all. Leave the file I/O for a little later, especially monitoring a folder that is actually quite complicated (no, you don't use an infinite loop to monitor a folder, that would be inefficient). 

Exploring the Python API should come after you have a good understanding of conditional logic, I think (eg: if statement, while loops). I don't know if you do? I am not sure what level you are at right now.

---

### Post by P=NP on 2009-05-20
> ...(eg: if statement, while loops)...Maybe there is more to it than I think, but doesn't it all come down to Boolean Logic?

---

### Post by monkeyking on 2009-05-20
> **P=NP said:**
> Maybe there is more to it than I think, but doesn't it all come down to Boolean Logic?

Everything comes down to boolean logic. ;)

Write a program that can add arbitrarily many numbers.

Thats a good excercise.

---

### Post by SCHolland on 2009-05-21
While not necessarily practical or real-world examples, I've found the following sites entertaining, informative, and a little frustrating:

[www.projecteuler.net](www.projecteuler.net)
[www.pythonchallenge.com](www.pythonchallenge.com)

I'm not far enough in either to determine if they're anything more than scripting challenges, but maybe they'll inspire you too. 

[Note: projecteuler requires registration to input/check answers]

Good luck!  If you find any examples more similar to what you were originally wanting, please post them.  I'd be interested in finding other exercises and examples too.

Steven

---

### Post by P=NP on 2009-05-21
I think I found more of what I was looking for, and as usual, don't know as much as I think I do. ;) I'm still looking for something a bit more involved, but I got to play with this a bit.
```

#we'll need the random module to make our guesses
import random

#set up these variables we decided were necessary.
#initializing variables like this is helpful because
#it helps people who're reading your code understand what your
#variables are, for the most part, and what you'll probably use them for.
#so make sure they all have nice descriptive names.
greeting = """ Welcome to the number-guessing game.
Hope you enjoy this! Hit enter to continue.  """
goodbye = "Thanks for playing the number-guessing game!"
usernum = 0
guessednum = 0
maxguesses = 5
guessed = False
min_guess = 0
max_guess = 100


#First order of business: greeting the user.
raw_input(greeting)

#now we want to get a number from him,
#and we'll store it in our usernum variable.
#we're going to assume the nice-user scenario where they know
#that by 'number' you mean 'integer' and not 'random gibberish.'
#you could use a try: -> except: block here, if you couldn't trust
#the user.
usernum = int(raw_input("What is your number?  "))

#once we have this number, we want to start up a loop
#that will continue to guess until it either gets the number right
#or runs out of guesses.

x = 0 #x is an arbitrary loop variable.
while x < maxguesses: #we'll loop until we reach the maximum guess limit.
    #we're using random.randrange because it behaves like range(), as 
John pointed out earlier.
    #this means if you call 'random.randrange(0,100)' the number will be 
0 or 99 or anywhere
    #in between, but not 100.  change the following line to either
    #'random.randrange(min_guess,max_guess+1)' or 
'random.randint(min_guess,max_guess)'
    #if you want to include both endpoints.
    guessednum = random.randrange(min_guess,max_guess)

    #now that we have the guessed number, let's compare it to the user's 
number.
    if usernum == guessednum: #if we guessed right :)
       guessed = True
       break#let's get out of the loop since we're sure we guessed 
correctly.
    elif usernum < guessednum: #we guessed too high.
       #the following line has what's called a 'string substitution.'
       #all of the '%s' items are replaced by the items in the 
parenthesis to the left of the string,
       #after the %.
       print "We guessed %s instead of %s, which is %s bigger than your 
number." % (guessednum,usernum,guessednum-usernum)
    elif usernum > guessednum: #we guessed too low.
       print "We guessed %s instead of %s, which is %s less than your 
number." % (guessednum,usernum,usernum-guessednum)
   
    #and finally, increment our loop-variable so we can keep track of 
how many times through
    #we've gone.
    x += 1

#now that the loop has ended, there are two outcomes:
#a.  we guessed correctly, and b. we guessed incorrectly.
if guessed: #option a.
    #we'll tell them we got it right.
    print "We guessed your number, %s!" % usernum
else: #option b.
    #we'll tell them they win.
    print "We couldn't guess %s, you win!" % usernum

#the game's over, so we'll say goodbye.
print goodbye

```I'm still very new to programming, but I'm assuming that was written in an earlier version of Python than I am using. I just installed the latest version of Python and IDLE3.0. I  debugged (is that right?) it to here:
```


import random

greeting = """ Welcome to the number-guessing game.
Hope you enjoy this! Hit enter to continue.  """
goodbye = "Thanks for playing the number-guessing game!"
usernum = 0
guessednum = 0
maxguesses = 5
guessed = False
min_guess = 0
max_guess = 100

#First order of business: greeting the user.
input(greeting)

#now we want to get a number from him,
#and we'll store it in our usernum variable.
#we're going to assume the nice-user scenario where they know
#that by 'number' you mean 'integer' and not 'random gibberish.'
#you could use a try: -> except: block here, if you couldn't trust
#the user.
ususernum = input("What is your number?  ")

#once we have this number, we want to start up a loop
#that will continue to guess until it either gets the number right
#or runs out of guesses.

x = 0 #x is an arbitrary loop variable.
while x < maxguesses: #we'll loop until we reach the maximum guess limit.
    #we're using random.randrange because it behaves like range(), as John pointed out earlier.
    #this means if you call 'random.randrange(0,100)' the number will be 0 or 99 or anywhere
    #in between, but not 100.  change the following line to either
    #'random.randrange(min_guess,max_guess+1)' or 'random.randint(min_guess,max_guess)'
    #if you want to include both endpoints.
    guessednum = random.randrange(min_guess,max_guess)

    #now that we have the guessed number, let's compare it to the user's 
#number.
    if usernum == guessednum: #if we guessed right :)
       guessed = True
       break#let's get out of the loop since we're sure we guessed 
#correctly.
    elif usernum < guessednum: #we guessed too high.
       #the following line has what's called a 'string substitution.'
       #all of the '%s' items are replaced by the items in the parenthesis to the left of the string after the %.
       print("We guessed % instead of %, which is % bigger than your number.") % (guessednum,usernum,usernum-guessednum)                                                  % (guessednum,usernum,guessednum-usernum)
    elif usernum > guessednum: #we guessed too low.
       print("We guessed % instead of %, which is % less than your number.") % (guessednum,usernum,usernum-guessednum)
   
    #and finally, increment our loop-variable so we can keep track of how many times through
    #we've gone.
    x += 1

#now that the loop has ended, there are two outcomes:
#a.  we guessed correctly, and b. we guessed incorrectly.
if guessed: #option a.
    #we'll tell them we got it right.
    print("We guessed your number, %s!") % usernum
else: #option b.
    #we'll tell them they win.
    print("We couldn't guess %s, you win!") % usernum

#the game's over, so we'll say goodbye.
print(goodbye)


#-#--------------------------End of File.

``` and got stuck. Could someone please explain this error to me?
```

Traceback (most recent call last):
  File "/home/test1/Desktop/Python Code/guessing game.py", line 47, in <module>
    print("We guessed % instead of %, which is % bigger than your number.") % (guessednum,usernum,usernum-guessednum)                                                  % (guessednum,usernum,guessednum-usernum)
TypeError: unsupported operand type(s) for %: 'NoneType' and 'tuple'

```I realize now I was a bit ahead of myself, but it seems the next best step would be to learn to write the output to a file with different string formatters and different data types.

I hope that explains a bit of where I'm at and any direction/advice would be greatly appreciated. Heavily commented code is great. Thanks!

---

### Post by crdlb on 2009-05-21
Make sure you're using python 2.6, not 3.0, since very few external libraries have been ported (so nobody else has switched either). IDLE 3.0 would be using python 3.0, I guess. Once you've ensured you're using 2.6, change your prints to look like ```
print "hello %s" % ("world",)
```
print is a statement in python 2.x, not a function. That said, you've also got duplicated code on line 47 that you need to remove (scroll way to the right), but I don't think that's causing the current error.

What seems to be happening is that you're using the % operator on the return value of the python 3.0 print function, which is always None, explaining the error message. (the % would need to be inside the parentheses so that it gets called on the string, but this is somewhat moot since you (imho) shouldn't use python 3.0 anyway)

Oh, and you need to be using "%s" inside the strings, not just "%" (there are other letters for numerical formatting, but %s in python works for numbers, just not with any special formatting)

---

### Post by trivialpackets on 2009-05-22
I'm all jumbled, I've been learning ruby, kind of switched into python, but I get my syntax confused as they are both mishmashed in my mind.  I shouldn't have done that.  But anyways.  My first task was similar to one noted here.  I created a game, where it asks you for a high number, then picks a number within the range of 1-that number randomly, then asks you to pick until you get the number.  Then, I decided I wanted to see how fast a computer could solve it, so I re-wrote it to solve itself.  The next step for me was to have the computer play the game x number of times and return their highest number of guesses, the lowest number of guesses and the average number of guesses.  My next step is to combine and have a game where the number is generated, the computer solves it, then asks you to solve it to see who wins!

---

