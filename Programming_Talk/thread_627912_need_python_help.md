---
title: "need python help"
date: 2007-11-30
forum: Programming Talk
---

### Post by rob1101 on 2007-11-30
i wrote this program but i keep getting the following errors and im new to python so i cant figure out the problems.


the program

```

# Description: Finds all prime numbers between a lowerbound and an upperbound.

lowerbound = input("Enter a lower bound: ")
upperbound = input("Enter a upper bound: ")
prinum = 1
i = lowerbound
a = 1

def prime(x):
    while x >= i:
        i += 1
        mod = x % i

        if mod == 0:
            prinum = 0
            i = lowerbound
    return i

for a in range(lowerbound, upperbound):
    prime(a)
    prinum = 1

    if prinum == 1:
        print a

```

the errors

```

Traceback (most recent call last):
  File "/home/robert/Programming/Python/primenumbers.py", line 25, in <module>
    prime(a)
  File "/home/robert/Programming/Python/primenumbers.py", line 15, in prime
    while x >= i:
UnboundLocalError: local variable 'i' referenced before assignment

```

---

### Post by Majorix on 2007-11-30
Like it says, you are trying to access something non-existant. The variable "i" doesn't exist in the function you defined.

---

### Post by rob1101 on 2007-11-30
> **Majorix said:**
> Like it says, you are trying to access something non-existant. The variable "i" doesn't exist in the function you defined.

hehe so simple i didnt see it. is there a way to call global variables in to a function? i know its not needed for this program, but i would just like to know.

---

### Post by Majorix on 2007-11-30
You use the syntax
```
global i
```
in your code BEFORE the while.

---

### Post by rob1101 on 2007-11-30
> **Majorix said:**
> You use the syntax
```
global i
```in your code BEFORE the while.

thanks a ton man

---

### Post by Majorix on 2007-11-30
No problem.

---

