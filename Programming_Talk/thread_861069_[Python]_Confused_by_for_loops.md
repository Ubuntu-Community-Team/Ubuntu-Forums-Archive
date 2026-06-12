---
title: "[Python] Confused by for loops"
date: 2008-07-16
forum: Programming Talk
---

### Post by TreeFinger on 2008-07-16
[php]
li = [1, 2, 1, 2, 1, 2]
for i in li:
	li[i] = 0
print li
[/php]

```

[0, 0, 0, 2, 1, 2]

```

I thought the following would work..
[php]
li = [1, 2, 1, 2, 1, 2]
for i in li:
	i = 0
print li
[/php]

```

[1, 2, 1, 2, 1, 2]

```

I'm confused :confused:

---

### Post by themusicwave on 2008-07-16
First off those two loops are totally different.

The python loops runs once for each item in li.  What is happening is that you are getting the Value in each of the cells, not it's index.

Try this:

[PHP]
li = [1, 2, 1, 2, 1, 2]
for item in li:
    print item
[/PHP]

You will see the values print in order like so:

1
2
1
2
1
2

If you want the indexes do this:

[PHP]
index=0
li = [1, 2, 1, 2, 1, 2]

while index < len(li):
   print "Value at index #" + str(index) + " " + li[index]
   index += 1
[/PHP]

That is the fundamental difference.  The For in python is very similar to a for each loop in other languages if you are familiar with such a thing.

---

### Post by TreeFinger on 2008-07-16
I'm simply attempting to change all the values in the list to 0.

---

### Post by themusicwave on 2008-07-16
I forgot to look at the the second part.

With your loop:

[PHP]
li = [1, 2, 1, 2, 1, 2]
for i in li:
    i = 0
print li  
[/PHP]


The line i=0 isn't doing anything.  Your loop is doing nothing to li.  You would get the same result with:

[PHP]
li = [1, 2, 1, 2, 1, 2]
print li  
[/PHP]

If you wanted to put all zeros in the list this would work:

[PHP]
li = [1,2,1,2,1,2]
count=0
while count < len(li):
	li[count]=0
	count +=1	
print li
[/PHP]

That yields: [0, 0, 0, 0, 0, 0]

There may be a better way to do it once the Python gurus weight in.

---

### Post by TreeFinger on 2008-07-16
I can see that i = 0 is doing nothing by the output

This code prints each value
```

li = [1, 2, 3, 4, 5, 6]
for i in li:
	print i

```

which confuses me why i = 0 does nothing.

---

### Post by tiachopvutru on 2008-07-16
> **TreeFinger said:**
> 
I thought the following would work..
[php]
li = [1, 2, 1, 2, 1, 2]
for i in li:
	i = 0
print li
[/php]

```

[1, 2, 1, 2, 1, 2]

```

I'm confused :confused:

For this one, until someone comes in who can explains what's truly going on, you will have to stick with what I think the problem is. The i in each iteration simply gets assigned to each item in the list, and in Python, assignment means referencing. A variable is simply a name that points to an object (an object can be a number, a string, etc.). So, think of when the for loop runs the first iteration, i and li[0] points at the same number 1, then you change i to point at a different number, which is 0, but li[0] still point at the same number that it originally pointed, which is 1. At least, that's what I think. =p

Anyway, you can use the while loop in this one, among a whole bunch of others (although most are unnecessary more complicated). You can use the list comprehension, too, which is faster and shorter.

```
li = [1, 2, 1, 2, 1, 2]
li = [i * 0 for i in li]
```

Note that I put i * 0 instead of i = 0 inside the bracket [], that's because list comprehension (which is what it is inside the []) only accept expressions and not statements (expressions are like a + b and statements are like a = b).

---

### Post by ghostdog74 on 2008-07-16
> **TreeFinger said:**
> [php]
li = [1, 2, 1, 2, 1, 2]
for i in li:
	li[i] = 0
print li
[/php]

I'm confused :confused:

why are you confused? if you do this, you will know why

```

for i in li:
  print "value of i is ", i
  print "value of li[i] is ", li[i]

```

---

### Post by CptPicard on 2008-07-16
> **tiachopvutru said:**
> in Python, assignment means referencing.

