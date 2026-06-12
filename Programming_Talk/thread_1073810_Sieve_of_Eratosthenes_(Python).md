---
title: "Sieve of Eratosthenes (Python)"
date: 2009-02-18
forum: Programming Talk
---

### Post by UnWeave on 2009-02-18
Okay, I feel I should preface this by saying I am new to Python.  In fact, I am new to programming in general.  Anyway, I've been going through some of the problems on projecteuler.net, which has led to me trying to create algorithm for the sieve of eratosthenes.  Basically, my code is as follows:

```

import math
import time

def primes_to_n(n):    #Function to find all primes between 2 and n
	list = []       #Create an empty list
	position = 1    #The inital starting position in the list is 1
	for x in range(2, n+1):           #This adds odd numbers up to n to the list
		if x % 2 != 0 or x == 2:  #it also adds the number two, since this is prime
			list.append(x)
	while list[position] <= math.sqrt(n):  #If the number at the current position in the list
		for y in list:                 #is less than sqrt(n), then all numbers in the list
			if y > list[position]: #that divide by the number at the current position
				if y % list[position] == 0:  #and are greater than it, should be removed
					list.remove(y)
		position += 1  #We now move to the next number in the list
	print list
	print '\nThere are ',len(list),' primes between 2 and ',n,'.'
		
primes_to_n(input('Give primes up to: '))

print time.clock()

```

