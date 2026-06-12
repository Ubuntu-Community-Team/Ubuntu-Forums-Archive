---
title: "[SOLVED] &amp;lt;Python&amp;gt;Project Euler Problem 23"
date: 2008-07-29
forum: Programming Talk
---

### Post by spadewarrior on 2008-07-29
I've been trying this one for hours. I thought it was easy, apparently not. I can't get the correct answer and I can't see what's wrong with the code.

Here's the problem: [http://projecteuler.net/index.php?section=problems&id=23](http://projecteuler.net/index.php?section=problems&id=23) 

Here's my code:

[PHP]#Problem 23
#02 August 2002
#
#A perfect number is a number for which the sum of its proper divisors is exactly equal to the number. For example, the sum of the proper divisors 
#of 28 would be 1 + 2 + 4 + 7 + 14 = 28, which means that 28 is a perfect number.

#A number whose proper divisors are less than the number is called deficient and a number whose proper divisors exceed the number is called
#abun.

#As 12 is the smallest abun number, 1 + 2 + 3 + 4 + 6 = 16, the smallest number that can be written as the sum of two abun numbers is 24.
#By mathematical analysis, it can be shown that all integers greater than 28123 can be written as the sum of two abun numbers. However, this 
#upper limit cannot be reduced any further by analysis even though it is known that the greatest number that cannot be expressed as the sum of two
#abun numbers is less than this limit.

#Find the sum of all the positive integers which cannot be written as the sum of two abun numbers.

import psyco, time, sys
from sets import Set
from math import sqrt
psyco.full()

s= time.time()



def sumDiv(n): # get sum of divisors of n

	divisors = [1]
	
	i = 2
	
	while i < n:
		if n % i == 0:
			divisors.append(i)
		i+=1
		
	return sum(divisors)


	

maximum =20160 # numbers above this can always be written as the sum of two abundant numbers

n = 12

abun = []

sums =[]


print "Getting abundant numbers..."

while n <= maximum * 2:
	
	divs = sumDiv(n)
	
	if divs > n: #if number is abun
		d2n = n * 2
		if n not in abun:
			abun.append(n) # add to list of abun numbers
			sys.stdout.write('\r')
			sys.stdout.write(str(n))
			sys.stdout.flush()
		
		
		
		while d2n < maximum:
			if d2n not in sums:
				sums.append(d2n)
				sys.stdout.write('\r')
				sys.stdout.write(str(n))
				sys.stdout.flush()
		
			d2n += n
			
	if divs == n:
		n2 = n*2
		if n2 not in abun:
			abun.append(n2)
			sys.stdout.write('\r')
			sys.stdout.write(str(n))
			sys.stdout.flush()
		
		
	n+=1
	


print

abun.sort()


print "Finding sums of abun numbers..."

i = 0

abunLength = len(abun)
while i < len(abun):
	j = i+1
	sys.stdout.write('\r')
	sys.stdout.write("Calculating ")
	
	sys.stdout.write(str(i))
	sys.stdout.write(" of ")
	sys.stdout.write(str(abunLength))
	sys.stdout.flush() 
	
	
	same = abun[i] * 2
	
	#if same < maximum:
	sums.append(same)
	
	
	while j < len(abun):
		adjacents = abun[i] + abun[j]
		#if adjacents < maximum:
	
		sums.append(adjacents)
		
		j += 1
	i += 1
	
	

print # blank line


i = 0
print "Getting rid of duplicates..."
sums = list(set(sums)) # remove dupes
print "Sorting..."
sums.sort() # sort in order again

print "Finding numbers that can't be written as the sum of two abun numbers..."


i = 0

n = 1



notsum = []
total = 0
while n < maximum :
	if n not in sums:
		total += n 
		notsum.append(n)
	sys.stdout.write('\r')
	sys.stdout.write("Running total: ")
	sys.stdout.write(str(total))
	sys.stdout.flush()

	
	n+=1

print 
print total
print sums
print notsum
print "\n"
print "Answer: ", sum(notsum)
print "Time taken: ", time.time() - s[/PHP]

