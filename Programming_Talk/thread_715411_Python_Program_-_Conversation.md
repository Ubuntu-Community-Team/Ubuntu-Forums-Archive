---
title: "Python Program - Conversation"
date: 2008-03-04
forum: Programming Talk
---

### Post by dev653 on 2008-03-04
Hi all,

Currently creating a python program. This program is a conversation between user and computer. A sample of a couple of questions:

```
name = raw_input("Hi there, I'm ConvoBot 1.0. What is your name? \n")
print "Nice to meet you",name
```

```
years = input("How old are you this year? \n")
seconds = years * 365 * 24 * 60 * 60
print "Oh my! You will be", seconds, "seconds old on your birthday!!" 
```

Now, in this program, further questions need to have a possible three responses..

```
feeling = raw_input("How are you feeling today? A: Good, B: Alright, C: Bad \n")
if feeling.upper() == "A":
    print <response A>
elif feeling.upper() == "B":
    print <response B>
elif feeling.upper() == "C":
    print <response C>
else:
    print <That wasn't A, B or C>
```

Now, with the above snippet of code, for each A, B and C, I want to generate a random response from a pool of 3 responses for each. So, A has three responses, B has three responses, C has three responses. If user chooses A, for instance, the computer responds with one of the RANDOM responses for A. My problem is actually getting them to be randomized and printed.

Any help would be greatly appreciated.

---

### Post by Wybiral on 2008-03-04
You use the "random" module for random numbers. For a random choice, you use the "choice" function from the "random" module.

Example:
```

>>> import random
>>> some_choices = ["Hello", "random", "world"]
>>> random.choice(some_choices)
'Hello'
>>> random.choice(some_choices)
'world'
>>> random.choice(some_choices)
'Hello'
>>> random.choice(some_choices)
random

```

---

### Post by Can+~ on 2008-03-04
Instead of "A) Good, B) Etc.." you could use a dictionary for each answer, and just output the matching one with the dictionary.

---

### Post by stevescripts on 2008-03-04
Let me begin by saying I have ~= 0, expierence with Python.  Due to all of the Python
folks here, and a desire to expand my horizons, I installed Python and Tkinter on this
box a few days back, and decided to tinker a bit.  

After googling about a bit, an hacking a couple of abortive ugly hacks, I checked back
and read Wybrial's comments.  Just a couple of minutes later, had a working proggie!

A question to the Python coders here, how would one use Python to catch erroneous user input? (eg, entering characters for age)

Steve

---

### Post by Wybiral on 2008-03-04
> **stevescripts said:**
> A question to the Python coders here, how would one use Python to catch erroneous user input? (eg, entering characters for age)

Steve

The easiest way would probably be to use an exception catch. The "int" function throws the "ValueError" exception when the string isn't an integer, so you can just catch this exception and do something about it.

```

user_in = raw_input("Enter a number: ")

try:
    x = int(user_in)
    print "%i is a number!" % x
except ValueError:
    print "'%s' is not an integer!" % user_in

```

---

### Post by stevescripts on 2008-03-04
TY again ;)

Steve

---

### Post by dev653 on 2008-03-09
Thanks for all the help guys. I went with the random function, with a try/except in there also. Here is my code.

```

ageflag = False
while ageflag == False
    try:
        years = int(raw_input("So " + name + ".. How old are you this year? \n"))
        seconds = years * 365 * 24 * 60 * 60
        print "Oh my! You will be", seconds, "seconds old on your birthday!!"
        ageflag =True
    except ValueError:
        print "That is not a number \n"
        ageflag = False

```

```

randomnum = random.randint(1,3)
feelresponse1 = "I'm good too. Yay!"
feelresponse2 = "I'm not so good. Maybe you can cheer me up.."
feelresponse3 = "Good to hear, good to hear."
if randomnum == 1:
    print feelresponse1
elif randomnum == 2:
    print feelresponse2
elif randomnum == 3:
    print feelresponse3

```

Again, much appreciated.

---

