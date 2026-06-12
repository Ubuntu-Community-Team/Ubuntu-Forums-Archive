---
title: "Please criitique my Python code"
date: 2008-03-27
forum: Programming Talk
---

### Post by mssever on 2008-03-27
Just for fun, I decided to implement a Python prime numbers module based on the [sieve of Eratosthenes]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes"). (This isn't homework; I finished school several years ago.)

Given that: 1) I don't have a whole lot of programming experience, 2) I'm not very good at math, and 3) I don't know Python as well as I know some other languages; I'm sure that my code could be improved and that I could learn some valuable lessons from such improvements. So, I'm posting my module here. Ruthless criticism is encouraged. :)

[php]#!/usr/bin/env python

"""
This module contains functions for handling prime numbers.

All prime number operations are done by means of the Sieve
of Eratosthenes.

Functions:
    list_primes(upper_limit)
        Lists all primes up to a given limit
    
    is_prime(num)
        Tests whether a given integer is prime

    prime_factors(num)
        Returns a list of num's prime factors
"""

from math import sqrt

def list_primes(upper_limit):
    """
    This function implements the Sieve of Eratosthenes
    to find all prime numbers up to a given integer.

    Parameter:
        upper_limit: the highest integer to search.
        (raises ValueError if upper_limit < 2)

    Returns: a list of prime numbers
    """
    if upper_limit < 2:
        raise ValueError, "%d doesn't make sense as an upper limit!" % upper_limit
    loop_limit = sqrt(upper_limit)
    ints = range(2, upper_limit + 1)
    primes = []
    while len(ints) > 0:
        i = ints[0]
        primes.append(i)
        del ints[0]
        if i <= loop_limit:
            ints = [x for x in ints if x % i != 0]
    return primes

def is_prime(num):
    "Tests whether num is prime. Returns bool."
    return num in list_primes(num)

def prime_factors(num):
    "Returns a list of num's prime factors."
    if num != int(num):
        raise ValueError, "Can't find the prime factors of a non-integer."
    num = abs(num)
    try:
        primes = list_primes(int(sqrt(num)))
    except ValueError:
        # num must either be small or invalid
        if num == 1:
            return [num]
        primes = list_primes(num)
    factors = []
    for i in primes:
        # I use a while loop instead of an if statement because some
        # factors might occur more than once.
        while num % i == 0:
            factors.append(i)
            num /= i
        if num == 1:
            return factors
    factors.append(num)
    return factors


if __name__ == '__main__':
    from sys import argv
    number = int(argv[1])
    print 'Primes up to %d:' % number, list_primes(number)
    print '%d is prime:' % number, is_prime(number)
    print 'The prime factors of %d are:' % number, prime_factors(number)
[/php]

---

### Post by ruy_lopez on 2008-03-27
> **mssever said:**
> 1) I don't have a whole lot of programming experience, 2) I'm not very good at math, and 3) I don't know Python as well as I know some other languages; I'm sure that my code could be improved and that I could learn some valuable lessons from such improvements.

I'm not very good at Python, or Maths, either. I don't have any criticisms. Here's an extension which performs prime factorisation (basic algorithm):

[PHP]
def prime_factorise(number):
	tmp = number

	while tmp % 2 == 0:
		print 2, 'x',
		tmp = tmp / 2
	i = 3
	while i <= sqrt(tmp) + 1:
		if tmp % i == 0:
			print i, 'x',
			tmp = tmp / i
		else:
			i = i + 2
	if tmp > 1:
		print tmp, '=', number
[/PHP]

The only suggestion I can make to your code is to add some checks to "__main__"

[PHP]
if __name__ == '__main__':
    from sys import argv
    if 1 < len(argv) < 3: 
	 . . . do stuff . . .
    else:
	 print "usage: " + argv[0] + " prime_limit"
[/PHP]

---

