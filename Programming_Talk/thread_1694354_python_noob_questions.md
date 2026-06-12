---
title: "python noob questions"
date: 2011-02-24
forum: Programming Talk
---

### Post by flee0308 on 2011-02-24
Hi, I have just started to learn python 2. Anyway, I have a question regarding 2 signs used.

First, what does the comma (,) sign do? It seems to act like a new line, except the stuff before it and after it are treated as the same line?

Secondly, what does the percentage (%) sign do? I can never figure it out. :/

---

### Post by Portmanteaufu on 2011-02-24
Both signs do different things depending on their context, but I'll take a guess as to where you're seeing them.

When printing, a comma is used to separate each item in a list of parameters you'd like to print. Usually, this is reflected in the output as a space. For instance:

```

>>> x = "dog"
>>> y = "cat"
>>> print x,y
dog cat

```

The same effect could be achieved by concatenating the strings together with a plus sign and adding the space yourself, like so:


```

>>> x = "dog"
>>> y = "cat"
>>> print x + " " + y
dog cat

```

Using the '+' gives you more control over how the output will look, but takes a little more time and effort on the system's part since it has to do the work of adding the strings together. You are also responsible for converting each item you add together into a string before trying to concatenate them using '+'.

The '%' sign is called a 'modulus' operator. It gives you the remainder of a division operation. For example:

```

# Remember that because I didn't say '9.0' instead of '9', it will do integer
# division and truncate the result.
>>> print 9 / 2
4
# If we wanted to know the remainder instead, we can do this:
>>> print 9 % 2
1

```

I hope that helps!

---

### Post by Tony Flury on 2011-02-24
> **Portmanteaufu said:**
> Both signs do different things depending on their context, but I'll take a guess as to where you're seeing them.

When printing, a comma is used to separate each item in a list of parameters you'd like to print. Usually, this is reflected in the output as a space. For instance:

```

>>> x = "dog"
>>> y = "cat"
>>> print x,y
dog cat

```

The same effect could be achieved by concatenating the strings together with a plus sign and adding the space yourself, like so:

The comma can be used also to create a tuple (i.e. a compound data item) for instance : 

```

>>> atuple = 53,"a"
>>> atuple
(53, 'a')
>>> atuple[0]
53
>>> atuple[1]
'a'

```
Note that a tuple is not modifiable

```

>>> atuple[0] = 54
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment

```

Nothing to stop you doing this though : 
```

>>> atuple = 54, atuple[1]
>>> atuple
(54, 'a')

```

---

