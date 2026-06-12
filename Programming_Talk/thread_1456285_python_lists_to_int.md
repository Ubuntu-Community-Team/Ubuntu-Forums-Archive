---
title: "python lists to int"
date: 2010-04-17
forum: Programming Talk
---

### Post by flyingsliverfin on 2010-04-17
if i have a bunch of lists full of numbers, but in a specific order, how do i combine those lists to make an integer?

for example:

x = ['9','5','7']
y = ['2','5','8']
then how do i make it print the number 957258?

---

### Post by soltanis on 2010-04-17
Is this homework?

(You answer "yes"): read about list methods, and the str.join function, which will help you get the solution.

(You answer "no"): Just this once, here's the answer:

```

x = ['9','5','7']
y = ['2','5','8']
print "".join(x.extend(y))

```

In the general case you had a list of lists with digits to combine you could do:
```

def collapse(x):
    return "".join(x)

combine = [x, y, z] # x, y, z are lists of digits
print collapse(map(collapse, combine))

```

Each invocation of collapse collapses a list of strings into a single joined string that is undelimited.

There is a way to extend this to the general case where you have a list of nested lists of lists with digits in them, but I'll leave that up to you as an exercise.

---

### Post by geirha on 2010-04-17
Have a look at list comprehensions. [http://docs.python.org/tutorial/datastructures.html#list-comprehensions](http://docs.python.org/tutorial/datastructures.html#list-comprehensions)

---

