---
title: "[SOLVED] Sieve of Eratosthenes in Python"
date: 2008-07-03
forum: Programming Talk
---

### Post by Infinite Recursion on 2008-07-03
I have a basic function setup that generates a list of primes based on the Sieve of Eratosthenes algorithm (see the [wikipedia]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes") article), but it seems to me that it's running much too slowly.  I think it would help if I could implement it as a generator, but I'm not sure how I would do so.  Any help/suggestions would be much appreciated.

Here is the code I have so far:
```

def primes(n):
    """ Returns a list of all prime numbers up to and including the given value. 
    Uses the Sieve of Eratosthenes algorithm. """
    values = range(3, n + 1, 2)
    max = sqrt(n)
    for i in values:
        if i < max:
            for j in xrange(i * i, n + 1, i): 
                try:
                    values.remove(j)
                except ValueError:
                    pass
    values.insert(0, 2)
    return values

```

---

### Post by slavik on 2008-07-04
hmm, you do a generator, but that might not be very useful. most of the times, you want a list of primes ... but even if it's a small loop to ask for one prime, the loop code would still be shorter ...

this is also one of those things that would probably be faster in C.

of course, the better way would be to find a better algorithm first.

---

### Post by Def13b on 2008-07-04
First things first, I should point out that math makes my head hurt. So while i had a quick look on wikipedia I didn't make it past the first sentence.

Not sure why but if I call your function with either 9 or 25 the returned list includes those numbers,

ie
```

>>>test = primes(9)
>>>print test
[2, 3, 5, 7, 9] # 9 isn't prime

>>>test = primes(25)
>>>print test
[2, 3, 5, 7, 11, 13, 17, 19, 23, 25] # 25 isn't prime
```

Couldn't tell you why this is, doesn't happen for all numbers though possibly more then I saw.

I've only been learning python recently so have been on the lookout for things to practice on, as such I briefly gave project euler a go. I've not been using Python long enough to help with modifying your function to make it a generator but here's the generator I used for primes, hopefully it will give you some inspiration on how to use your function as a generator.

```
def isprime(x):
	'''checks if x is a prime, returns false if its not'''
	for i in range(3, int(x**0.5)+1, 2):
		if x % i == 0:
			return False
			break

def primes(n):
	'''Generates a iterator of primes upto and including n'''
	check = 2
	while check <= n:
		if isprime(check) != False:
			yield check
		if check == 2:
			check += 1
		else:
			check += 2
```

```
>>>test = primes(25)
>>>for i in test: print i
2 3 5 7 11 13 17 19
```

There is definately a speed boost to be gained, calling your function with 100000 took longer then 60secs (I stopped it there so not sure of final time), calling the generator took less then 1 second. It's then easy enough to append each item from the iterator into a list if needed.

I should also point out that I've in no way checked that the generator is accurate, so it's possible it's faster because it's wrong, hopefully someone with a better idea of math and python will provide more help for you.

---

### Post by ghostdog74 on 2008-07-04
you can look at [other implementations]("http://www.google.com.sg/search?hl=en&q=Python+sieve&btnG=Google+Search&meta=") and see how they are done.

---

### Post by myrtle1908 on 2008-07-04
Maybe ...

[PHP]
def primes(n): 
	if n==2: return [2]
	elif n<2: return []
	s=range(3,n+1,2)
	mroot = n ** 0.5
	half=(n+1)/2-1
	i=0
	m=3
	while m <= mroot:
		if s[i]:
			j=(m*m-3)/2
			s[j]=0
			while j<half:
				s[j]=0
				j+=m
		i=i+1
		m=2*i+3
	return [2]+[x for x in s if x]
[/PHP]

Stolen from here: [http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/366178](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/366178)

---

### Post by Infinite Recursion on 2008-07-04
> **Def13b said:**
> Not sure why but if I call your function with either 9 or 25 the returned list includes those numbers,

ie
```

>>>test = primes(9)
>>>print test
[2, 3, 5, 7, 9] # 9 isn't prime

>>>test = primes(25)
>>>print test
[2, 3, 5, 7, 11, 13, 17, 19, 23, 25] # 25 isn't prime
```

Couldn't tell you why this is, doesn't happen for all numbers though possibly more then I saw.


It seems like it was doing this for all perfect squares.  This is a result of having "if i < max:" instead of "if i <= max:".  Thanks for pointing that out.

I think I'm going to try to add values to the lists rather than removing them; see how that goes.  I have suspicions that Python is slow at removing items from lists, because it then shifts the following elements to the left.

---

### Post by ghostdog74 on 2008-07-04
> **Infinite Recursion said:**
> .  I have suspicions that Python is slow at removing items from lists,  
its faster to create another list.

---

### Post by CptPicard on 2008-07-04
This is a sort of "backwards-looking" implementation which lets you have an arbitrary length stream of primes. Memory consumption of course grows every time you call yield() but this is pretty quick because I just append() to the list.


```

from math import sqrt


def primes():
  i = 2
  primes = []

  def check(n):
    for p in primes:
      if p > sqrt(n):
	return True
      elif n % p == 0:
	return False
    return True

  while True:

    if check(i):
      primes.append(i)
      yield i

    i = i + 1


```

---

### Post by Infinite Recursion on 2008-07-04
Thanks for all of your help.  I've found a function that works much more quickly.  For any that are curious, here it is:

```

def primes(n):
    """ Returns a list of all prime numbers up to and including the given
    value.  Uses the Sieve of Eratosthenes algorithm. """
    li = [1] * (n + 1)
    max = sqrt(n)
    for i in xrange(2, n + 1):
        if li[i]:
            yield i
            if i <= max:
                for j in xrange(i * i, n + 1, i):
                    li[j] = 0

```

I did a quick test, and found that it generates all primes < 1,000,000 in just over .5s.  Much better than 10+ minutes (never actually let it finish), as the previous function was getting!

---

### Post by pmasiar on 2008-07-05
> **CptPicard said:**
> 
```

      if p > sqrt(n):

```

I bet this  will be faster
```

      if p*p > n:

```" :-)

---

### Post by slavik on 2008-07-05
> **pmasiar said:**
> I bet this  will be faster
```

      if p*p > n:

```" :-)
probably more accurate, too. :)

---

