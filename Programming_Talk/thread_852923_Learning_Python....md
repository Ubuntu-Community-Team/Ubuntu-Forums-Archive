---
title: "Learning Python..."
date: 2008-07-08
forum: Programming Talk
---

### Post by tiachopvutru on 2008-07-08
... that's the name of the book I was learning Python from...

Ah wait, that wasn't my point. :) Anyway, I have a question to ask about what I should do from here. Currently, I'm onto a part (which consists of several chapters) about module and reading a chapter about importing a package of modules. There is still another chapter on module before I get on the two last parts about coding in OOP and Exceptions.

Since the rest of what I still need to learn from the book consist of more than 200 pages, and I really want to code badly, I'm in need of some directions or guidance. I'll continue reading the book as I go, though. Anyway, since the book implies (or rather, what I think it implies) that the knowledge I have so far should be sufficient for some (very) basic coding tasks, I think I am able to at least do something.

I will admit now that I probably didn't go through learning it with as much careful attentions to details as I should have (although I doubt I will be able to remember much anyway without doing something along the way). And back to the original topic, I have tried something like [http://www.pythonchallenge.com/]("http://www.pythonchallenge.com/") but couldn't even get last Level 1. I'll stop here, though, to prevent any further damage to others' impression on me. :)

It would be sweet if someone says that I can actually code some sorts of desktop applications already... though I doubt it.

---

