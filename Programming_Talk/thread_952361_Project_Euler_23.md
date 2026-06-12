---
title: "Project Euler 23"
date: 2008-10-19
forum: Programming Talk
---

### Post by luke77 on 2008-10-19
Hi guys,

I'm doing the Project Euler problems to help me learn python and brush up on my math, and I'm stuck on number 23. The problem is posted here:
[]("http://projecteuler.net/index.php?section=problems&id=23")

Here's the code I've written so far:
```

def isPrime(x):
    for i in xrange(2,x/2):
        if x%i==0:
            return False
    return True

def isAbundant(a):

    divisors =[ x for x in xrange(1,a/2 + 1) if a%x==0 ]
    if sum(divisors)>a:
        return True
    return False
#Generate list of abundant numbers below 28123
abundants=[]
for i in xrange(1,28123):
    if isAbundant(i):
        abundants.append(i)




def isItASum(x):
    b=len(abundants)/2 + 1
    for i in abundants[0:b]:
        if (x-i) in abundants:
            return True
    return False

#Generate list of numbers that can be expressed as sum of two abundant numbers
theanswers=[]

for abundant in abundants:
    for abundant1 in abundants:
        thesum=abundant+abundant1
        if thesum not in theanswer:
            theanswer.append(thesum)

#Sum all numbers that can't be expressed as sum of two abundants
for i in xrange(1,28123):
    if i not in theanswer:
        answer=answer+i

print answer
```

This seems like it should work, but when I run the code it just "processes" for a long time, and no answer. I think it's probably because this piece of code:

```
for abundant in abundants:
    for abundant1 in abundants:
        thesum=abundant+abundant1
        if thesum not in theanswer:
            theanswer.append(thesum)
```

asks the computer to perform so many operations, but I'm not sure how to solve this more "concisely". Any suggestions?

Thanks,
Luke

---

### Post by Lux Perpetua on 2008-10-19
You probably don't want to search a list for every sum of two abundant numbers. I'd use a different structure here. For example, you could make a big table of booleans (indices 1, ..., 28123), and when you generate a sum of two abundant numbers, set the corresponding bit to "true." 

If that's still too slow, consider changing the approach entirely: instead of generating all possible sums of abundant numbers (of which there might be very many), go through 24, ..., 28123 and try to write each number as a sum of abundant numbers, which you can do with at worst a single pass through your sorted list of abundant numbers.

---

### Post by Reiger on 2008-10-19
Could you please post your problem, it must've been accidentally deleted/missed in post #1, also your primality test may not work: what does it return when you give it 2, or anything below 2?

---

### Post by y-lee on 2008-10-19
> **Reiger said:**
> Could you please post your problem. 

For the record:
> A perfect number is a number for which the sum of its proper divisors is exactly equal to the number. For example, the sum of the proper divisors of 28 would be 1 + 2 + 4 + 7 + 14 = 28, which means that 28 is a perfect number.

A number whose proper divisors are less than the number is called deficient and a number whose proper divisors exceed the number is called abundant.

As 12 is the smallest abundant number, 1 + 2 + 3 + 4 + 6 = 16, the smallest number that can be written as the sum of two abundant numbers is 24. By mathematical analysis, it can be shown that all integers greater than 28123 can be written as the sum of two abundant numbers. However, this upper limit cannot be reduced any further by analysis even though it is known that the greatest number that cannot be expressed as the sum of two abundant numbers is less than this limit.

Find the sum of all the positive integers which cannot be written as the sum of two abundant numbers.


> **Reiger said:**
> also your primality test may not work: what does it return when you give it 2, or anything below 2?

That is not the problem here tho it gives true for 0,1 and 2. So it succeeds for 2 but arguably fails for 1 and certainly fails for zero.

luke77, I see two problems with your code as posted. It is probably not why the code takes so long. but anyway you define **theanswers=[]** but then use the variable name theanswer. latter you use **answer=answer+i** but 'answer' is not defined in your code. Fixing these and using a smaller max number the code seemed to work for me.

You do need to speed it up somehow tho so it won't take so long on bigger numbers. I can think of several ways to do this but you might want to consider that the sum-of-divisors function S(x) is multiplicative in the following sense: if x and y are relatively prime, then S(xy) = S(x)S(y). Maybe that will help. :)

---

### Post by luke77 on 2008-10-19
> **Lux Perpetua said:**
> You probably don't want to search a list for every sum of two abundant numbers. I'd use a different structure here. For example, you could make a big table of booleans (indices 1, ..., 28123), and when you generate a sum of two abundant numbers, set the corresponding bit to "true." 

If that's still too slow, consider changing the approach entirely: instead of generating all possible sums of abundant numbers (of which there might be very many), go through 24, ..., 28123 and try to write each number as a sum of abundant numbers, which you can do with at worst a single pass through your sorted list of abundant numbers.


Could you explain the first method, generating a table of booleans and setting the bit to true when a sum of an abundant number is generated? Python is my first language and I think this approach is probably more common in one of the lower level languages...I am not sure how to generate a table of booleans that can be modified.

Second, I had thought about using your second approach but it seemed like it would be just as "complex". With this method you'd have to generate the list of abundants, and then for each number to test (24...28123), subtract the first abundant number and test to see if the result is in the abundant list. For instance, something like:

```
for number in range(24,28123):
for abundant in abundants:
if (number - abundant) in abundants:
numbersThatAreSumsOfAbundants.append(number)
```

I tried this and had the same problem I'm having now; basically, far too many calculations.

---

### Post by luke77 on 2008-10-20
bump?

---

### Post by Paul Miller on 2008-10-21
Your "sum of divisors" calculation in the isAbundant() function is wrong.  Try it out with isAbundant(12).  Then, step through it with a=12 to find out why.

Edit: Looks like I was mistaken.  This part is right.

---

