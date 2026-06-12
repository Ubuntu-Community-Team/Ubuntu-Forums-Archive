---
title: "more memory for python script"
date: 2007-01-24
forum: Programming Talk
---

### Post by oldmanstan on 2007-01-24
i get a memory error from my python script, i think i probably just need to increase the amount of memory python is allowed to use (the loop runs fine for awhile before the error so it's not a bug in the code... i dont think)

how do i do this? i'm new to python, poked around on google and searched the forums but the word memory in the google searches sort of nets a whole lot of stuff that won't help

thanks

---

### Post by pmasiar on 2007-01-24
error message?

---

### Post by rekahsoft on 2007-01-24
code?

---

### Post by oldmanstan on 2007-01-24
sorry, i figured it was something simple how you can just change the amount allocated to a php script in a config file for php, here's the error, it includes the line it's trying to run...

```
Traceback (most recent call last):
  File "primes.py", line 93, in ?
    findmersenne_num(int(sys.argv[2]), int(sys.argv[3]))
  File "primes.py", line 73, in findmersenne_num
    if checkifprime(m):
  File "primes.py", line 6, in checkifprime
    for a in range(2,int(testnum**.5)+1):
MemoryError
```

---

### Post by pmasiar on 2007-01-24
> **oldmanstan said:**
> sorry, i figured it was something simple how you can just change the amount allocated to a php script in a config file for php, here's the error, it includes the line it's trying to run...

```
Traceback (most recent call last):
  File "primes.py", line 93, in ?
    findmersenne_num(int(sys.argv[2]), int(sys.argv[3]))
  File "primes.py", line 73, in findmersenne_num
    if checkifprime(m):
  File "primes.py", line 6, in checkifprime
    for a in range(2,int(testnum**.5)+1):
MemoryError
```

1) How big is the testnum? range() generates whole list. You may want to use xrange() which creates iterator (avoids creating huge list used for your loop only

2) Python takes all the memory it needs. Can you simplify expressions - assign them to variables so you will see which part of the expression fails?

---

### Post by oldmanstan on 2007-01-24
testnum shouldn't actually be all that large at this point (not greater than 61) but after it checks testnum it checks 2^testnum-1 so maybe that's the problem 

i used xrange and now it seems to run, i'm still waiting for it to finish but it is much futher along than when it threw the error so apparently problem solved (at least partially, might still error out)

also i'm watching python in top and so far it hasn't snagged more than about 2.5 MB, which is actually sort of odd but i guess if an iterator takes up quite a bit less memory than a full list that makes sense

thanks for the advice!

---

### Post by jblebrun on 2007-01-24
> **oldmanstan said:**
> testnum shouldn't actually be all that large at this point (not greater than 61) but after it checks testnum it checks 2^testnum-1 so maybe that's the problem 

i used xrange and now it seems to run, i'm still waiting for it to finish but it is much futher along than when it threw the error so apparently problem solved (at least partially, might still error out)

also i'm watching python in top and so far it hasn't snagged more than about 2.5 MB, which is actually sort of odd but i guess if an iterator takes up quite a bit less memory than a full list that makes sense

thanks for the advice!

Would you be willing to let us see your code?

---

### Post by oldmanstan on 2007-01-24
> **jblebrun said:**
> Would you be willing to let us see your code?

sure, keep in mind that a) it isn't really that good, there are probably better ways to do things and b) i'm not a programmer and it's just for craps and giggles :)

that said, i'm brand new to python (i've coded in quite a few other languages but never "serious" applications and, as i said, never professionally) and it seems to be a neat language so any other pointers you feel inclined to offer will be gladly accepted

here is the whole script, though only 2 of the functions (well, one function and one procedure i guess) are being used when i get that error message (which seems to be fixed, seems)