Yes, the issue is that the only thing here that is being actually assigned is the "i" and *not* the list contents. Which means that at each iteration, i is first made to refer to an item in the list, and then inside the loop, it is made to refer to a constant 0. Then we just go again...

EDIT: To be more clear of what your misconception is here... if this held what you're trying to do, this would be true:

```

a = 5
b = a
b = 3

#Now a would be 3 but of course it isn't.

```

---

### Post by themusicwave on 2008-07-16
I think that tiach is right about the i=0 thing, but I too will wait for some gurus.

As for the first one

[PHP]li = [1, 2, 1, 2, 1, 2]
for i in li:
    li[i] = 0
print li
[/PHP]

In that one I know exactly what happens.  Let's look at the loop step by step.

1)The loop enters and the first value is pulled from li and assigned to i.  This is 1.

Now, li[1] is set to 0.  Li now looks like [1,0,1,2,1,2]

2) The loop runs again this next value of li is pulled out which is 0 and this is assigned to i.

Now, li[0] is set to 0.  Li looks like [0,0,1,2,1,2].

3) The loop runs again this next value of li is pulled out which is 1 and this is assigned to i.

Now, li[1] is set to 0.  Li looks like [0,0,1,2,1,2].

4) The loop runs again this next value of li is pulled out which is 2 and this is assigned to i.

Now, li[2] is set to 0.  Li looks like [0,0,0,2,1,2].

5) The loop runs again this next value of li is pulled out which is 1 and this is assigned to i.

Now, li[1] is set to 0.  Li looks like [0,0,0,2,1,2].

6) The loop runs again this next value of li is pulled out which is 2 and this is assigned to i.

Now, li[2] is set to 0.  Li looks like [0,0,0,2,1,2].

The loop runs once for each value in li.  The confusion really comes from the fact that li[1] is set to 0 which then causes li[0] to get set to 0 as well.

---

### Post by ghostdog74 on 2008-07-16
> **TreeFinger said:**
> I'm simply attempting to change all the values in the list to 0.

use a for loop going over the length of the list
```

for i in range(len(li)):
    li[i]=0

```
or simply create another list with all 0's according to the length of li.
or 
```

map(lambda x :0 , li)

```

---

### Post by Martin Witte on 2008-07-16
as others suggested in this thread - create a new list with length of the original list and fill it with zeros, a quick way is
```
>>> li = [1, 2, 1, 2, 1, 2]
>>> li = [0, ] * len(li)
>>> print li
[0, 0, 0, 0, 0, 0]
>>> 
```

---

### Post by Can+~ on 2008-07-16
The iterator "i" in the for loop just copies the value contained in each element of the list. Therefore, modifying the value of i has no effect on the original *list* (why I said array?).

Here's a more "Pythonic" way:

[PHP]a = [1, 2, 1, 2, 3, 1]
print a

# Define a short function that just returns 0, and map it.
a = map(lambda x: 0, a)

print a[/PHP]

Although the method suggested before is more efficient. The map function makes sense when there are values to compute.

---

### Post by Smygis on 2008-07-16
[php]
>>> a = [1, 2, 1, 2, 3, 1]
>>> for i in xrange(len(a)):
...     a[i] = 0
... 
>>> a
[0, 0, 0, 0, 0, 0]
>>> # or the exact same thing a diffrent way. The most Pythonic way
... 
>>> a = [1, 2, 1, 2, 3, 1]
>>> a = [0 for _ in a]
>>> a
[0, 0, 0, 0, 0, 0]
>>> 

[/php]

---

### Post by Lux Perpetua on 2008-07-17
> **TreeFinger said:**
> I can see that i = 0 is doing nothing by the output

This code prints each value
```

li = [1, 2, 3, 4, 5, 6]
for i in li:
	print i

```

which confuses me why i = 0 does nothing.I think I know what's confusing you: the i in the loop body gets its own copy of each element of the list. It doesn't become an alias for the corresponding list element.

To do what you want, I'd probably do something like ```
for i in xrange(len(li)):
    li[i] = 0

```

---

### Post by dmm1285 on 2008-07-17
Another way to do it:
[PHP][0 for i in li][/PHP]

---

### Post by Smygis on 2008-07-17
how nice that the two guys behind me wrote the exact same thing i did.

---

