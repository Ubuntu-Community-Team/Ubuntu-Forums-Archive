---
title: "Sieve of Eratosthenes in Python - Comments/Suggestions please"
date: 2008-04-04
forum: Programming Talk
---

### Post by Siph0n on 2008-04-04
I finally implemented the Sieve of Eratosthenes in Python! :) Comments/Suggestions are welcome!...

```

maxPrime = 2000000
primeRange = range(3,maxPrime,2)
primes = [2]
stop = 0

while True:
    # Find the Multiple to remove
    for i in primeRange:
        if i != -1:
            # Append that multiple to primes
            primes.append(i)
            multToRem = i
            break
    # Find where to start from in primeRange... this part could probably be
    # combined with the previous for loop
    for i in range(0,len(primeRange)):
        if primeRange[i] == multToRem:
            start = i
            break
    # Go through primeRange and remove all multiples of multToRem.
    # Also, use a step of multToRem to skip unneccesary numbers
    for i in range(start,len(primeRange),multToRem):
        primeRange[i] = -1
    stop += 1
    # Stop after you iterated maxPrime**0.5 because everything left after that
    # is prime
    if stop >= maxPrime**0.5:
        break
    
# Add the remaining numbers to prime. Again this is probably not efficient...
for i in range(int(maxPrime**0.5),len(primeRange)):
    if primeRange[i] != -1:
        primes.append(primeRange[i])

```

---

### Post by Can+~ on 2008-04-04
I once made a similar thing, but on my own, on python, when trying out the Genexps, xrange, set and lambda functions:

[PHP]def getPrimes(limit):
	notprime = lambda x: ((x if x%3 else 3) if x%5 else 5) if x%7 else 7 # this line sucks.
	
	primes = set(notprime(i) for i in xrange(1,limit,2))
	primes.add(2) # 2 perished :(.
	
	return primes[/PHP]

Some tips about your code:
-xrange if you're gonna iterate, please.
-**0.5 is equal to do **2 on the other side.
-No globals, avoid while (1), try to use a function.

To me:
-I should probably redo my getPrimes. :(

---