(Sorry if that is a little difficult to read, copying and pasting it all in didn't work out too well) 
And it's extremely slow.  The way I actually solved the problem that lead to me finding out about this method was basically a heavily-optimized brute-force method, and it is far quicker than this method for ~ n > 1000.  I've seen examples of sieves that work far more quickly than this, though the only ones I have seen simply list the number of primes. I'd like to know what it is about this code that makes it particularly slow, if anyone can explain it in semi-layman's terms that would be great.

Thanks.

---

### Post by PythonPower on 2009-02-18
Something simple like this? primes() gives you an iterator and primesArray() an array. The computional complexity of both is the same; so is the memory complexity.

[PHP]

def primes(n):
	sieve = [True]*(n+1)
	for i in range(2, n+1):
		if sieve[i]:
			yield i
			for j in range(2*i, n+1, i): sieve[j] = False

def primesArray(n):
    return [p for p in primes(n)]

for p in primes(100): print(p)
print(primesArray(10))
	
[/PHP]

---

### Post by UnWeave on 2009-02-20
Yeah, that's similar to the sort of thing I've seen before, but I don't fully understand it. For one, I haven't yet met 'yield'. I looked it up, but I'm still not entirely sure what it does.

Also, what I really wanted to know was why my version is so slow, but thanks anyway.

---

### Post by gil_johnson on 2009-08-22
UnWeave,
I am new to Python as well, although I have been a 'hobby' programmer for
some time. I am learning Python 3.0 so I made some changes to you code -
mainly 'print' statements have been replaced by the 'print()' function. I
think this is available in Python 2.6, so this should run on your system.
I changed the 'input' function so you can enter arithmetical expressions
such as 2**20, and your name 'list' to 'init_list' since 'list()' is a
Python function. The listing is at the end of this note.

I added timers around your two loops, and the result was:

    Give primes up to: 100000
[B]    'for' loop: 0.0450949668884        (seconds)
    'while' loop: 16.133852005         (seconds)[/B]
    [2, 3, 5, 7, ... 99989, 99991]
    There are 9592 primes between 2 and 100000.

From that you can see that virtually all of your time is spent in the
'while' loop. Most of that is stepping through the list, checking:

    if y > list[position]:
        if y % list[position] == 0:
            list.remove(y)

'y' is checked every pass through the loop, even if 'y - 1' was found to be
greater than initial_list[position], and the modulo and remove operations
are slow.

You are better off zeroing the multiples of 'prime' in place, not removing
them. Starting at 'position = 1' if 'init_list[position]' is not zero, it's
prime, and the multiples of 'init_list[position]' occur at steps of 'prime'
into your list. If this description doesn't make sense, test this on paper,
or there are lots of demonstrations of the classic sieve online, including
wikipedia, where you can see this.

Results with the new version:

    Give primes up to: 100000
    'for' loop: 0.0103569030762
    'while' loop: 0.0326659679413
    [2, 3, 5, 7, ...  99989, 99991]
    There are 9592 primes between 2 and 100000.

    Give primes up to: 10000000
    'for' loop: 0.918962001801
    'while' loop: 3.53711295128
    There are 664579 primes between 2 and 10000000.
    [2, 3, 5, 7, ... 9999971, 9999973, 9999991]

You can save a tiny bit of time by taking the 'if' line out of the 'for'
loop, putting the special case of 2 in your initialization code, and
changing your 'range()' arguments to go by steps of 2. This avoids the
modulo operation and the two tests in each cycle of the loop.

This isn't an optimized program. I tried to stick to your organization
where possible. There are more optimizations possible, and there are more
compact ways to store the primes. There are a LOT of versions online. I
just tried to demonstrate the importance of timers, and keeping as many
operations as possible outside the loops.

The new version:

```
import math
import time

def primes_to_n(n):
         init_list = [2]               # Create a list with 2 as a special case
         position = 1

            for_timer0 = time.time()                           # start 'for' timer
    
            for x in range(3, n + 1, 2):           # This adds odd numbers up to n
                        init_list.append(x)

            print('\nfor loop:', time.time() - for_timer0)       # end 'for' timer

            while_timer0 = time.time()                       # start 'while' timer

            while init_list[position] <= math.sqrt(n):
                        if init_list[position]:                                                                                                  # Start at position 1, if
                                    prime = init_list[position]                                                                  # it isn't 0, it's prime
                                    x_off = position + prime                                                                    # First multiple,
                                    while x_off < len(init_list):
                                                init_list[x_off] = 0            # cross it off,
                                                x_off += prime                  # next multiple.
                        position += 1

            final_list = []
                for y in range(len(init_list)):                  # Transfer primes to a
                                if init_list[y]:                             # list without zeroes.
                                            final_list.append(init_list[y])

            print('while loop:', time.time() - while_timer0)   #  end 'while' timer
             print('There are', len(final_list),'primes between 2 and', n, end = '.\n')
             print(final_list)

limit = eval(input('Give primes up to: '))
primes_to_n(limit)

gil_johnson
```

---

### Post by Lux Perpetua on 2009-08-23
> **UnWeave said:**
> Okay, I feel I should preface this by saying I am new to Python.  In fact, I am new to programming in general.  Anyway, I've been going through some of the problems on projecteuler.net, which has led to me trying to create algorithm for the sieve of eratosthenes.  Basically, my code is as follows:

```

import math
import time

def primes_to_n(n):    #Function to find all primes between 2 and n
	list = []       #Create an empty list
	position = 1    #The inital starting position in the list is 1
	for x in range(2, n+1):           #This adds odd numbers up to n to the list
		if x % 2 != 0 or x == 2:  #it also adds the number two, since this is prime
			list.append(x)
	while list[position] <= math.sqrt(n):  #If the number at the current position in the list
		for y in list:                 #is less than sqrt(n), then all numbers in the list
			if y > list[position]: #that divide by the number at the current position
				if y % list[position] == 0:  #and are greater than it, should be removed
					list.remove(y)
		position += 1  #We now move to the next number in the list
	print list
	print '\nThere are ',len(list),' primes between 2 and ',n,'.'
		
primes_to_n(input('Give primes up to: '))

print time.clock()

```

(Sorry if that is a little difficult to read, copying and pasting it all in didn't work out too well) 
And it's extremely slow.  The way I actually solved the problem that lead to me finding out about this method was basically a heavily-optimized brute-force method, and it is far quicker than this method for ~ n > 1000.  I've seen examples of sieves that work far more quickly than this, though the only ones I have seen simply list the number of primes. I'd like to know what it is about this code that makes it particularly slow, if anyone can explain it in semi-layman's terms that would be great.

Thanks.It would help if you implemented the correct algorithm. ;) The sieve of Eratosthenes is what PythonPower posted; your algorithm is a variant of repeated *trial division*. The amount of work the sieve of Eratosthenes does to find all the primes up to n is close to linear in n, since it visits each number once for each of its prime factors, and the number of prime factors of a number is small compared to the number itself. (The true order of the running time is actually worse than n but better than n*log(n); you can make it truly order n by modifying the algorithm a bit). 

In your code, on the other hand, for each y, you compute y % p for all primes p less than or equal to the smallest prime factor of y; the number of such primes need not be much smaller than y, and may be as large as roughly y/log(y). To make matters worse, each time you discover a composite number, you have to do a deletion from your list, which is on average a pretty expensive operation.

---

### Post by UnWeave on 2009-08-23
> **gil_johnson said:**
> UnWeave,
I am new to Python as well, although I have been a 'hobby' programmer for
some time. I am learning Python 3.0.

...

The new version:

```
import math
import time

def primes_to_n(n):
         init_list = [2]               # Create a list with 2 as a special case
         position = 1

            for_timer0 = time.time()                           # start 'for' timer
    
            for x in range(3, n + 1, 2):           # This adds odd numbers up to n
                        init_list.append(x)

            print('\nfor loop:', time.time() - for_timer0)       # end 'for' timer

            while_timer0 = time.time()                       # start 'while' timer

            while init_list[position] <= math.sqrt(n):
                        if init_list[position]:                                                                                                  # Start at position 1, if
                                    prime = init_list[position]                                                                  # it isn't 0, it's prime
                                    x_off = position + prime                                                                    # First multiple,
                                    while x_off < len(init_list):
                                                init_list[x_off] = 0            # cross it off,
                                                x_off += prime                  # next multiple.
                        position += 1

            final_list = []
                for y in range(len(init_list)):                  # Transfer primes to a
                                if init_list[y]:                             # list without zeroes.
                                            final_list.append(init_list[y])

            print('while loop:', time.time() - while_timer0)   #  end 'while' timer
             print('There are', len(final_list),'primes between 2 and', n, end = '.\n')
             print(final_list)

limit = eval(input('Give primes up to: '))
primes_to_n(limit)

gil_johnson
```

Thanks! Regarding your PM, I had sort of given up on this particular problem, and in fact have not done any coding for a few months now, but I am still interested.  This is exactly the sort of explanation I needed, so again, thank you very much.

@Lux: Your explanation is also appreciated, though I'd be lying if I said I fully understood all of what you said. For the most part, though, I did understand what you were saying, so thanks to you, too.

---

