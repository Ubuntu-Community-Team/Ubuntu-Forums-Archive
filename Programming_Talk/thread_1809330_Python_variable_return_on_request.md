---
title: "Python variable return on request"
date: 2011-07-21
forum: Programming Talk
---

### Post by The Cyph3r on 2011-07-21
So it's my second go at learning Python, and I decided to dive right in and make a program to return vocab terms for one of my college courses. Basically, I want the program to request the user to input the term, and the program returns the vocab term (entered as a variable).

So far what I have is: 

```
#This program SHOULD return vocab terms for Managerial Accounting


ContributionMargin = "The amount remaining from sales revenue after variable expenses have been deducted"
ContributionMarginRatio = "Contribution margin divided by sales"
var = 1

print "This is the ACCT 2302 vocab program"
print "Press 'ctrl+c' to close program"



while var == 1:
    print "Enter the vocabulary term(no spaces) to retrieve definition)"
    input("Enter a vocab term: ")
```So with only two terms entered, what must I do to allow the vocab terms I enter to be returned?

---

### Post by Bachstelze on 2011-07-21
For starters, never use input(), ever. Always use raw_input().

In order to achieve what you want, the best way is to store the data not in simple variables but in a *dictionary*, like this:

```
data = {} # Create the dictionary, then populate it with data
data['ContributionMargin'] = "The amount remaining from sales revenue after variable expenses have been deducted"
data['ContributionMarginRatio'] = "Contribution margin divided by sales"
```

Then your code can look like this:

```
data = {} # Create the dictionary, then populate it with data
data['ContributionMargin'] = "The amount remaining from sales revenue after variable expenses have been deducted"
data['ContributionMarginRatio'] = "Contribution margin divided by sales"

print "This is the ACCT 2302 vocab program"
print "Press 'ctrl+c' to close program"

while True:
    print "Enter the vocabulary term(no spaces) to retrieve definition)"
    s = raw_input("Enter a vocab term: ")
    print data[s]

```

The problem you will have with this code is that if the user enters a string that is not a key in the dictionary, your program will crash. To prevent this, you can use something called *exception handling*, but I guess this is better left for later. ;)

---

### Post by Bachstelze on 2011-07-21
(...)

---

### Post by The Cyph3r on 2011-07-21
Okay, so if I'm creating a program that references many individually defined variables for the user to trigger, then a "data = {}" dictionary is the best way to do it, or only in this situation?

Also, how do you signal the end of a "while True" loop?

---

### Post by TwoEars on 2011-07-21
> **The Cyph3r said:**
> Okay, so if I'm creating a program that references many individually defined variables for the user to trigger, then a "data = {}" dictionary is the best way to do it, or only in this situation?

Also, how do you signal the end of a "while True" loop?

1) Every time you need to map a set of keys to a set of values, you should use dict. See [http://docs.python.org/tutorial/datastructures.html#dictionaries](http://docs.python.org/tutorial/datastructures.html#dictionaries)



2) break.
```

print 'Before while.'
while True:
    print 'During while.'
    break

print 'Finished.'
```

---

### Post by Bachstelze on 2011-07-21
> **The Cyph3r said:**
> Okay, so if I'm creating a program that references many individually defined variables for the user to trigger, then a "data = {}" dictionary is the best way to do it, or only in this situation?

You can use a dictionary in a lot of cases, but in the case at hand, you use a dictionary because you want to access a variable whose name depends on another variable. Basically you have a variable s and you want to access "a variable whose name is the contents of s". In other languages you can do that directly but not in Python, so a dict is a simple and efficient way to do it.

*EDIT:* And even in languages where you can do it directly (e.g. PHP), it is generally considered bad style and rarely done in practice.

> Also, how do you signal the end of a "while True" loop?

You can use a break statement to exit it, but your program says to use Ctrl+C anyway.

---

### Post by The Cyph3r on 2011-07-21
If I want the loop to continue until the user wants to end the program, is it better to use the "while var == 1" method? Using the "while True" method, I can't see a way to make the user trigger the "break"...
But then again, I'm a n00b :p

---

### Post by TwoEars on 2011-07-21
> **The Cyph3r said:**
> If I want the loop to continue until the user wants to end the program, is it better to use the "while var == 1" method? Using the "while True" method, I can't see a way to make the user trigger the "break"...
But then again, I'm a n00b :p

Well, in Python, while True: is used a lot more, generally because it gives you better handling of what happens, and cuts down on lines.

Have a look at this - [http://wiki.python.org/moin/WhileLoop](http://wiki.python.org/moin/WhileLoop)

---

### Post by cgroza on 2011-07-21
While var == 1 is not very pythonic at all. It defeats the purpose of using python.

To break out of the loop, you would be changing the var variable anyway, so instead of that use break.

So:

```

while True:
    # do somethnig
    if something:
        break      # using the other method, you would be doing var = 0 here.

```

---

### Post by The Cyph3r on 2011-07-21
Yeah, when I thought about it, I went in and added this after the dictionary listing:
```

print "This is the ACCT 2302 vocab program"
print "Type 'end' to close program"



while True:
    s = raw_input("Enter the vocabulary term(no spaces) to retrieve definition: ")
    print data[s]
    if raw_input() == "end":
        break

```It's an ultra-simple program, I know..but we all have to start somewhere, and I might as well create something that I can actually USE!

---

### Post by cgroza on 2011-07-21
There is a little problem. What if the user actually wanted to see the word "end"?
So instead of checking for the word end, check for an empty string.
And really, asking the user if he wants to quit after each word is annoying.

So something like this could fix the problem:
```

if not s:
    break

```

---