```
import math
import sys

def checkifprime(testnum):
	"""checks if testnum is prime, returns 1 if yes, 0 if no"""
	for a in xrange(2,int(testnum**.5)+1):
		if testnum % a == 0:
			return 0
	return 1

def findprimes_range(start, end):
	"""finds all primes in a range given by start and end"""
	if start >= end:
		return 0
	if start < 3:
		print 2
		start = 3
		if start >= end:
			return 0
	for a in range(start, end):
		if checkifprime(a):
			print a
	return 1

def findprimes_num(start, num):
	"""finds next num primes greater than or equal to start"""
	a = 0 #our counter
	if num < 1:
		return 0
	if start < 3:
		print 2
		start = 3
		a = 1 #since we already have 1 prime
	while a < num:
		if checkifprime(start):
			print start
			a = a + 1
		start = start + 1
	return 1

def findmersenne_range(start, end):
	"""finds all mersenne primes m=2^p-1 where p is prime between start and end"""
	if start >= end:
		return 0

	pstart = math.log(start+1, 2) #cycle through exponents for more speed
	pstart = int( math.ceil(p) )

	pend = math.log(end+1, 2)
	pend = int( math.ceil(p) )

	for a in range(pstart, pend):
		if checkifprime(a):
			m = x**p - 1
			if checkifprime(m):
				print m
	return 1

def findmersenne_num(start, num):
	"""finds num mersenne primes m=2^p-1 where p is prime greater than or equal to start"""
	a = 0 #counter
	if num < 1:
		return 0
	if start < 3:
		start = 3
	
	p = math.log(start+1, 2) #cycle through exponents for more speed
	p = int( math.ceil(p) )

	while a < num:
		if checkifprime(p):
			m = 2**p - 1
			if checkifprime(m):
				print m
				a = a + 1
		p = p + 1

def print_help():
	print """primes.py - by George Lesica
usage: primes.py <PMpm> <start> <end | number>
options:
	P - search for primes in a range <start> to <end>
	M - search for mersenne primes in a range <start> to <end>
	p - find <number> primes greater than or equal to <start>
	m - find <number> mersenne primes greater to or equal to <start>"""

if len(sys.argv) == 4:
	if sys.argv[1] == 'P':
		findprimes_range(int(sys.argv[2]), int(sys.argv[3]))
	elif sys.argv[1] == 'M':
		findmersenne_range(int(sys.argv[2]), int(sys.argv[3]))
	elif sys.argv[1] == 'm':
		findmersenne_num(int(sys.argv[2]), int(sys.argv[3]))
	elif sys.argv[1] == 'p':
		findprimes_num(int(sys.argv[2]), int(sys.argv[3]))
	else:
		print_help()
else:
	print_help()
```


EDIT: might be useful to know what i fed it when it choked: ```
$ python primes.y m 0 9
```

it choked after the 8th number in the mersenne set (which makes sense since after 8 they really start to blow up)

EDIT: success! it just finished the 9th number and quit just like it's sposed to, apparently xrange fixed the problem, thank you very much! still feel free to suggest other things if you want though, i have no problems with constructive criticism

---

### Post by pmasiar on 2007-01-24
> **oldmanstan said:**
> sure, keep in mind that a) it isn't really that good, there are probably better ways to do things and b) i'm not a programmer and it's just for craps and giggles :)

that said, i'm brand new to python (i've coded in quite a few other languages but never "serious" applications and, as i said, never professionally) and it seems to be a neat language so any other pointers you feel inclined to offer will be gladly accepted

That's exactly why I suggest Python for beginners: is forgiving, "obvious" solution is the right one, it does not require the all-out dedication and learning it's quirks like other "more serious" languages.

BTW range() will be same thing as xrange() in one of future versions of Python - or even better IIUC list generators will be silently converted to iterators behind the sceen somehow.

---

### Post by pmasiar on 2007-01-24
> **oldmanstan said:**
> success! it just finished the 9th number and quit just like it's sposed to, apparently xrange fixed the problem, thank you very much! still feel free to suggest other things if you want though, i have no problems with constructive criticism

See? many of our C lovers here in forum will argue that computing primes in python is abomination - C is "right" language to do it. Well, how long it took (for a green beginner) to write this program? In C calculation would be faster - maybe saving 15 minutes of computing time, by investing couple hours of programmers time for this one-off task.

---

### Post by jblebrun on 2007-01-24
> **pmasiar said:**
> See? many of our C lovers here in forum will argue that computing primes in python is abomination - C is "right" language to do it. Well, how long it took (for a green beginner) to write this program? In C calculation would be faster - maybe saving 15 minutes of computing time, by investing couple hours of programmers time for this one-off task.

well, yeah, until you want to find the 1,000,000th mersenne prime ;-)

---

