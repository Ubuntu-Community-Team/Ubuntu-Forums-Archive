---
title: "Python example not making sense"
date: 2010-06-30
forum: Programming Talk
---

### Post by xoros on 2010-06-30
Going through the python tutorial (section 4.4. break and continue  Statements, and else Clauses on Loops)  in this example:
```
>>> for n in range(2, 10):
...     for x in range(2, n):
...         if n % x == 0:
...             print n, 'equals', x, '*', n/x
...             break
...     else:
...         # loop fell through without finding a factor
...         print n, 'is a prime number'
...
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3

```



```
>>> for n in range(2, 10):
...     for x in range(2, n):
...             print "x is",x
...             print "n is",n
...             if n % x == 0:
...                     print n, 'equals', x, '*', n/x
...                     break
...             else:
...                     print n, 'is a prime number'
... 
x is 2
n is 3
3 is a prime number
x is 2
n is 4
4 equals 2 * 2
x is 2
n is 5
5 is a prime number
x is 3
n is 5
5 is a prime number
x is 4
n is 5
5 is a prime number
x is 2
n is 6
6 equals 2 * 3
x is 2
n is 7
7 is a prime number
x is 3
n is 7
7 is a prime number
x is 4
n is 7
7 is a prime number
x is 5
n is 7
7 is a prime number
x is 6
n is 7
7 is a prime number
x is 2
n is 8
8 equals 2 * 4
x is 2
n is 9
9 is a prime number
x is 3
n is 9
9 equals 3 * 3
>>> 

```

How come in that last example (I'm trying to see what is happening with x and n) It gives those results?   
9 is a prime number ? 
It doesn't make sense... is the print statement initializing the variables incorrectly or something?

---

### Post by Can+~ on 2010-06-30
The "else" statement has a different effect depending if it's paired with an "if" or a "for" statement.

[PHP]for iteration in iterable:
    # Normal iteration
else:
    # If a loop ends succesfully.[/PHP]

A "break" statement will make it end abruptly, thus, ignoring the "else" clause.

---

### Post by xoros on 2010-06-30
Thank you

---

