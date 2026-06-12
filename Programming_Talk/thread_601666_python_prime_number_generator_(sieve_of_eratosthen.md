---
title: "python prime number generator (sieve of eratosthenes)"
date: 2007-11-03
forum: Programming Talk
---

### Post by mrpeenut24 on 2007-11-03
I'm trying to implement the [Sieve of Eratosthenes]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes") in python.  (I've seen that it's already been implemented using yield, however, I'd like to try it with simple lists.)  And here's what I have so far:

```

#!/usr/bin/python

from math import sqrt

#initialize an empty list that will store every number up to 
#limit at first then delete the numbers that aren't prime
primes = [] 

#generate primes up to this number
limit = 30

#append all numbers up to limit into primes
##there has to be a faster way...
for i in xrange(2,limit+1):
    primes.append(i)

#reset i to use later
i = 0
  

#start at beginning of primes := 2
## so long as this entry in primes is less than the square
## root of limit, check if it's divisible by anything else in the list
[COLOR=Red]## i believe the problem lies in not resetting i?[/COLOR]
while primes[i] < sqrt(limit):
    for j in xrange(i, len(primes)):
        if not primes[j] == primes[i]:
            if primes[j] % primes[i] == 0:

               ## print out i & primes[i] and j & primes[j] 
                print "[",i,"]",primes[i]," xx  [",j,"]",primes[j]

               # j is divisible by i, remove it
              [COLOR=Red] ## with this line not in place, everything prints out correctly above
               ## however, with it here, it messes up, keeping i and primes[j] == 0[/COLOR]
                #primes.remove(j)
    i = i + 1

```You may have to run the script to see what it does, but I'm not sure what the problem is.  Without that primes.remove(j) line, everything works fine, however, when I add it, it messes everything up.  I'm assuming it shrinks the list, which I'm counting on happening, but I think that's what's causing the problem.  Anyone see what I'm missing?

---

### Post by smartbei on 2007-11-03
What you are doing is shortening the list. Say you ha da list with five elements:
```

l=[1,2,3,4,5]

```
l[3] = 4 right?

What happens when you l.remove(2): l[3]=5

If you were looping over the list, you would have skipped over the value 5 entirely.

See [http://ubuntuforums.org/showthread.php?t=595784](http://ubuntuforums.org/showthread.php?t=595784) for a recent thread about using the Sieve of Eratosthenes. See the OP's code or my (farther down) code for reference.

By the way, why are you bothering to append all the numbers into the list primes? after all, if primes[i]=i+2, why not just use i?

---

### Post by Lux Perpetua on 2007-11-03
> **mrpeenut24 said:**
> I'm trying to implement the [Sieve of Eratosthenes]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes") in python.  (I've seen that it's already been implemented using yield, however, I'd like to try it with simple lists.)  And here's what I have so far:

```

#!/usr/bin/python

from math import sqrt

#initialize an empty list that will store every number up to 
#limit at first then delete the numbers that aren't prime
primes = [] 

#generate primes up to this number
limit = 30

#append all numbers up to limit into primes
##there has to be a faster way...
for i in xrange(2,limit+1):
    primes.append(i)

#reset i to use later
i = 0
  

#start at beginning of primes := 2
## so long as this entry in primes is less than the square
## root of limit, check if it's divisible by anything else in the list
[COLOR=Red]## i believe the problem lies in not resetting i?[/COLOR]
while primes[i] < sqrt(limit):
    for j in xrange(i, len(primes)):
        if not primes[j] == primes[i]:
            if primes[j] % primes[i] == 0:

               ## print out i & primes[i] and j & primes[j] 
                print "[",i,"]",primes[i]," xx  [",j,"]",primes[j]

               # j is divisible by i, remove it
              [COLOR=Red] ## with this line not in place, everything prints out correctly above
               ## however, with it here, it messes up, keeping i and primes[j] == 0[/COLOR]
                #primes.remove(j)
    i = i + 1

```You may have to run the script to see what it does, but I'm not sure what the problem is.  Without that primes.remove(j) line, everything works fine, however, when I add it, it messes everything up.  I'm assuming it shrinks the list, which I'm counting on happening, but I think that's what's causing the problem.  Anyone see what I'm missing?There are quite a few bugs here. 

1. You probably meant del primes[j], not primes.remove(j). 
2. The list in a for statement is only evaluated once, so you are shrinking your list while iterating up to the original length of the list. 
3. There is at least one more bug. (Hint: after you think your program is working, set limit to 25 and see if it still works.)

---

