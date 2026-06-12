---
title: "Explanation of script"
date: 2008-08-25
forum: Programming Talk
---

### Post by swappo1 on 2008-08-25
Hello,

I am running a script for a tutorial and I don't quite understand what is happening.
  
I have added a print n statement below the for n...statement and print x below the for x...statement to help understand what is happening.
[PHP]#! /usr/bin/env python
# using_break_statement.py

for n in range(2, 10):
    print n
    for x in range(2, n):
	print x
	if n % x == 0:
	    print n, "equals", x, "*", n/x
	    break
    else:
	print n, "is a prime number"[/PHP]
I get the following output
```
scott@scott-laptop:~$ python using_break_statement.py
2
2 is a prime number
3
2
3 is a prime number
4
2
4 equals 2 * 2
5
2
3
4
5 is a prime number
6
2
6 equals 2 * 3
7
2
3
4
5
6
7 is a prime number
8
2
8 equals 2 * 4
9
2
3
9 equals 3 * 3

```
x does not seem to be incrementing like I would expect.  After n = 4 it prints out two numbers for n and x?  I think I am not understanding how the second range function is working.  Thanks for any help.

---

### Post by ghostdog74 on 2008-08-25
indent your last print statement.

---

### Post by swappo1 on 2008-08-25
Here is a repost of the script.  It seems the formatting changed when I pasted it in.
```
for n in range(2, 10):
    print n
    for x in range(2, n):
	print x
	if n % x == 0:
	    print n, "equals", x, "*", n/x
	    break
    else:
	print n, "is a prime number"
```

---

### Post by ghostdog74 on 2008-08-25
your else is "orphaned".

---

### Post by dribeas on 2008-08-25
> **swappo1 said:**
> Here is a repost of the script.  It seems the formatting changed when I pasted it in.
```
for n in range(2, 10):
    print n
    for x in range(2, n):
	print x
	if n % x == 0:
	    print n, "equals", x, "*", n/x
	    break
    else:
	print n, "is a prime number"
```
What is going on in the code is that x is being incremented up to the point where factors are found. Then you **break** out of the inner for (x), and in the next iteration of the outer for (n) you start again with x = 2. The inner loop iterates from 2 to either n/2 if n is prime or the first factor of n. As you are breaking out of the inner for, the else statement does not get executed.

---

