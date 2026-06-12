---
title: "Python self learning"
date: 2011-04-15
forum: Programming Talk
---

### Post by hdanap on 2011-04-15
Hi, need help,

im trying to rewrite a code using the while loop, and i keep getting out or range error, help

```

def add_matrices(m1, m2):
    """
    >>> a = [[1, 2], [3, 4]]
    >>> b = [[2, 2], [2, 2]]
    >>> add_matrices(a, b)
    [[3, 4], [5, 6]]
    >>> c = [[8, 2], [3, 4], [5, 7]]
    >>> d = [[3, 2], [9, 2], [10, 12]]
    >>> add_matrices(c, d)
    [[11, 4], [12, 6], [15, 19]]
    >>> c
    [[8, 2], [3, 4], [5, 7]]
    >>> d
    [[3, 2], [9, 2], [10, 12]]
    """
        
    matrix = []
    row = []
    j = 0
    i = 0
    while i <= len(m1):
        while j < range(i+1):
            row += [m1[i][j] + m2[i][j]]
            j += 1
        i += 1
        matrix += [row]
    return matrix


```

what am i doing wrong

---

### Post by aromo on 2011-04-15
```
:
:
    while i <= len(m1):
:
:
```

Try replacing that with this:
```
:
:
    while i < len(m1):
:
:
```

---

### Post by hdanap on 2011-04-15
> **aromo said:**
> ```
:
:
    while i <= len(m1):
:
:
```Try replacing that with this:
```
:
:
    while i < len(m1):
:
:
```


Still out of range, thanks

---

### Post by cgroza on 2011-04-15
In what way did you try debugging it? The error says that you are going to far when iterating over an list.
I suggest you to monitor your values and maybe this way you will spot the problem in the loop.

---

### Post by cgroza on 2011-04-15
The line where the error appears would be also very useful.

---

### Post by hdanap on 2011-04-15
> **cgroza said:**
> The line where the error appears would be also very useful.


```

File "vectors.py", line 142, in __main__.add_matrices
Failed example:
    add_matrices(c, d)
Exception raised:
    Traceback (most recent call last):
      File "/usr/lib/python2.6/doctest.py", line 1253, in __run
        compileflags, 1) in test.globs
      File "<doctest __main__.add_matrices[5]>", line 1, in <module>
        add_matrices(c, d)
      File "vectors.py", line 165, in add_matrices
        row += [m1[i][j] + m2[i][j]]
    IndexError: list index out of range

the code underneath is what im trying to rewrite with the while loop, cos i dont understand how the for enumerate() works,
but i understand the while loop, so if i can understand it with the while, i will understand the workings of the enumerate.

Thanks

new_matrix = []
    for i, row in enumerate(m1):
        new_row = []
        for j, m1_value in enumerate(row):
            m2_value = m2[i][j]
            new_row += [m1_value + m2[i][j]]
        new_matrix += [new_row]
    return new_matrix


```

---

### Post by llanitedave on 2011-04-15
What values were you passing into the function?

edit:  Never mind, I see it now.

Anyway, your relation: j < range(i+1)


Makes no sense to me.  "range" creates an iterable list, while "j" is a single integer.
The comparison you give will always be "True", so that your "row += [m1[i][j] + m2[i][j]]"
will end up being 

row += [m1[2][3] + m2[2][3]]

after just a couple of iterations.  Since your matrix has only three items and the contents contain only two, you'll be out of range in a jiffy.

---

### Post by hdanap on 2011-04-16
> **llanitedave said:**
> What values were you passing into the function?

edit:  Never mind, I see it now.

Anyway, your relation: j < range(i+1)


Makes no sense to me.  "range" creates an iterable list, while "j" is a single integer.
The comparison you give will always be "True", so that your "row += [m1[i][j] + m2[i][j]]"
will end up being 

row += [m1[2][3] + m2[2][3]]

after just a couple of iterations.  Since your matrix has only three items and the contents contain only two, you'll be out of range in a jiffy.


Hi, u seem to know ur stuff,