### Post by lut4rp on 2008-07-08
If you have prior programming experience, read Dive Into Python. Its a much smaller, and faster book, and is freely available as download (in various formats) and to read online also.
ref. [http://www.diveintopython.org](http://www.diveintopython.org)

---

### Post by elithrar on 2008-07-08
In terms of tackling a project or starting somewhere: what takes your interest? Web development, GUI applications, network programming, CLI apps/scripts?

---

### Post by tiachopvutru on 2008-07-08
> **lut4rp said:**
> If you have prior programming experience, read Dive Into Python. Its a much smaller, and faster book, and is freely available as download (in various formats) and to read online also.
ref. [http://www.diveintopython.org](http://www.diveintopython.org)

Well, I'm not really looking for a book to learning python right now, as I still have to finish the one that I'm reading...

> **elithrar said:**
> In terms of tackling a project or starting somewhere: what takes your interest? Web development, GUI applications, network programming, CLI apps/scripts?

If it's only about my interest, then I don't really have a preference yet. Heck, I don't know if I can even create a program right now.

However, out of the ones that you listed, I probably would go for GUI applications (this means making GUI out of already-existed command-line programs, right?). Network programming sounds cool but... complicated. I'm not interested in Web development, and do not know what CLI apps/scripts are.

---

### Post by WW on 2008-07-08
It looks like your book is [Learning Python](http://safari.oreilly.com/9780596513986) from O'Reilly.  Have you completed the "Brain Builder" exercises for the chapters that you have read so far?

---

### Post by pmasiar on 2008-07-08
If you need bunch of little problems to train on (you did solved all "homework" tasks, right?), try Project Euler. 200 tasks, and you will see how hard it is by how many people succeeded in solving it.

---

### Post by tiachopvutru on 2008-07-08
> **WW said:**
> It looks like your book is [Learning Python](http://safari.oreilly.com/9780596513986) from O'Reilly.  Have you completed the "Brain Builder" exercises for the chapters that you have read so far?

Yes, somewhat...

> **pmasiar said:**
> If you need bunch of little problems to train on (you did solved all "homework" tasks, right?), try Project Euler. 200 tasks, and you will see how hard it is by how many people succeeded in solving it.

In a way, yes, I do need a bunch of little problems to train on since I'm prone to forget stuffs (mostly methods, since there are so many of them) that I learn.

As for Project Euler, is it designed for beginners? Well, I guess, skill-wise, I fit in the category of "students for whom the basic curriculum is not feeding their hunger to learn (not really)." I just looked at the first question, but it seems like something I will be able to solve (hopefully) rather than something I can't even get past level 1 (like Python Challenge)... Also, do I register there to check my answer?

In addition, may I ask what skills I need to build on before I can actually start coding some sort of general applications?

EDIT: Anyway, I think I have completed Problem #1:
```
L = [x for x in range(1000) if x % 3 == 0 or x % 5 == 0]

solution = 0
for each in L:
    solution += each

print solution

```

---

### Post by ghostdog74 on 2008-07-08
> **tiachopvutru said:**
> 
```
L = [x for x in range(1000) if x % 3 == 0 or x % 5 == 0]

solution = 0
for each in L:
    solution += each

print solution

```

```

print sum([x for x in range(1000) if x % 3 == 0 or x % 5 == 0])

```

---

### Post by tiachopvutru on 2008-07-08
> **ghostdog74 said:**
> ```

print sum([x for x in range(1000) if x % 3 == 0 or x % 5 == 0])

```

Ah, thank you. I forgot about the sum built-in function.

Anyway, I was able to solve Problem #2 (I think), but it didn't turn out to be as short as I had hoped...

Problem:
> Each new term in the Fibonacci sequence is generated by adding the previous two terms. By starting with 1 and 2, the first 10 terms will be:

1, 2, 3, 5, 8, 13, 21, 34, 55, 89, ...

Find the sum of all the even-valued terms in the sequence which do not exceed four million.

My solution:
```
L = [1, 2]
i = 0

while True:
    added = L[i] + L[i+1]
    if added <= 4000000:
        L.append(added)
        i += 1
    else:
        L = filter((lambda x: x % 2 == 0), L)
        print sum(L)
        break

```

---

### Post by pmasiar on 2008-07-08
```

if x % 3 == 0: # hard way
if not x % 3: # easy way
# read: if no remainder after division 

``` :-)

---

### Post by -grubby on 2008-07-08
Not to highjack this thread, but project Eueler looks interesting (from what I've read from this forum page). Too bad I really suck at math.

---

### Post by ghostdog74 on 2008-07-08
> **pmasiar said:**
> ```

if x % 3 == 0: # hard way
if not x % 3: # easy way
# read: if no remainder after division 

``` :-)

Some test runs, taking large numbers. All runs show the hard way runs a bit faster than the easy way. Guess it has to spend time "inverting" the result because of the "not"
```

# python -c "print sum([x for x in xrange(10000000) if x % 3 == 0 or x % 5 == 0])"
23333331666668
# python -c "print sum([x for x in xrange(10000000) if not x % 3 or not x % 5])"
23333331666668
# time python -c "print sum([x for x in xrange(10000000) if x % 3 == 0 or x % 5 == 0])"
23333331666668

real    0m13.087s
user    0m12.833s
sys     0m0.240s
# time python -c "print sum([x for x in xrange(10000000) if not x % 3 or not x % 5])"
23333331666668

real    0m13.311s
user    0m13.197s
sys     0m0.116s
# time python -c "print sum([x for x in xrange(10000000) if x % 3 == 0 or x % 5 == 0])"
23333331666668

real    0m12.551s
user    0m12.313s
sys     0m0.228s
# time python -c "print sum([x for x in xrange(10000000) if not x % 3 or not x % 5])"
23333331666668

real    0m13.240s
user    0m12.969s
sys     0m0.248s
# time python -c "print sum([x for x in xrange(10000000) if x % 3 == 0 or x % 5 == 0])"
23333331666668

real    0m12.688s
user    0m12.453s
sys     0m0.188s
# time python -c "print sum([x for x in xrange(10000000) if not x % 3 or not x % 5])"
23333331666668

real    0m12.922s
user    0m12.801s
sys     0m0.116s


```

---

### Post by tiachopvutru on 2008-07-08
Well, I'm getting stuck at Problem #3

```
The prime factors of 13195 are 5, 7, 13 and 29.

What is the largest prime factor of the number 600851475143 ?
```

The problem is about find prime factors of a number, and here's my code:

```
num = 600851475143
answer = []

for x in xrange(2, num/2 + 1):
    while num % x == 0:
        answer.append(x)
        num = num/x

print answer

```

When I run it, I get this error:
```
OverflowError: long int too large to convert to int

```

I vaguely remember something about long int being int with an L behind it, but I don't know how to get around this problem...

Also, since the variable num constantly changes, how would it affect the for loop?

@pmasiar: Your example makes sense, but *if x%3==0 *clicks to me more than *if not x%3* :)

---

### Post by thornmastr on 2008-07-08
> **nathangrubb said:**
> Not to highjack this thread, but project Eueler looks interesting (from what I've read from this forum page). Too bad I really suck at math.

Instead of Eular, take a look at [http://challenge-you.appspot.com/](http://challenge-you.appspot.com/)

These are great for people learning Python, or people who know the rudiments of Python and want to build on what they already know.

Since I come from a C++ background and have been doing Python for three weeks, these challenges are ideal and certainly fit my current requirements.

---

### Post by pmasiar on 2008-07-08
> **tiachopvutru said:**
> I vaguely remember something about long int being int with an L behind it, but I don't know how to get around this problem...

Don't worry about the types, Python will do most typecasting for you. The only need to worry is in integer division: use 5/2.0 instead of 5/2 if you don't want integer division

> @pmasiar: Your example makes sense, but *if x%3==0 *clicks to me more than *if not x%3* :)

I know, I mistakenly thought that 'not x%3' is faster. As ghostdog74 found for me, I was wrong.

BTW, I found again that in Python "there is one obvious way to do it right". Thanks, Guido! :-)

---

### Post by tiachopvutru on 2008-07-08
> **pmasiar said:**
> Don't worry about the types, Python will do most typecasting for you. The only need to worry is in integer division: use 5/2.0 instead of 5/2 if you don't want integer division

Actually, my bad. I forgot to post the whole error message.

I got this error:
```
Traceback (most recent call last):
  File "C:\Documents and Settings\Administrator\Desktop\ch06.py", line 4, in <module>
    for x in xrange(2, num/2 + 1):
OverflowError: long int too large to convert to int

```

But eh, I now want to write application even more. =p

---

### Post by Lster on 2008-07-08
[QUOTE=ghostdog74]```
print sum([x for x in range(1000) if x % 3 == 0 or x % 5 == 0])
```[/QUOTE]

You might be interested to know that this code is faster still:

[PHP]
def add(n, x):
	q = n/x
	r = n%x
	
	return q*(x+n-r)/2

t = add(10**3-1, 3)
t += add(10**3-1, 5)
t -= add(10**3-1, 15)

print t
[/PHP]

Not that it really matters for such small numbers. But for values like 10^12 it does.

---

### Post by WW on 2008-07-08
> **tiachopvutru said:**
> Actually, my bad. I forgot to post the whole error message.

I got this error:
```
Traceback (most recent call last):
  File "C:\Documents and Settings\Administrator\Desktop\ch06.py", line 4, in <module>
    for x in xrange(2, num/2 + 1):
OverflowError: long int too large to convert to int

```

But eh, I now want to write application even more. =p

From [Python Library Reference](http://docs.python.org/lib/built-in-funcs.html):
> 
Note: xrange() is intended to be simple and fast. Implementations may impose restrictions to achieve this. The C implementation of Python restricts all arguments to native C longs ("short" Python integers), and also requires that the number of elements fit in a native C long.

The number 600851475143 is larger than the maximum value that can be represented by a long int.

---

### Post by Wybiral on 2008-07-08
> **ghostdog74 said:**
> Some test runs, taking large numbers. All runs show the hard way runs a bit faster than the easy way. Guess it has to spend time "inverting" the result because of the "not"

Those results don't look very conclusive to me. Too much fluctuation and not enough tests run (it's also factoring in Python startup/parse time and well, it's parsing two different chunks of code). The difference isn't greater than the overall variance.

---

### Post by ghostdog74 on 2008-07-08
> **Wybiral said:**
> Those results don't look very conclusive to me. Too much fluctuation and not enough tests run (it's also factoring in Python startup/parse time and well, it's parsing two different chunks of code). The difference isn't greater than the overall variance.

well, you can try them out on your environment and see if its conclusive.  Python startup/parse time is not an issue because the environment are the same for both scenarios.

---

### Post by tiachopvutru on 2008-07-08
> **Lster said:**
> You might be interested to know that this code is faster still:

[PHP]
def add(n, x):
	q = n/x
	r = n%x
	
	return q*(x+n-r)/2

t = add(10**3-1, 3)
t += add(10**3-1, 5)
t -= add(10**3-1, 15)

print t
[/PHP]

Not that it really matters for such small numbers. But for values like 10^12 it does.

Ah, thank you. It took me quite a while to figure out the code (although not concrete enough to be able to explain in words), but it's amazing. :) 

> **WW said:**
> From [Python Library Reference](http://docs.python.org/lib/built-in-funcs.html):

The number 600851475143 is larger than the maximum value that can be represented by a long int.

Well, if I change xrange to range, I receive another error on the resulting list being too long. Does that mean that I ought to use a different and more efficient algorithm in order to solve this problem?

---

### Post by tiachopvutru on 2008-07-09
Well... seem like all I had to do was use a while loop instead of a for loop. I think I got it right... 

```
num = 600851475143
answer = []
i = 2

if num % i == 0:
    answer.append(i)
    num = num/i

i = 3

while num != 1:
    if num % i == 0:
        answer.append(i)
        num = num/i
    else:
        i+=2

print answer    

```

I wonder if I would save some performance if I start i from num and slowly decreasing it instead of starting from 2 and slowly increasing it. I would then have to check if the answer is prime, though...

---

### Post by Lster on 2008-07-09
> **tiachopvutru]Ah, thank you. It took me quite a while to figure out the code (although not concrete enough to be able to explain in words), but it's amazing.
[/QUOTE]

Let's define add(n, d) to be:

"The sum of all integers, less than or _equal_ to n, that are divisible by d. For example d(10, 3) = 18."

Therefore, add(999, 3) gives the number of numbers less than 1000 (&#8804 said:**
> 
def add(n, x):
	terms = n/x #Number of terms
	r = n%x #Remainder from division
	
	first = x #First term
	last = n-r #Last term. r is taken to make last divisible by x
	
	#Average = (first+last)/2
	return terms*(first+last)/2

t = add(999, 3)
t += add(999, 5)
t -= add(999, 15) #Remove overlap

print t
[/PHP]

[QUOTE=tiachopvutru]I wonder if I would save some performance if I start i from num and slowly decreasing it instead of starting from 2 and slowly increasing it. I would then have to check if the answer is prime, though...

You might be interested in SymPy which is a very good symbolic maths library. I think it is an available package in Synaptic so it should be easy to install. Then you can try out the stuff on:

[http://docs.sympy.org/](http://docs.sympy.org/)

And it also has an isprime() function! :)

---

