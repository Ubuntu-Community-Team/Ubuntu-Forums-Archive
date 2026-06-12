---
title: "how to declare a 2D array in python"
date: 2006-02-10
forum: Programming Talk
---

### Post by krypto_wizard on 2006-02-10
I am trying to execute the following code

```

a =[][]
for i in range(3):
    for j in range(3):
        a[i][j] = i+j

print a

```

I get an error "invalid syntax". How to fix this bug.

Thanks for the help

---

### Post by thumper on 2006-02-10
You need to append values into the lists

```
>>> a = []
>>> for i in xrange(3):
...     a.append([])
...     for j in xrange(3):
...             a[i].append(i+j)
...
>>> a
[[0, 1, 2], [1, 2, 3], [2, 3, 4]]
>>>

```

---

### Post by krypto_wizard on 2006-02-10
Thanks, it worked like a charm.

[QUOTE=thumper]You need to append values into the lists

```
>>> a = []
>>> for i in xrange(3):
...     a.append([])
...     for j in xrange(3):
...             a[i].append(i+j)
...
>>> a
[[0, 1, 2], [1, 2, 3], [2, 3, 4]]
>>>

```[/QUOTE]

---

### Post by zobayer1 on 2010-12-10
:popcorn: Just to put, there is an easier way, have a look:

To create an n by n 2D array:
```
a = [[]*n for x in xrange(n)]
```
In case you want to initialize each element with some value v
```
a = [[v]*n for x in xrange(n)]
```
Test it
```

print a

```

---

### Post by Tony Flury on 2010-12-11
if it is going to be a sparsley populated array, that you need to index with two integers, you might find that a dictionary with a tuple (x,y) as the key might work just as well.

---

### Post by ssam on 2010-12-11
and if you are dealing with arrays of numbers then have a look at numpy.

---

### Post by Pipeliner on 2011-09-16
You should also be able to type this in:
```
l_variable = [[[2]*3]*4]*5
```This will create a three dimensional array with the following properties

[LIST]
[*]all values will be populated with '2'
[*]the first dimension will be length 3
[*]the second dimension will be length 4
[*]the third dimension will be length 5
[/LIST]
Because Python does not require type declaration when creating a new variable, I choose to put a prefix in front of my variables. In this instance I use the "l_" in front of my list variables.

This has been tested with Python 2.7.1

---

### Post by Senesence on 2011-09-16
> **Pipeliner said:**
> You should also be able to type this in:
```
l_variable = [[[2]*3]*4]*5
```This will create a three dimensional array

Yes, it will, but a three dimensional array of what?

Independent lists, or references to a single list?

This would be a good test to run:

[php]l_variable[0][0][0] = 5
print l_variable[/php]

Be careful.

---

### Post by Pipeliner on 2011-09-16
This will be the result of:
```
l_variable = [[[2]*3]*4]*5
```[[[2,2,2], [2,2,2], [2,2,2], [2,2,2]],  [[2,2,2], [2,2,2], [2,2,2], [2,2,2]],[[2,2,2], [2,2,2], [2,2,2], [2,2,2]],[[2,2,2], [2,2,2], [2,2,2], [2,2,2]],[[2,2,2], [2,2,2], [2,2,2], [2,2,2]]]

---

### Post by Senesence on 2011-09-16
Run this:

[php]
l_variable = [[[2]*3]*4]*5
print l_variable

l_variable[0][0][0] = 5
print l_variable
[/php]

See the problem now?

---

### Post by Pipeliner on 2011-09-16
Good Point,

Next time, instead of the hints, just post the error in the thread so everyone can follow.

---

### Post by Senesence on 2011-09-16
> **Pipeliner said:**
> Good Point,

Next time, instead of the hints, just post the error in the thread so everyone can follow.

It's not an error. The syntax is correct, and results in correct behavior, but it might be behavior that you didn't really expect, because you misunderstood the nature of the statement.

Anyway, I think hints are actually preferable to just dumped answers, because they teach people how to run their own tests, and think critically.

Also, it's not like these were "cryptic" hints; I essentially gave you the test to run, which would (with basic analysis) answer the questions posed.

---

### Post by richtheguru on 2012-11-19
I agree with Pipeliner. Critical Thinking is not the same as understanding the nuances behind a specific programming language. I come from a BASIC background where I had a thorough grasp on multi-dimensional arrays. What I'd like is to see some examples of...

1. Declaring a 2d array at top of program  { BASIC:   DIM A(40,40) } 
2. Setting the contents of a position in the array {   LET A(X,Y)=42  }
3. Extracting those contents { LET B = A(X,Y) }
4. something a bit more complex { LET A(X,Y)=A(C,D)+42 }

Any help in this regard would be greatly appreciated.

---

### Post by Tony Flury on 2012-11-19
Using my dictionary idea :

I use a tuple to be the key into the dictionary - the values in the tuple are the indexes in the array

```

grid = {} # Declare it - you don't need to worry about the size.

grid[1,2] = 42 # Set the value at 1,2 to the value 42

a = grid[1,2] # Fetch the value at 1,2

grid[3,4] = grid[1,2] + 4 # add 4 to what is at 1,2 and store in 3,4 

```

Advantages : doesn't use a lot of memory if you have only a few items in your grid - you only store the data you need.. Can be very quick to fetch items. Can use any range of values you want. can easily test for empty positions.

Disadvantages : probably not very efficient if you have a lot of data in the grid.

Remember - python is not BASIC, so it isn't the same - python doesn't really have arrays - it has lists, and dictionaries.

---

### Post by papibe on 2012-11-19
**Old thread closed.**

Please don't reply on an old thread. Create a new one if you have a similar concern.

---

