---
title: "Get set using recursion in python"
date: 2008-11-17
forum: Programming Talk
---

### Post by Sagekilla on 2008-11-17
Hi all, I'm currently working on a program that would find the set (according to the [CS definition]("http://en.wikipedia.org/wiki/Set_(computer_science)") which means no repeating entries) of a list of numbers using recursion.

I know I can do it iteratively with something relatively simple like:

```
def getSet(list):
	for x in list:
		if list.count(x) > 1:
			list.remove(x)
	return list
```

But I'm trying to figure out how I could recursively achieve the same goal.

Does anyone have any information to point me towards what I would need to do for the base case / recursive case to achieve this?

Thanks!

---

### Post by cl333r on 2008-11-17
Recursions are dangerous because they can easily make your program go out of memory. Trying to use recursions when one can use iterations is a very bad idea IMHO.
If you got free time and are interested into programming I would really suggest learning something else.
Just my 0.02 euro

---

### Post by pp. on 2008-11-17
> **cl333r said:**
> Recursions are dangerous because they can easily make your program go out of memory. Trying to use recursions when one can use iterations is a very bad idea IMHO.
If you got free time and are interested into programming I would really suggest learning something else.
Just my 0.02 euro

Sorry to say, that is not very useful advice. You'd just as soon say that iterations are dangerous things because they might send your program into a never ending loop.

Both iteration and recursion are useful constructs, and more power to the programmer who knows when to apply which (and when not to apply which).

---

### Post by pp. on 2008-11-17
> **Sagekilla said:**
> 

Does anyone have any information to point me towards what I would need to do for the base case / recursive case to achieve this?



Hint: For a solution of the Set Building task I would consider three cases.

---

### Post by wmcbrine on 2008-11-17
You know Python has set(), right?

>>> a = [1, 2, 1, 5, 2, 9]
>>> a
[1, 2, 1, 5, 2, 9]
>>> set(a)
set([1, 2, 5, 9])

---

### Post by cl333r on 2008-11-17
> **pp. said:**
> Sorry to say, that is not very useful advice. You'd just as soon say that iterations are dangerous things because they might send your program into a never ending loop.

Both iteration and recursion are useful constructs, and more power to the programmer who knows when to apply which (and when not to apply which).

In general, recursive code can be simpler and shorter than iterative code. But recursive programs can run into the problem of increasing the run time (because of the overhead involved in multiple subprogram calls), and of running out of memory (because of the unseen stack that keeps track of variables and return locations).

---

### Post by wmcbrine on 2008-11-17
I should add that this:

> **Sagekilla said:**
> ```
def getSet(list):
	for x in list:
		if list.count(x) > 1:
			list.remove(x)
	return list
```

may not work as you expect, since you're removing elements from the list while iterating over it.

It's not clear to me that this is a problem where recursion would be useful. Many problems are, many aren't.

My iterative solution, if you don't want to use set():

```
def get_set(oldlist):
    newlist = []
    for x in oldlist:
        if x not in newlist:
            newlist.append(x)
    return newlist
```

---

### Post by slavik on 2008-11-17
> **cl333r said:**
> Recursions are dangerous because they can easily make your program go out of memory. Trying to use recursions when one can use iterations is a very bad idea IMHO.
If you got free time and are interested into programming I would really suggest learning something else.
Just my 0.02 euro
if the language in question does tail recursion optimizations, then you will never blow the stack.

---

### Post by ghostdog74 on 2008-11-17
> **wmcbrine said:**
> You know Python has set(), right?

>>> a = [1, 2, 1, 5, 2, 9]
>>> a
[1, 2, 1, 5, 2, 9]
>>> set(a)
set([1, 2, 5, 9])

but then OP will not learn how it is fundamentally done. @OP, for learning purposes, use a dictionary
```

>>> d={}
>>> for i in a:
...  if not d.has_key(i):
...   d[i]=1
...
>>> d
{1: 1, 2: 1, 5: 1, 9: 1}
>>> d.keys()
[1, 2, 5, 9]

```

---

### Post by Paul Miller on 2008-11-17
This sounds a little like a homework exercise, so I'll just offer some hints:

1. You should know how to do it if the input list contains zero or one elements.

2. If your input list contains n elements, break the input into two smaller cases, one of which you can handle directly, and call your function recursively to handle the other piece.

You should be able to do this with exactly n recursive calls.

---

### Post by WW on 2008-11-17
Sagekilla,

If you are implementing a set because you need one for some other application, just use the built-in python sets.  If you are implementing it to learn python, then consider it a challenge to see how many ways you can do it.  Here's a more concise version of ghostdog74's method using a dict:
```

>>> a = [0,10,1,1,3,10,4,1,5]
>>> dict((x,True) for x in a).keys()
[0, 1, 3, 4, 5, 10]
>>> 

```

---

