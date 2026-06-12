---
title: "python: a little explanation on my script"
date: 2009-08-30
forum: Programming Talk
---

### Post by filifunk on 2009-08-30
so by looking at other people's codes I've worked this for plotting some stock data from a file called 'table.csv' using matplotlib

```


import pylab

def seriesplot(data):
    pylab.plot(data)
    pylab.show()

infile = open('table.csv', 'r')
lines = infile.readlines()
infile.close()
del lines[0]
lines.reverse()

dates = []
values = []
for line in lines:
    elements = line.split(',')
    dates.append(elements[0])
    values.append(float(elements[-1]))
seriesplot(values)


```

1) It works fine, for one though I don't understand what these lines mean:

```

dates = []
values = []

```

I don't know how to explain those lines...dates and values equal nothing?  that seems silly....

Thanks!

---

### Post by Mirge on 2009-08-30
Just declaring and initializing empty arrays for use in the loop.. or lists, as they say in Python I believe.

---

### Post by colau on 2009-08-30
> **filifunk said:**
> so by looking at other people's codes I've worked this for plotting some stock data from a file called 'table.csv' using matplotlib

```


import pylab

def seriesplot(data):
    pylab.plot(data)
    pylab.show()

infile = open('table.csv', 'r')
lines = infile.readlines()
infile.close()
del lines[0]
lines.reverse()

dates = []
values = []
for line in lines:
    elements = line.split(',')
    dates.append(elements[0])
    values.append(float(elements[-1]))
seriesplot(values)


```

1) It works fine, for one though I don't understand what these lines mean:

```

dates = []
values = []

```

I don't know how to explain those lines...dates and values equal nothing?  that seems silly....

Thanks!


Empty arrays or lists.

---

### Post by Mirge on 2009-08-30
> **colau said:**
> ```

dates = []
values = []

```Empty arrays or lists.

Yes, because I didn't say that...:popcorn:

---

### Post by Can+~ on 2009-08-31
It's a list initialized with a [], so it can call the .append() method the first time.

It's part of the OO-ness of python, if you don't do that, then [it will try to call .append() method of an undeclared variable]("http://en.wikipedia.org/wiki/Duck_typing"), and throw an error.

---

### Post by M4rotku on 2009-08-31
In order to append a list, it has to exist in the first place.  Since you don't want to declare it's existence inside of the loop, you have to declare it as an empty list beforehand.

---

### Post by Bodsda on 2009-08-31
Thought I would just add another small point as a continuation of the previous poster. 

If the list declaration was performed at the top of the loop then every iteration would set them back to [], so appending things to them would be pretty useless.

This is one downfall of python. For example in C++ those declarations could have been made at the for loop and not caused an issue.

---

### Post by wmcbrine on 2009-08-31
> **Bodsda said:**
> For example in C++ those declarations could have been made at the for loop and not caused an issue.In some contexts, yes, that might be slightly more elegant. But not in this one. *values* is referenced after the loop. In fact, the loop exists only to populate *values* (and *dates*, but that's unused, if this is really the complete code), so that it can be used later. Since it's used outside the loop, it makes sense for it to be declared outside the loop.

Now, if you really don't need *dates*, this loop:

```
values = []
for line in lines:
    elements = line.split(',')
    values.append(float(elements[-1]))
```

could be replaced with a list comprehension:

```
values = [float(line.split(',')[-1]) for line in lines]
```

dispensing with the empty initialization that so offends the OP. Try that in C++. :)

Seriously, to call this a downfall of Python is silly. The C++ equivalent of almost *any* Python program is going to be covered in cruft by comparison.

---

