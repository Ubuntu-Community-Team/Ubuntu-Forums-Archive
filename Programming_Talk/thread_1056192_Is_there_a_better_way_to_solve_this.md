---
title: "Is there a better way to solve this?"
date: 2009-01-31
forum: Programming Talk
---

### Post by eightmillion on 2009-01-31
Is there a better way to solve this, other than brute force? Am I missing something?

> A number ends with the digit 6. 
If that final six gets moved to the beginning of the number (think "rotate decimal right"), the resulting number is six times the original one. 
What is the original number? 

For example, if our desired number was 456, then 645 should equal 6 * 456, which is obviously not the case.

My python version of this has been running for about fifteen minutes. I compiled a c++ version with shedskin and it ran for about ten minutes and then printed a 0 and exited. I'm assuming that I overflowed an integer. Here's my python code:

```

#!/usr/bin/env python

x = 6

def rotate(num):
    shift = 10
    msig,lsig = divmod(num,10)
    while shift < msig: shift*=10
    return shift*lsig + msig

while rotate(x) != 6*x:
    x+=10

print x

```

This challenge really isn't very interesting if it's just a stress test for my processor.

---

### Post by pp. on 2009-01-31
I haven't given much thought to your problem.

However, you appear to inspect many numbers which can not possibly satisfy the requirements.

Consider y=6x.

We know that y begins with the digit '6'. That somewhat limits the digits x can start with. We also know that x ends with the digit '6'. That also limits the number of digits y can end with.

---

### Post by kavon89 on 2009-01-31
Would that include decimals? 1.6, 1.06 etc?

---

### Post by Reiger on 2009-01-31
By observing 'how you do division', you can see that the most significant (the leftmost) digit of the original must have been 1. Reason: 

define a number consisting of a digit x at the left, followed n digits unknown (denoted by ?), and at the very right a 6 (given in the problem):
x???6

By the example we move 6 to the left, so:
6x???

Now we divide by 6 again, and (according to the problem) obtain the original:
1((int) x/6)??6 = x???6

So we know we start with 1 and end with 6. If you can capture that logic in code, you may be onto something?

---

### Post by eightmillion on 2009-01-31
> **pp. said:**
> I haven't given much thought to your problem.

However, you appear to inspect many numbers which can not possibly satisfy the requirements.

Consider y=6x.

We know that y begins with the digit '6'. That somewhat limits the digits x can start with. We also know that x ends with the digit '6'. That also limits the number of digits y can end with.

I think that's it. In order for y to start with 6, x has to start with 10 or 11. Thanks. :D

> **kavon89 said:**
> Would that include decimals? 1.6, 1.06 etc?

It only includes integers.

---

### Post by unutbu on 2009-01-31
```
Let x be a number with digits (1,a_{n-1},a_{n-2},a_{n-3},...,a_1,  6)
Let y be a number with digits (6,      1,a_{n-1},a_{n-2},...,a_2,a_1)

```
y=6*x is a number with what digits ?

Start with the units digit. x has a units digit of 6.
6*6=36. The units digit of 36 is 6. So y must have a units digit of 6. a_1=6.

Now think about the tens digit of 6*x. The tens digit is related to 6*a_1+3. The 3 comes from the tens digit of 36. But we know a_1=6. So 6*a_1+3=39. So the tens digit of 6*x is 9.
And we have to carry the 3 (in 39) over to the hundreds digit...

Trundle along this line of thinking and you end up with:

1016949152542372881355932203389830508474576271186440677966
6101694915254237288135593220338983050847457627118644067796

[PHP]
#!/usr/bin/env python
done=False
a=[6]
b=[0]
def units_digit(num):
    astr='%s'%num
    return int(astr[-1])
def tens_digit(num):
    astr='%s'%num
    if len(astr)>1:
        return int(astr[-2])
    else:
        return 0

while not done:
    num=6*a[-1]+b[-1]
    a.append(units_digit(num))
    b.append(tens_digit(num))
    if a[-1]==1 and b[-1]==0:
        done=True
a.reverse()
big_str=''.join([str(num) for num in  a])
big_num=int(big_str)
print big_num
print big_num*6[/PHP]

---

### Post by wmcbrine on 2009-01-31
I hate this kind of problem -- it mixes up real quantitative relationships (in this case, multiplication), which can be worked out algebraically, with tricks based on mere manipulation of the symbols used in a particular base system (in this case, base 10).

So let's fix that, and make it all algebraic. That calls for a logarithm. "Move 6 to the front" can be thought of as (in Python terms):

(x - 6) / 10 + 10 ** int(math.log10(x)) * 6

That's y (the second number), AKA 6x.

---

### Post by WW on 2009-01-31
***Spoiler alert!***

Here's another version.  It finds all the solutions up to a given maximum number of digits.  It took a few seconds to find the 172 solutions that have fewer than 10,000 digits.
```

def find_numbers(maxdigits):
    result = []
    for k in range(2,maxdigits):
        p = 10**(k-2)-36
        m,r = divmod(p,59)
        if r == 0:
            n = 10**(k-1) + m*10 + 6
            result.append(n)
    return result

```
How does it work?  Let n be a solution with k digits.  Since the last digit of n is 6, 6*n will certainly be greater than rotated(n) unless the first digit of n is 1.  Let m be the inner number between the 1 and the 6, so n = 10**(k-1) + 10*m + 6.  Then rotated(n) is 6*10**(k-1) + 10**(k-2) + m. We want 6*(10**(k-1) + 10*m + 6) = 6*10**(k-1) + 10**(k-2) + m. Solve this equation for m to get 

m = ( 10**(k-2) - 36 ) / 59

Since m must be an integer, there is only a solution for a given k if (10**(k-2)-36) is divisible by 59.  The code loops through all values of k up to maxdigits, and computes n whenever (10**(k-2)-36) is divisible by 59.

---

### Post by WW on 2009-01-31
I just wanted to add that I think unutbu's algorithm is very cool.  It's simpler and faster than what I wrote.  It doesn't waste time checking possible solutions; it simply generates the solution.

Also, there is no point in my code computing more numbers after the first.  These solutions can be generated by concatenating copies of the first solution.  That is, the first solution is 1016...7966, the second solution is 1016...79661016...7966, the third is 1016...79661016...79661016...7966, and so on.

---