Please u know where or book i can learn tools to solve or come up with algorithm or logical tools for programming, really want to learn but got no money for school and im not to well off, but spent alot of time at the library, learning with no tutor and i just cant grasp this stuff,

I find programming is not the language u use but the logic u apply.

Pls some one point me in a good direction. Im reading how to think like a computer scientist but that doesnt teach the Logical process or algorithmic tools needed.

HEEEEEEEEEEELP!!!!!!!!!!!!!!!!!!!!

---

### Post by llanitedave on 2011-04-16
I don't really "know my stuff".  I'm new at Python too, and I've been out of programming for a number of years.

The only advice I can give about logical approaches to programming are to keep trying it, and keep asking questions like you're doing.  Since you're doing Python, in addition to this forum I'd also recommend 
[http://www.python-forum.org/pythonforum/]("http://www.python-forum.org/pythonforum/")

which has a beginner's section and some smart people posting.  

There's also, on the official Python web site, a listing of "Beginner's Guides for NonProgrammers" which can start you from scratch.

[URL="http://wiki.python.org/moin/BeginnersGuide/NonProgrammers"]
http://wiki.python.org/moin/BeginnersGuide/NonProgrammers[/URL]

There's no shortcut, though.  Getting good at it will take a lot of trial and error, a lot of head scratching, and a lot of asking of what you might think are dumb questions on forums like this.  I've spent hours and hours completely puzzled by things not working, when it turned out to be something simple, or something that was so subtle I still can't quite understand it.  Don't be afraid to make mistakes.  Read a lot of tutorials, and experiment with different ideas.  You'll get there.

---

### Post by hdanap on 2011-04-16
> **llanitedave said:**
> I don't really "know my stuff".  I'm new at Python too, and I've been out of programming for a number of years.

The only advice I can give about logical approaches to programming are to keep trying it, and keep asking questions like you're doing.  Since you're doing Python, in addition to this forum I'd also recommend 
[http://www.python-forum.org/pythonforum/](http://www.python-forum.org/pythonforum/)

which has a beginner's section and some smart people posting.  

There's also, on the official Python web site, a listing of "Beginner's Guides for NonProgrammers" which can start you from scratch.

[URL="http://wiki.python.org/moin/BeginnersGuide/NonProgrammers"]
http://wiki.python.org/moin/BeginnersGuide/NonProgrammers[/URL]

There's no shortcut, though.  Getting good at it will take a lot of trial and error, a lot of head scratching, and a lot of asking of what you might think are dumb questions on forums like this.  I've spent hours and hours completely puzzled by things not working, when it turned out to be something simple, or something that was so subtle I still can't quite understand it.  Don't be afraid to make mistakes.  Read a lot of tutorials, and experiment with different ideas.  You'll get there.

Thanx for that, really needed it

Cheeers

---

### Post by GenBattle on 2011-04-17
> **hdanap said:**
> Hi, need help,

im trying to rewrite a code using the while loop, and i keep getting out or range error, help

```

def add_matrices(m1, m2):
    """
    >>> a = [[1, 2], [3, 4]]
    >>> b = [[2, 2], [2, 2]]
    >>> add_matrices(a, b)
    [[3, 4], [5, 6]]
    >>> c = [[8, 2], [3, 4], [5, 7]]
    >>> d = [[3, 2], [9, 2], [10, 12]]
    >>> add_matrices(c, d)
    [[11, 4], [12, 6], [15, 19]]
    >>> c
    [[8, 2], [3, 4], [5, 7]]
    >>> d
    [[3, 2], [9, 2], [10, 12]]
    """
        
    matrix = []
    row = []
    j = 0
    i = 0
    while i <= len(m1):
        while j < range(i+1):
            row += [m1[i][j] + m2[i][j]]
            j += 1
        i += 1
        matrix += [row]
    return matrix


```

what am i doing wrong

You said you're trying to use a while loop, why not just use a for loop. The easiest way to iterate over lists in python is using something of the form:
```
for i in m1:
```
EDIT: scratch that, this method won't really work for your situation, i see.

In each iteration of such a loop, i will point to the next item in the list.

Some observations from your code:
[LIST]
[*]No matter how you do it, remember that lists/arrays/whatever are always indexed from 0 upwards by default, so the first item in the list is item 0, not item 1. This means your last item is at len(list) - 1. When using a loop condition to cycle through all of the items in the array, you want to cycle from 0 to (len - 1).
[*]The second fault I can spot is that (as someone else pointed out) you're using a range (which return a list of numbers from 0 to the value you specify) in a place that should only contain a single value.
[*]Another thing to note is that a 2D array or list is just a list of lists, so m1[i] will be a list, so you can get the length of the second dimension by checking len(m1[i]).
[*]You only create one row, and then endlessly append items to it, and append it to the your matrix, so all you are doing is re-adding the same array to the matrix multiple times, so the matrix is really just one giant row. Each time you cycle through your row index (let's call it i for now), you need to create a new row.
[*]Python lists have an append method to append an item to the end of the list (although i believe what you are doing does the same thing, more or less).
[/LIST]

So your code should be (if you intend to only use while loops to cycle through the items in m1 and m2, assuming they are both of equal size):

```

matrix = []
j = 0
i = 0
while i < len(m1):
	row = []
	while j < len(m1[i]):
		row.append(m1[i][j] + m2[i][j])
		j += 1
	i += 1
	matrix.append(row)
return matrix

```

Note that it would be wise to also check m1 and m2 have the same dimensions, otherwise you will get an out of range error. Out of range errors basically mean you're trying to access a list/array index that does not exist.

Hopefully this isn't information overload for you, it does take a while to get into programming, but the best way to learn is to drink from the firehose.

If you need more problems to practice with, i recommended project euler ([www.projecteuler.net](www.projecteuler.net)). Keep going with python, it will allow you to get a grip on programming without having to deal with alot of other more advanced stuff you can pick up later.

---

### Post by hdanap on 2011-04-19
> **GenBattle said:**
> You said you're trying to use a while loop, why not just use a for loop. The easiest way to iterate over lists in python is using something of the form:
```
for i in m1:
```EDIT: scratch that, this method won't really work for your situation, i see.

In each iteration of such a loop, i will point to the next item in the list.

Some observations from your code:
[LIST]
[*]No matter how you do it, remember that lists/arrays/whatever are always indexed from 0 upwards by default, so the first item in the list is item 0, not item 1. This means your last item is at len(list) - 1. When using a loop condition to cycle through all of the items in the array, you want to cycle from 0 to (len - 1).
[*]The second fault I can spot is that (as someone else pointed out) you're using a range (which return a list of numbers from 0 to the value you specify) in a place that should only contain a single value.
[*]Another thing to note is that a 2D array or list is just a list of lists, so m1[i] will be a list, so you can get the length of the second dimension by checking len(m1[i]).
[*]You only create one row, and then endlessly append items to it, and append it to the your matrix, so all you are doing is re-adding the same array to the matrix multiple times, so the matrix is really just one giant row. Each time you cycle through your row index (let's call it i for now), you need to create a new row.
[*]Python lists have an append method to append an item to the end of the list (although i believe what you are doing does the same thing, more or less).
[/LIST]

So your code should be (if you intend to only use while loops to cycle through the items in m1 and m2, assuming they are both of equal size):

```

matrix = []
j = 0
i = 0
while i < len(m1):
    row = []
    while j < len(m1[i]):
        row.append(m1[i][j] + m2[i][j])
        j += 1
    i += 1
    matrix.append(row)
return matrix

```Note that it would be wise to also check m1 and m2 have the same dimensions, otherwise you will get an out of range error. Out of range errors basically mean you're trying to access a list/array index that does not exist.

Hopefully this isn't information overload for you, it does take a while to get into programming, but the best way to learn is to drink from the firehose.

If you need more problems to practice with, i recommended project euler ([www.projecteuler.net]("http://www.projecteuler.net")). Keep going with python, it will allow you to get a grip on programming without having to deal with alot of other more advanced stuff you can pick up later.


hey, GenBattle,

thank for the short tutorial, rally helped, thanks for the advise, 

really kool

---

