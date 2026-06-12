---
title: "frusterted with password module"
date: 2010-03-01
forum: Programming Talk
---

### Post by XXMy_Little_ShinigamiXX on 2010-03-01
hi im trying to make a password module until it continues to ask for a password until the value is correct. i have been at this for 2 + hours and have gotten nowhere. this is my code;

```

import sys

x = 'password'
guess = str(raw_input('please enter the passcode: '))
z = xrange(9, 50)

if guess == x:
 print 'congrats'
 import callme

if guess != x:
 while True:
  try:
   x = 'password'
   guess = str(raw_input('please enter the passcode: '))
   if x == guess:
    print 'congrats'
    import callme
    break
   else:
    pass
  except len(guess) >= z:
   print 'password is not more than 8 characters'
 
   #else:
   #sys.exit()
# the last two lines are just incase

``````

import sys

x = 'password'
guess = str(raw_input('please enter the passcode: '))
z = xrange(9, 50)

if guess == x:
 print 'congrats'
 import callme

if guess != x:
 while True:
  try:
   x = 'password'
   guess = str(raw_input('please enter the passcode: '))
  except len(guess) >= z:
   print 'password is not more than 8 characters'
  except guess == x:
   break
   print 'congrats'
   import callme
   #else:
   #sys.exit()
# the last two lines are just incase


```ive tried revising this about a million times nothing seems to work. i had it one time where i was having it ask what the password was and it would keep asking me what it was even if i got it correct. in short unless i get it right on the first guess it keeps asking me and never assumes the other value. so im assuming whats happening is it is jumping straight down to the not correct version of the code and staying there because its in a while loop. im just fed up with it ](*,) can someone PLEASE HELP ME  i understand its taking the first piece of coding it sees and then down to the next until i run out of code and i could do it that way but i dont want to i wana run a loop until the value is equal. 


----------------EDIT

could it be when it jumps down to the while false loop the value of x is not there so it isnt associating guess with the value of x?


nevermind i figured it out lol. ugh so frustrating lol. also just as a PS i posted my new working code on top and the non working code on bottom. just so everyone has an idea of what i was doing wrong lol.

---

### Post by CptPicard on 2010-03-01
A quick few-second look tells me that at least 'z' is being used wrong. It's a generator, not something you can compare like you're trying to.

---

### Post by XXMy_Little_ShinigamiXX on 2010-03-01
> **CptPicard said:**
> A quick few-second look tells me that at least 'z' is being used wrong. It's a generator, not something you can compare like you're trying to.

yes the z is being used wrong but im not too worried about that part, i actually planning on changing this module later on, because i dont plan on the password permanently being password lol. and the length thing i could add, or the number error and add something like ValueError to an except statement. i just wanted the idea behind the program to work. the z i kept up there strictly because it wasnt interrupting the code and it can be kept as an idea for when i revise it for use as a submodule. 

on that topic by the way, what do you mean generators cant compare? im sure youre an expert on python as you answered my questions a while back, and thank you for those great responses. by the way i updated those if you would please have a look at my response just making sure i understand them when you have time. also please share your diverse python knowledge explaining the meaning of the statement a generator cant compare like im trying to. im pretty sure what you mean is the range() function can only be used as a generator right? not to compare? so the fact i assigned a variable is fine because variables can compare, for example;

a = ['something', 'goes', 'here']
b = ['put', 'something', 'here']

and if you did a|b that would compare the lists right? do i have that symbol right? lol

so what youre saying is the range function cant be used for comparison right?
sorry if i talk a lot i find the more i talk the more i understand lol. :popcorn:

---

### Post by CptPicard on 2010-03-01
Actually, to be more exact, xrange is actually an iterable object, that you can get an iterator for  and then iterate over that:

```

>>> x = xrange(0,10)
>>> i = x.__iter__()
>>> i.next()
0
>>> i.next()
1
>>> x > 15
True
>>> x != 15
True
>>> x == 0
False

```

It also appears that you can do comparisons -- this is something I've never thought of even trying; it might have a sensible definition in terms of where in the sequence the iterator currently is -- but I can't figure out any actual useful meaning for the comparison results I'm getting...

And regarding your other thread post, I really suggest you dig deeper into some treatment of how OOP works in Python. There's plenty of good stuff on the net, but I also get the feeling that your current tutorial is a bit too heavy on jargon that is just confusing for you for the time being.

---

