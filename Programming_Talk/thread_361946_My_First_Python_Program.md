---
title: "My First Python Program"
date: 2007-02-15
forum: Programming Talk
---

### Post by thenetduck on 2007-02-15
Hi, 
 I just did my first pointless program for python. I am just really really happy to have a first small program in python that I wrote! anyway, not to spam but thought I would post it. It just gives you change back when you buy something with a dollar. 

```


# This program is for eduction and was written by The Net Duck
# Process
# This will take correct input from a user in money. 
#   It will tell how much change it (it being a vending machine) will 
#   give from a dollar. It can't be over a dollar or it will say you
#   don't have enoght money to buy whatever.
import math
# Define varibles
DOLLAR = 100
QUARTER = 25
DIME = 10
NICKEL = 5
PENNY = 1
userInput = input("Please enter how much the item costs in cents (no .): ")
changeBack = DOLLAR - userInput
# Sorts the quarts
numQuarters = changeBack/QUARTER
changeBack = changeBack%QUARTER

numDimes = changeBack/DIME
changeBack = changeBack%DIME

numNickel = changeBack/NICKEL
changeBack = changeBack%NICKEL

numPenny = changeBack

print "Number of Quarters"
print numQuarters
print "Number of Dimes"
print numDimes
print "Number of Nickels"
print numNickel
print "Number of Pennies"
print numPenny


```

I just can't figure out how to print more than one thing on a line at a time. Does anyone know how to do that? for instance, I want to print an int and a string on the same line. I notice very quickly that the + and << doesn't work. Thanks,
 The Net Duck

---

### Post by rasgryphon on 2007-02-15
put a comma in between what you want to print, ie:

print "Number of Quarters", numQuarters

the comma also adds a space, so that would come out like "Number of Quarters 1" not "Number of Quarters1"

---

### Post by JDahl on 2007-02-15
```
print "int: %i, string: %s" %(1,"abc")
```

---

### Post by thenetduck on 2007-02-15
> **rasgryphon said:**
> put a comma in between what you want to print, ie:

print "Number of Quarters", numQuarters

the comma also adds a space, so that would come out like "Number of Quarters 1" not "Number of Quarters1"

What if I wanted to just print out something without a space? How would I do that? With JDahl's suggestion? 

 The Net Duck

---

### Post by pmasiar on 2007-02-15
> **thenetduck said:**
> Hi, 
 I just did my first pointless program for python. I am just really really happy to have a first small program in python that I wrote! (...)
I just can't figure out how to print more than one thing on a line at a time.

this page: 
[http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Revenge_of_the_Strings](http://en.wikibooks.org/wiki/Non-Programmer%27s_Tutorial_for_Python/Revenge_of_the_Strings) will have answers for this and many other questions. Whole wikibook is excellent for beginners. You can find even more here: [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart)

Good luck!

---

### Post by rolando2424 on 2007-02-15
Well, it was better than my crappy Albhed-English translation script :D

---

### Post by duff on 2007-02-15
ok, now modify it so it shows all possible ways of making change without duplicates.

---

### Post by thenetduck on 2007-02-16
Man that is a really hard to think through (for me at least). I have made it my next goal to find all combinations, still working my psuedo out on paper though. Any suggestions on good or efficent was to do this? (Not asking for the solution but more of something to get me thinking in a different paradime) Thanks,
 
 The Net Duck

---

### Post by duff on 2007-02-16
> **thenetduck said:**
> Man that is a really hard to think through (for me at least). I have made it my next goal to find all combinations, still working my psuedo out on paper though. Any suggestions on good or efficent was to do this? (Not asking for the solution but more of something to get me thinking in a different paradime) Thanks,
 
 The Net Duck

It's a good recusion exercise.  I just did it in about 10 minutes...it's not that bad.  You don't even need to store anything (just your call stack).

---

### Post by rickardg on 2007-02-16
> **thenetduck said:**
> Man that is a really hard to think through (for me at least). I have made it my next goal to find all combinations, still working my psuedo out on paper though. Any suggestions on good or efficent was to do this? (Not asking for the solution but more of something to get me thinking in a different paradime) 

Start with trying to find a solution for a small instance of the problem, like changing 10 cents in nickels and pennies, then try to express the solution to a bigger problem in terms of the smaller ones.

This problem is actually quite tricky, even if the solution is simple once you've figured it out.

The straightforward solution found in most Computer Science textbooks is quite inefficient, a less wasteful implementation is left as an exercise for the interested reader... :-)

---