### Post by Wybiral on 2008-03-27
It looks pretty good to me (I don't know much about the algorithm, but the Python code looks fine).

If you don't want to import the sqrt function, you can always use the inverse power, "upper_limit ** 0.5" (your way is more self-documenting, but using the "**" operator will be a little faster because it avoids a global name lookup). But that's really just a matter of preference, and the speedup wouldn't be too great (unless you were doing something that required millions of iterations).

---

### Post by mssever on 2008-03-27
> **Wybiral said:**
> you can always use the inverse power, "upper_limit ** 0.5"I'd forgotten that that works. I do have a vague recollection of using fractional exponents in algebra class. But I do think that math.sqrt is more readable. And it's only getting called once per function invocation.

---

### Post by mssever on 2008-03-27
Oh, I have one other question. In list_primes, I check for an out-of-bounds argument. In Ruby, I would raise ArgumentError if the argument was out of bounds, but I discovered that ArgumentError isn't one of Python's standard exceptions.

After playing with it a bit, I noticed that Python raises TypeError for the wrong number of arguments; so, in the absence of better information, I decided to follow suit and raise Type Error for out-of-bounds arguments. But I don't think that TypeError makes sense, since it really doesn't have anything to do with type.

What is the Pythonic way to handle this?

---

### Post by pmasiar on 2008-03-27
> **mssever said:**
> But I do think that math.sqrt is more readable. And it's only getting called once per function invocation.

Yes, it is more readable - and IIRC, target method is cached so it will be found even faster next time. There is no reason to trade  readability for speed - "There is one obvious way to do it right".

---

### Post by ghostdog74 on 2008-03-27
you can look at the Python library reference for the [various types of exceptions]("http://docs.python.org/lib/module-exceptions.html") and their meanings.

---

### Post by mssever on 2008-03-27
> **ghostdog74 said:**
> you can look at the Python library reference for the [various types of exceptions]("http://docs.python.org/lib/module-exceptions.html") and their meanings.

Thanks. Based on that link, it appears that ValueError is the proper exception.

---

### Post by Wybiral on 2008-03-27
> **pmasiar said:**
> Yes, it is more readable - and IIRC, target method is cached so it will be found even faster next time. There is no reason to trade  readability for speed - "There is one obvious way to do it right".

You would use:```

"%s blah %s" % (a, b)

```
Instead of:
```

a + " blah " + b

```
Because you know that the first one is faster even though the second one is a bit easier to read, right? It's one of those little trade-offs that makes sense to do.

I think it depends how much readability you're sacrificing and how much you need the speed. In this case, it's too trivial to matter, I just threw it in as a random fact. But if this were in a tight loop, where it might be called millions of times... Then it would matter, and it would be more acceptable to trade in some readability (as long as you make it clear what's going on and comment well).

Another solution that helps a little to speed up global function calls is to create a local instance (Guido gives an example of this [here]("http://www.python.org/doc/essays/list2str.html")). But the "**" operator is still going to be a bit faster.

In case you're curious, I've timed them all on Python 2.5 and they run in this order: "x ** 0.5", "local_sqrt(x)", "sqrt(x)", and "math.sqrt(x)".

---

### Post by mssever on 2008-03-27
> **Wybiral said:**
> Guido gives an example of this [here]("http://www.python.org/doc/essays/list2str.html")
Interesting read.

---

### Post by Siph0n on 2008-03-27
Does it matter that loop_limit = sqrt(upper_limit), returns a non-integer? Also, I never got this method... does it work for numbers like 15? Because the square root of 15 is 3.8, but 5 is prime and above that upper limit.... Can anyone explain that? Thx

edit : I tried your program on 15 and it works.... so im even more lost.... lol

---

### Post by mssever on 2008-03-27
> **Siph0n said:**
> Does it matter that loop_limit = sqrt(upper_limit), returns a non-integer? Also, I never got this method... does it work for numbers like 15? Because the square root of 15 is 3.8, but 5 is prime and above that upper limit.... Can anyone explain that? Thx

edit : I tried your program on 15 and it works.... so im even more lost.... lol

It doesn't matter. The algorithm deletes all multiples of the prime numbers it encounters from the list, so when it gets to the square root of the maximum value, there's no point in searching for multiples; all remaining numbers are prime. So a simple inequality is adequate here. We only need to know whether i > the square root.

---

### Post by mssever on 2008-03-28
I've added another function for your critiquing pleasure.  given that I designed the algorithm myself instead of getting the basic idea from Wikipedia, it can probably stand some improvement. I've edited the original post, but I'll paste it here, as well, for convenience.

[php]def prime_factors(num):
    "Returns a list of num's prime factors."
    if num != int(num):
        raise ValueError, "Can't find the prime factors of a non-integer."
    num = abs(num)
    try:
        primes = list_primes(num / 2)
    except ValueError:
        # num must either be small or invalid
        if num == 1:
            return [num]
        primes = list_primes(num)
    factors = []
    for i in primes:
        # I use a while loop instead of an if statement because some
        # factors might occur more than once.
        while num % i == 0:
            factors.append(i)
            num /= i
        if num == 1:
            return factors
    return [num] # If we get here, num must be prime[/php]In a previous iteration of the algorithm, i needed to sort the list before returning it, and I ran into a snag. some_list.sort() modifies the list in place, then it returns None. That breaks the following code: [php]return some_list.sort()[/php] forcing you to do the sort and the return on separate lines. I eventually found the documentation on this (it took me a while, because it wasn't where I expected it to be), and learned that this behavior is by design.

In Ruby, there are two sort methods. some_array.sort makes a copy of the array and returns it. some_array.sort! sorts the array in place and returns self. (A Ruby convention is that "dangerous" methods--those that modify self and/or operate by side effect--have names ending with an exclamation point.) This way, Ruby doesn't break chaining.

Is there similar functionality in Python?

Another question: I tried to use this module to solve [this Project Euler puzzle]("http://projecteuler.net/index.php?section=problems&id=3"). The puzzle is finding the largest prime factor of 600851475143. When I run my code, though, it needs to call range(2, (600851475143 / 2) + 1) which raises OverflowError. Is there a way in Python to be able to get ranges of big numbers? Ruby handles all that transparently. Even 2...600851475143 (Ruby's range syntax) works fine.

---

### Post by imdano on 2008-03-28
You might want to use ```
 if not isinstance(num, int):
``` instead of ```
if num != int(num)
```If num is a str or list (or any type that can't be cast to an int), Python will raise a ValueError when the cast is attempted, so your custom ValueError won't get raised (I think, didn't test it).

edit: Removed some stuff I said because I misread your post.

---

### Post by ruy_lopez on 2008-03-28
It locks up for even relatively small (prime number speaking) values (like 8193221, for instance, which my Palm does instantly).

Going through the primes in the list is wasteful. You have to list a whole load of primes, the majority of which won't be factors. The method I used yesterday checks odd numbers (there are no even primes, except 2). It also counts upwards, so if the number is composed of, say, (2 x 2 x 2 x 3 . . . 7), it'll never have to count above 7. Your method lists every prime up to (num / 2).

I'm no expert. I think the method I used yesterday was deeply flawed also. I'd be interested to hear a better way from someone.

Same as yesterday but returns a list:
[php]
def factor_primes (number):
	p = []
	
	# add error handling
	
	while number % 2 == 0:
		p.append(2)
		number = number / 2
	i = 3
	while i <= sqrt(number) + 1:
		if number % i == 0:
			p.append(i)
			number = number / i
		else:
			i = i + 2
	if number > 1:
		p.append(number)
	
	return p
[/php]

```

time ./primes.py 2147483646
[2, 3, 3, 7, 11, 31, 151, 331]

real    0m0.049s
user    0m0.032s
sys     0m0.020s
```

---

### Post by mssever on 2008-03-28
> **imdano said:**
> You might want to use ```
 if not isinstance(num, int):
``` instead of ```
if num != int(num)
```If num is a str or list (or any type that can't be cast to an int), Python will raise a ValueError when the cast is attempted, so your custom ValueError won't get raised (I think, didn't test it).
I wasn't aware of isinstance, but I don't think that it will consider 3.0 to be an int (though I haven't tested it). If int can't cast its input to an integer, then raising ValueError is what I expected. My custom ValueError is intended to catch cases where, say, 3.1 is passed in. If I can use duck typing instead of explicit types, that's ideal.
> **ruy_lopez said:**
> Going through the primes in the list is wasteful. You have to list a whole load of primes, the majority of which won't be factors. The method I used yesterday checks odd numbers (there are no even primes, except 2). It also counts upwards, so if the number is composed of, say, (2 x 2 x 2 x 3 . . . 7), it'll never have to count above 7. Your method lists every prime up to (num / 2).

I'm no expert. I think the method I used yesterday was deeply flawed also. I'd be interested to hear a better way from someone.
Yes, I'm not very good at math. I can't see how your function guarantees that it will only list *prime* factors, so I don't know that I can use it. In reality, I wrote my function before I did anything more than glance at yours. Given that my algorithm gets hit by OverflowError on sufficiently large errors, something's wrong.

---

### Post by ruy_lopez on 2008-03-28
> **mssever said:**
> I can't see how your function guarantees that it will only list *prime* factors, so I don't know that I can use it.

It *seems* to return prime factors. I haven't tested it thoroughly enough to say, with certainty, if it returns accurate prime factors every time.

I copied it from a C program years ago, and rewrote it for VisualCalc on the Palm.

[This]("http://mathworld.wolfram.com/DirectSearchFactorization.html") looks like the algorithm that the code uses.

---

### Post by ruy_lopez on 2008-03-28
This new version uses your seive of eratosthenes list_primes(number) to generate a list of primes. Each prime in the list is exhausted before moving onto the next one. This new version is *guaranteed* to return valid prime factors (assuming list_primes() does).

At first glance, it seems to return the same values as the previous algorithm.

[php]
def prime_fact (number):
    # no point trying primes above sqrt(number)
	primes = list_primes(int(sqrt(number)))
	p = []

	i = 0
	while i < len(primes):
		if number % primes[i] == 0:
			p.append(primes[i])
			number = number / primes[i]
		else:
			i += 1
	
	if number > 1:
		p.append(number)

	return p
[/php]

The other algorithms (eulers method, pollard's rho algorithm etc.) are all beyond my ken.

There's a performance hit:
```

./new_prime.py
[2, 2, 2, 2, 19, 32499583L]

real    0m1.182s
user    0m1.160s
sys     0m0.020s

./original_prime.py
[2, 2, 2, 2, 19, 32499583L]

real    0m0.068s
user    0m0.048s
sys     0m0.020s

```

I imagine this'll probably get worse, as the the number being factorised gets bigger.

---

### Post by pmasiar on 2008-03-28
> **Wybiral said:**
> You would use:```

"%s blah %s" % (a, b)

```
Instead of:
```

a + " blah " + b

```
Because you know that the first one is faster even though the second one is a bit easier to read, right? It's one of those little trade-offs that makes sense to do.

I prefer (1), if template string is long enough (and/or needs matching XML tags), and when I have more than 2-3 arguments of mixed/non-string type. So, almost always :-) 

If i have many arguments with longish names, I do:

```

"%s blah %s" % (
    a, b)

```

---

### Post by mssever on 2008-03-28
> **ruy_lopez said:**
> This new version uses your seive of eratosthenes list_primes(number) to generate a list of primes. Each prime in the list is exhausted before moving onto the next one. This new version is *guaranteed* to return valid prime factors (assuming list_primes() does).
Thanks. This approach is almost the same as mine. I changed my function to list the primes up to the square root, and changed two lines at the bottom: [php]def prime_factors(num):
    "Returns a list of num's prime factors."
    if num != int(num):
        raise ValueError, "Can't find the prime factors of a non-integer."
    num = abs(num)
    try:
        primes = list_primes(int(sqrt(num)))
    except ValueError:
        # num must either be small or invalid
        if num == 1:
            return [num]
        primes = list_primes(num)
    factors = []
    for i in primes:
        # I use a while loop instead of an if statement because some
        # factors might occur more than once.
        while num % i == 0:
            factors.append(i)
            num /= i
        if num == 1:
            return factors
    factors.append(num)
    return factors[/php]
I discovered this as I was preparing to prove that only listing up to the square root wouldn't work (because I'd tried that already). I was going to offer 106 as a number that would cause your function to fail. But it didn't fail. On closer inspection, I realized that I hadn't accounted for the fact that there can only be at most one prime factor above the square root, which is why your algorithm works. So I modified mine. (IMHO my loop is a little cleaner than yours, though I haven't profiled it for performance.)

With the modified function, I was able to factor the number that started it all: ```
>>> import primes
>>> primes.prime_factors(600851475143)
[71, 839, 1471, 6857]
``` Of course, this algorithm still suffers from the same problems as the last one. The only difference is that it can take larger numbers before blowing up.

---

### Post by ruy_lopez on 2008-03-28
> **mssever said:**
>  (IMHO my loop is a little cleaner than yours, though I haven't profiled it for performance.)

You're right [php]for i in primes:[/php] is more native to Python (something I cannot say about myself).

EDIT: actually, using list_primes() is pointless. The original algorithm is good. Because non-primes are themselves composed of smaller prime numbers, by the time the algorithm reaches a non-prime, it's component primes have already been factored out.

A simple list of odd numbers illustrates this fact:
```

2        Prime
3        Prime
5        Prime
7        Prime
9        Not Prime. Composed of 3 x 3. 3 is factored out above.
11      Prime
13      Prime
15      Not Prime. Composed of 3 x 5. 3 & 5 are both factored out above.
17      Prime
19      Prime
21      Not Prime. Composed of 3 x 7. 3 & 7 are both factored out above.

```

You get the idea. When counting upwards, the smaller primes decompose any larger non-prime that could conceivably upset the results. A non-prime consisting of smaller primes will never divide out cleanly after the smaller primes of which it consists have been factored out. Only prime factors will divide out cleanly.

That's how the original algorithm works. Adding a list of primes to the algorithm makes an already inefficient process even more inefficient.

---

