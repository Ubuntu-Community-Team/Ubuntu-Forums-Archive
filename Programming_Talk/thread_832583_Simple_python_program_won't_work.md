---
title: "Simple python program won't work"
date: 2008-06-17
forum: Programming Talk
---

### Post by DanielJackins on 2008-06-17
So doing project Euler I've found already a few problems need generation of prime numbers. While this was unnecessary, I thought I would attempt to make a function to perform this task for me (more for practice than usefulness, as I have trouble understanding parameters in functions):

[php]
def primeCheck(num):
	import math
	prime = 1
	i = 3
	while i <= math.sqrt(num):
		prime = 1
		if num%i == 0:
			prime = 0
		i = i + 2
		if prime == 0:
			print num, 'is not prime'
		elif prime == 1:
			print num, 'is prime'
			
num1 = raw_input('What number would you like to check as a prime? ')		
primeCheck(num1)
[/php]

When I attempt to run this program and give it the number to check, it gives me these errors:

What number would you like to check as a prime? 5
Traceback (most recent call last):
  File "primes.py", line 16, in <module>
    primeCheck(num1)
  File "primes.py", line 5, in primeCheck
    while i <= math.sqrt(num):
TypeError: a float is required


Can anybody see my problem? Thanks

---

### Post by LaRoza on 2008-06-17
[php]
def primeCheck(num):
	import math
	prime = 1
	i = 3
	while i <= math.sqrt(num):
		prime = 1
		if num%i == 0:
			prime = 0
		i = i + 2
		if prime == 0:
			print num, 'is not prime'
		elif prime == 1:
			print num, 'is prime'
			
num1 = float(raw_input('What number would you like to check as a prime? '))		
primeCheck(num1)
[/php]

raw_input() returns a string. You have to conver it to a float (Python is strongly typed).

---

### Post by tamoneya on 2008-06-17
also you need to look at your program flow a fair amount.  the place where you check the value of prime and then print whether it is prime or not should be outside of the for loop.  Also have you considered the value of 2.  2 is considered a prime but your program will return that it isnt prime.  Ill let you try it again to restructure the flow but if you cant get it I will post a solution.

---

### Post by iXombie on 2008-06-17
by doing a raw_input you are sending a string change num to an intiger

i love Project Euler it was the best help i've had for python.

---

### Post by DanielJackins on 2008-06-17
Thanks for the quick replies :)

Okay, so I understand what you're saying about the strings Laroza, so thank you for that.

So I changed it a bit:

[php]
def primeCheck(num):
	import math
	prime = 1
	i = 3
	if num == 2:
		i = num + 1
	while i <= math.sqrt(num):
		prime = 1
		if num%i == 0:
			prime = 0
		i = i + 2
		if prime == 0:
			print num, 'is not prime'
		elif prime == 1:
			print num, 'is prime'
			
num1 = int(raw_input('What number would you like to check as a prime? '))		
primeCheck(num1)
[/php]

So I'd guess that would solve the problem of 2 being prime, at least I think. Other than that, I don't see how to restructure it. I *can* see that there are problems, as if I put in something like 1000:
```

What number would you like to check as a prime? 1000
1000 is prime
1000 is not prime
1000 is prime
1000 is prime
1000 is prime
1000 is prime
1000 is prime
1000 is prime
1000 is prime
1000 is prime
1000 is prime
1000 is not prime
1000 is prime
1000 is prime
1000 is prime

```

---

### Post by iXombie on 2008-06-17
are you meaning to print i and not num?

---

### Post by tamoneya on 2008-06-17
the sections that check the value of "prime" need to be moved outside of the while loop.  Each time it goes through it prints whether it was divisible by the last odd number it checked.  If you look you notice that it called it not prime twice.  These occurances are when i = 5 or 25.  Since I dont want to ruin the challenge for you I will give you some psuedocode.
```
set prime to "true" or 1
check divisibility by 2
start loop up to sqrt(num):
     check divisibility by odd numbers starting at three
     if divisibile set prime to false/0
     if not divisible leave prime alone and check another number
end loop
check value of prime and print result
```

---

### Post by ConMan318 on 2008-06-18
> **tamoneya said:**
> 
```
set prime to "true" or 1
check divisibility by 2
start loop up to sqrt(num):
     check divisibility by odd numbers starting at three
     if divisibile set prime to false/0
     if not divisible leave prime alone and check another number
end loop
check value of prime and print result
```

I would return False immediately if a divisor is found, rather than using a flag value.  Especially in Project Euler, where you are often required to generate large amounts of primes and/or check if very large numbers are prime.

```

check divisibility by 2
    return False if divisble
start loop up to sqrt(num):
     check divisibility by odd numbers starting at three
     if divisibile return False
end loop
return True
```

Not really a big difference as far as the coding goes, but it will noticeably decrease runtime on many of the Euler problems.

---

### Post by tamoneya on 2008-06-18
> **ConMan318 said:**
> I would return False immediately if a divisor is found, rather than using a flag value.  Especially in Project Euler, where you are often required to generate large amounts of primes and/or check if very large numbers are prime.

```

check divisibility by 2
    return False if divisble
start loop up to sqrt(num):
     check divisibility by odd numbers starting at three
     if divisibile return False
end loop
return True
```

Not really a big difference as far as the coding goes, but it will noticeably decrease runtime on many of the Euler problems.

I wasnt familar with project Euler myself and I was trying to keep the psuedocode straight forward.  Putting the a return in the loop may be causing some confusion as it is since the first code is trying to do something of that nature.  If you really wanted to be efficient you would not check every odd number but instead make an array of every odd number and then use a Sieve of Eratosthenes or an Elliptic Curve.
[http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes](http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)
[http://en.wikipedia.org/wiki/Elliptic_curve_primality_test](http://en.wikipedia.org/wiki/Elliptic_curve_primality_test)

---

