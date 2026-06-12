---
title: "[Python] Project Euler problem 23"
date: 2008-11-08
forum: Programming Talk
---

### Post by DanielJackins on 2008-11-08
So I am rather new to Python and programming as a whole, and have been trying to solve [problem 23](http://projecteuler.net/index.php?section=problems&id=23) on project euler;

A perfect number is a number for which the sum of its proper divisors is exactly equal to the number. For example, the sum of the proper divisors of 28 would be 1 + 2 + 4 + 7 + 14 = 28, which means that 28 is a perfect number.

A number whose proper divisors are less than the number is called deficient and a number whose proper divisors exceed the number is called abundant.

As 12 is the smallest abundant number, 1 + 2 + 3 + 4 + 6 = 16, the smallest number that can be written as the sum of two abundant numbers is 24. By mathematical analysis, it can be shown that all integers greater than 28123 can be written as the sum of two abundant numbers. However, this upper limit cannot be reduced any further by analysis even though it is known that the greatest number that cannot be expressed as the sum of two abundant numbers is less than this limit.

Find the sum of all the positive integers which cannot be written as the sum of two abundant numbers.



Here is my code so far (which works, but is rather slow :P):

abundantfunction.py
```
def abundant(limit):
	abList = []
	num = 1
	abCheck = 1
	abSum = 0
	while num < limit:
		while abCheck <= num/2 + 1:
			if num%abCheck == 0:
				abSum = abSum + abCheck
			if abSum > num:
				abList.append(num)
				abCheck = num
			abCheck = abCheck + 1
		num = num + 1
		abCheck = 1
		abSum = 0
	print abList
```
problem23.py
```

from abundantfunction import abundant
abundant(28123)

```



My main question is how could I effectively go about adding all of my found abundant numbers together?

Thanks a lot for any help :)

---

### Post by y-lee on 2008-11-08
I didn't really check your function to make sure it worked but you can use the sum function. Change

```
print abList
```

to

```
return abList
```

and then 

```
print sum(abundant(1237))
```

---

### Post by DanielJackins on 2008-11-08
Where is the 1237 coming from? Sorry I wasn't clear, but I meant to add every possible combination of said numbers together, like numbers 1 and 2, 1 and 3, 2 and 7, etc.

---

### Post by y-lee on 2008-11-08
> **DanielJackins said:**
> Where is the 1237 coming from? Sorry I wasn't clear, but I meant to add every possible combination of said numbers together, like numbers 1 and 2, 1 and 3, 2 and 7, etc.

Ah the 1237 was just a number i tested the sum function with. I should have clicked your link and read the problem my bad.

---

