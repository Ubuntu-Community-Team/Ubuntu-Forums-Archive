---
title: "idiomatic Python advice sought"
date: 2008-04-09
forum: Programming Talk
---

### Post by stevescripts on 2008-04-09
Moving along from coin flips in another thread, to rolling a pair of dice.

Consider the following simple script:
```

#! /usr/bin/python

import random

def roll(var):
	result = random.randrange(1,7);
	var = result
	return var;

die1 = 0
die2 = 0

def aThrow(var1, var2):
	var1 = roll(var1);
	var2 = roll(var2);
	result = var1 + var2;
	return result;

x = 0
theList = []

while x < 20:
	result = aThrow(die1, die2);
	x += 1;
	theList.append(result);
	
print "theList = ", theList

```

What would be the standard idiomatic Python method to determine the number of instances of each result?

TIA

Steve
(who is enjoying tinkering with Python (and other stuff) in his spare time at home ;) )

---

### Post by Wybiral on 2008-04-09
I would use:

```

n = 10
dice = [random.randint(1, 6) for i in xrange(n)]
print dice

```

Wait, why are you using semi-colons in Python?

---

### Post by CptPicard on 2008-04-09
Interestingly I am involved in a similar exercise, only this time with Haskell and monads...

[http://en.wikibooks.org/wiki/Programming:Haskell_monads#Stateful_Computations](http://en.wikibooks.org/wiki/Programming:Haskell_monads#Stateful_Computations)

---

### Post by stevescripts on 2008-04-09
CptPicard 

:)

I will get around to this in common lisp and scheme sometimes too

Wybiral - the semi-colons are a bad habit?

(I made a post asking that, that seems to have disappeared into a rip in the fabric of the net)

All criticisms gratefully accepted

Steve

---

### Post by WW on 2008-04-09
First, a comment on your functions.  The arguments to your functions serve no purpose.  You could just as well define your functions like this:
[php]
def roll():
	return random.randrange(1,7)

def aThrow():
	return roll()+roll()
[/php]

For counting the number of occurrences of each item in a list, I don't know the "standard idiomatic Python method" (i.e. I don't know what Guido would do :)), but this:
[php]
count = [(k,theList.count(k)) for k in set(theList)]
[/php]
will create a list of tuples, each tuple containing an item in theList and the number of occurrences.  E.g.
[php]
>>> theList = [10,11,10,7,8,7,5,9,9,3,8,6,9,5,10,7]
>>> [(k,theList.count(k)) for k in set(theList)]
[(3, 1), (5, 2), (6, 1), (7, 3), (8, 2), (9, 3), (10, 3), (11, 1)]
>>> 
[/php]
or you could just make a list of the counts, e.g.
[php]
>>> theList = [10,11,10,7,8,7,5,9,9,3,8,6,9,5,10,7]
>>> count = [ theList.count(k) for k in range(1,13) ]
>>> count
[0, 0, 1, 0, 2, 1, 3, 2, 3, 3, 1, 0]
>>> 
[/php]

---

### Post by Wybiral on 2008-04-09
> **stevescripts said:**
> Wybiral - the semi-colons are a bad habit?

Yeah, that's a pretty bad habit in Python. Interestingly enough, Javascript doesn't require semicolons either, but in Js it's a bad habit not to use them... Strange...

---

### Post by stevescripts on 2008-04-10
Wybiral,

TY! (on all counts ;) )

Steve

---

### Post by stevescripts on 2008-04-10
WW,

Thank you also!

Steve
(rather elegant, that bit of code)

---

### Post by nanotube on 2008-04-10
you could just generate it within your loop, as you are generating the throws, and stick them in a dict. 

if you don't actually need the raw data from your "theList" variable, and are only after the frequency, you can even forget about appending stuff to "theList" - and if you are doing a really large sample size, save yourself some ram. 

also, (again, not very important for small samples) technically you'd be saving yourself extra looping over the list that you are doing by generating the frequencies afterwards in a separate step.

so, 
```

def roll():
    return random.randrange(1,7)

def aThrow():
    return roll()+roll()  

histogram = {}.fromkeys(range(2,13), 0) # create blank histogram
for i in xrange(20000): # no need to use a while and have to manually increment a counter, when a for loop will do.
    result = aThrow() # no need for arguments, as per WW's post
    histogram[result] += 1 

# generate a halfway decent-looking numeric histogram:
for item in histogram.items():
    print item

# and an even better-looking x-histogram:
for item in histogram.items():
    print ( '%02d, %s' % (item[0], int(item[1]/100)*'X') )

```

and the resulting output:
```
(2, 528)
(3, 1071)
(4, 1691)
(5, 2282)
(6, 2745)
(7, 3373)
(8, 2850)
(9, 2217)
(10, 1624)
(11, 1072)
(12, 547)

02, XXXXX
03, XXXXXXXXXX
04, XXXXXXXXXXXXXXXX
05, XXXXXXXXXXXXXXXXXXXXXX
06, XXXXXXXXXXXXXXXXXXXXXXXXXXX
07, XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
08, XXXXXXXXXXXXXXXXXXXXXXXXXXXX
09, XXXXXXXXXXXXXXXXXXXXXX
10, XXXXXXXXXXXXXXXX
11, XXXXXXXXXX
12, XXXXX



```
so the most frequent one by far is the 7, and it is looking remarkably symmetric (both consistent with the laws of probability).

---

### Post by pmasiar on 2008-04-10
When writing Python, best is to start with [PEP 8](http://www.python.org/dev/peps/pep-0008/) - everybody else is using it. Including naming, your names are java-like.

See [http://learnpython.pbwiki.com/PythonTricks](http://learnpython.pbwiki.com/PythonTricks) - common mistakes beginners make. One not mentioned is, beginners are afraid to use dictionaries. Dicts are fast and use them whenever they fit! :-)

---

### Post by stevescripts on 2008-04-10
> **pmasiar said:**
> When writing Python, best is to start with [PEP 8](http://www.python.org/dev/peps/pep-0008/) - everybody else is using it. Including naming, your names are java-like.

See [http://learnpython.pbwiki.com/PythonTricks](http://learnpython.pbwiki.com/PythonTricks) - common mistakes beginners make. One not mentioned is, beginners are afraid to use dictionaries. Dicts are fast and use them whenever they fit! :-)

Many thanks to all - nanotube - really nice code - the info I have
gotten from all in this thread is exactly the type of stuff I am looking for.

pmasiar - Java like names?  Heaven forbid (I have done no java for
the last 5 years or so...) :)

I will definitely look at those links!

Thx again folks!

Steve

---

### Post by pmasiar on 2008-04-10
> **stevescripts said:**
> Java like names? 

like 'aList'. Maybe it comes from JavaScript then? Anyway, at least it is not Hungarian Notation :-)

Python naming standard is with underscore: 'a_list'. Of course many projects use 'aList' because it is 1 char shorter - and underscore makes you hit "shift" anyway... Pick any naming convention a stick to it.

---

### Post by stevescripts on 2008-04-10
> **pmasiar said:**
>  ... Anyway, at least it is not Hungarian Notation :-) ...


:lolflag:

Nice to know I am not alone concerning Hungarian Notation ...

pmasair - TY again for those links - very informative

Steve

---

