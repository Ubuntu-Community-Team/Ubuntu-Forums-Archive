---
title: "Euler Problem 23 in Python"
date: 2010-04-07
forum: Programming Talk
---

### Post by whackedspinach on 2010-04-07
I'm trying to solve [Project Euler problem #23]("http://projecteuler.net/index.php?section=problems&id=23").  I think the code works, but it is terribly inefficient (I killed it after 10 minutes of number crunching).  What is a better way to solve this problem?
```
'''Project Euler - Problem 23
"Find the sum of all the positive integers which cannot be 
written as the sum of two abundant numbers."'''
def sum_divisors(n):
    """Sums the proper divisors of n."""
    sum = 1
    for x in xrange(2, int(n ** 0.5) + 1):
        if (n % x == 0):
            sum += x + n / x
    if (n ** 0.5) == int(n ** 0.5): sum -= (n ** 0.5)
    return sum

def is_abundant(n):
    """Checks if the sum of the divisors of n is greater than n."""
    if sum_divisors(n) > n: 
        return True
    else: return False

def find_abundants(limit):
    """Finds all abundant numbers up to the specified limit"""
    abundants = [x for x in xrange(1, limit) if is_abundant(x)]
    return abundants

abundants_below_28123 = find_abundants(28123)
sums = [x + y for x in abundants_below_28123 for y in abundants_below_28123 if x + y < 28123]
answer = 0
for x in xrange(1, 28123):
    if x in sums: pass
    else: answer += x
print answer
```

---

### Post by Simon17 on 2010-04-07
You could be a lot smarter about the way you generate your sums. For a given, x, you only need to check y<28123-x.
This will make your sums array smaller, also speeding up other parts of your code.

---

### Post by Some Penguin on 2010-04-08
You can also short-circuit the loop in your 'abundant' check once it's clear that it must fail.

---

### Post by citaret on 2010-04-08
I think the code to check if x in sums is a hotspot, which is slow. Here is my code, which finished in 10s on my computer, where find_abundants costs 1s and get_list costs 9s.

```
#!/usr/bin/env python

'''Project Euler - Problem 23
"Find the sum of all the positive integers which cannot be 
written as the sum of two abundant numbers."'''
def sum_divisors(n):
    """Sums the proper divisors of n."""
    sum = 1
    for x in xrange(2, int(n ** 0.5) + 1):
        if (n % x == 0):
            sum += x + n / x
    if (n ** 0.5) == int(n ** 0.5): sum -= (n ** 0.5)
    return sum

def is_abundant(n):
    """Checks if the sum of the divisors of n is greater than n."""
    if sum_divisors(n) > n: 
        return True
    else: return False

def find_abundants(limit):
    """Finds all abundant numbers up to the specified limit"""
    abundants = [x for x in xrange(1, limit) if is_abundant(x)]
    return abundants

[B]def get_list(limit):
    abds = find_abundants(limit)
    list = range(limit)
    for x in abds:
        for y in abds:
            if x + y >= limit:
                break
            list[x + y] = 0
    return list

print sum(get_list(28123))[/B] 

```

---

### Post by whackedspinach on 2010-04-08
> **citaret said:**
> I think the code to check if x in sums is a hotspot, which is slow. Here is my code, which finished in 10s on my computer, where find_abundants costs 1s and get_list costs 9s.

```

[B]def get_list(limit):
    abds = find_abundants(limit)
    list = range(limit)
    for x in abds:
        for y in abds:
            if x + y >= limit:
                break
            list[x + y] = 0
    return list

print sum(get_list(28123))[/B] 

```

That is a much more eficent way of doing that, since you don't have to check a sums list every time, etc.  Runs in 7.5s on my computer.  Thanks, all.

---