I'd be grateful for ideas. 


Thanks.

---

### Post by TreeFinger on 2008-07-29
> **spadewarrior said:**
> I've been trying this one for hours. I thought it was easy, apparently not. I can't get the correct answer and I can't see what's wrong with the code.

Here's the problem: [http://projecteuler.net/index.php?section=problems&id=23](http://projecteuler.net/index.php?section=problems&id=23) 

Here's my code:

[PHP]#Problem 23
#02 August 2002
#
#A perfect number is a number for which the sum of its proper divisors is exactly equal to the number. For example, the sum of the proper divisors 
#of 28 would be 1 + 2 + 4 + 7 + 14 = 28, which means that 28 is a perfect number.

#A number whose proper divisors are less than the number is called deficient and a number whose proper divisors exceed the number is called
#abun.

#As 12 is the smallest abun number, 1 + 2 + 3 + 4 + 6 = 16, the smallest number that can be written as the sum of two abun numbers is 24.
#By mathematical analysis, it can be shown that all integers greater than 28123 can be written as the sum of two abun numbers. However, this 
#upper limit cannot be reduced any further by analysis even though it is known that the greatest number that cannot be expressed as the sum of two
#abun numbers is less than this limit.

#Find the sum of all the positive integers which cannot be written as the sum of two abun numbers.

import psyco, time, sys
from sets import Set
from math import sqrt
psyco.full()

s= time.time()



def sumDiv(n): # get sum of divisors of n

	divisors = [1]
	
	i = 2
	
	while i < n:
		if n % i == 0:
			divisors.append(i)
		i+=1
		
	return sum(divisors)


	

maximum =20160 # numbers above this can always be written as the sum of two abundant numbers

n = 12

abun = []

sums =[]


print "Getting abundant numbers..."

while n <= maximum * 2:
	
	divs = sumDiv(n)
	
	if divs > n: #if number is abun
		d2n = n * 2
		if n not in abun:
			abun.append(n) # add to list of abun numbers
			sys.stdout.write('\r')
			sys.stdout.write(str(n))
			sys.stdout.flush()
		
		
		
		while d2n < maximum:
			if d2n not in sums:
				sums.append(d2n)
				sys.stdout.write('\r')
				sys.stdout.write(str(n))
				sys.stdout.flush()
		
			d2n += n
			
	if divs == n:
		n2 = n*2
		if n2 not in abun:
			abun.append(n2)
			sys.stdout.write('\r')
			sys.stdout.write(str(n))
			sys.stdout.flush()
		
		
	n+=1
	


print

abun.sort()


print "Finding sums of abun numbers..."

i = 0

abunLength = len(abun)
while i < len(abun):
	j = i+1
	sys.stdout.write('\r')
	sys.stdout.write("Calculating ")
	
	sys.stdout.write(str(i))
	sys.stdout.write(" of ")
	sys.stdout.write(str(abunLength))
	sys.stdout.flush() 
	
	
	same = abun[i] * 2
	
	#if same < maximum:
	sums.append(same)
	
	
	while j < len(abun):
		adjacents = abun[i] + abun[j]
		#if adjacents < maximum:
	
		sums.append(adjacents)
		
		j += 1
	i += 1
	
	

print # blank line


i = 0
print "Getting rid of duplicates..."
sums = list(set(sums)) # remove dupes
print "Sorting..."
sums.sort() # sort in order again

print "Finding numbers that can't be written as the sum of two abun numbers..."


i = 0

n = 1



notsum = []
total = 0
while n < maximum :
	if n not in sums:
		total += n 
		notsum.append(n)
	sys.stdout.write('\r')
	sys.stdout.write("Running total: ")
	sys.stdout.write(str(total))
	sys.stdout.flush()

	
	n+=1

print 
print total
print sums
print notsum
print "\n"
print "Answer: ", sum(notsum)
print "Time taken: ", time.time() - s[/PHP]

I'd be grateful for ideas. 


Thanks.

I'm not in the state of mind to really help you right now but I do have a suggestion for the following:

[php]



def sumDiv(n): # get sum of divisors of n

    divisors = [1]
    
    i = 2
    
    while i < n:
        if n % i == 0:
            divisors.append(i)
        i+=1
        
    return sum(divisors) 
[/php]

instead of using n use n / 2 + 1

6 is divisible by 3 but nothing greater than that is going to be divisible. May speed things up a bit.

Why do you do maximum * 2?

---

### Post by spadewarrior on 2008-07-30
You can safely ignore the '* 2' bit after maximum. I was experimenting (I think....)

Good call on n/2 + 1. I was using n/2 before and didn't think of that.

---

### Post by Lux Perpetua on 2008-07-30
Here's something that may or may not help you: the sum-of-divisors function S(x) is *multiplicative* in the following sense: if x and y are relatively prime (have no common prime factors), then S(xy) = S(x)S(y). 

Example: S(4) = 1 + 2 + 4 = 7
S(7) = 1 + 7 = 8
S(28) = 1 + 2 + 4 + 7 + 14 + 28 = 56 = 7*8 = S(4)S(7)

Good luck...

---

### Post by Lster on 2008-07-30
[PHP]
def sumDiv(n): # get sum of divisors of n

    divisors = [1]
    
    i = 2
    
    while i < n:
        if n % i == 0:
            divisors.append(i)
        i+=1
        
    return sum(divisors) [/PHP]

This function is very slow because it runs in O(n) time. You can go through numbers much faster with a function similar to:

[PHP]def sumfacs(n):
	t = 1
	s = int(n**0.5)
	i = 2
	while i <= s:
		if n%i == 0:
			if n != i*i: t += n/i
			t += i
		
		i += 1
	
	return t[/PHP]

This has O(&#8730;n) complexity.

I'm not quite sure what your algorithm does but I would suggest you use something along the lines of:

[LIST=1]
[*]Find all abundant numbers up to the limit provided. Store these in a set.
[*]Loop through every combination of two abundant number checking that their sum is less than the limit. If it is, store these in a set.
[*]Finally, loop through all natural numbers up to your limit, adding them to a total if they do not appear in the set.
[/LIST]

For speed, you might want to use arrays instead of sets. And the second point is quite slow - using that algorithm above, I managed to compute the right answer in ~11 seconds in Python. With an improved second stage, I can reduce computation time to under 3 seconds.

---

### Post by spadewarrior on 2008-07-30
Thanks for that!

---

### Post by Lux Perpetua on 2008-07-30
> **Lster said:**
> [PHP]
def sumDiv(n): # get sum of divisors of n

    divisors = [1]
    
    i = 2
    
    while i < n:
        if n % i == 0:
            divisors.append(i)
        i+=1
        
    return sum(divisors) [/PHP]

This function is very slow because it runs in O(n) time. You can go through numbers much faster with a function similar to:

[PHP]def sumfacs(n):
	t = 1
	s = int(n**0.5)
	i = 2
	while i <= s:
		if n%i == 0:
			if n != i*i: t += n/i
			t += i
		
		i += 1
	
	return t[/PHP]

This has O(&#8730;n) complexity.I'm pretty sure you can get close to O(1) using my observation above, although I haven't implemented it. I'm thinking along the lines of a sieve of Eratosthenes. The drawback is that to find the abundant numbers up to N, you'd need a table of size about N. But 28123 is a pretty modest upper limit.

---

### Post by Lster on 2008-07-30
I think I have an O(n&#8730;n) solution. I'll have a play around with it using the fact S is multiplicative for some conditions. :)

---

### Post by Lster on 2008-07-30
Possible spoiler ahead! This code will be deleted when this thread has run its due course to stop cheating.

This uses the identities Lux Perpetua wrote about above. It reduces runtime by half a second. The main bottleneck still exists though in the last loop. Anyone have any ideas?

[PHP]
#Code available on request.
[/PHP]

---

