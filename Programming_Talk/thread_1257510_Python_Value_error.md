---
title: "Python: Value error"
date: 2009-09-03
forum: Programming Talk
---

### Post by filifunk on 2009-09-03
so I've got historical stock data in a .csv file, and I'm trying to create a script where I can plot it on matplotlib.  In the initial stages of my code:

```


data = []
for row in csv.reader(open('fhco.txt')):
    data.append(row)

header    = data[0]
values    = array(data[1:])


```

when I run it in ipython I get this:

```


---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)

/home/petemondejar/Documents/Programming/fhco.py in <module>()
     17 
     18 header  = data[0]
---> 19 values  = array(data[1:])
     20 
     21 

ValueError: setting an array element with a sequence
WARNING: Failure executing file: <fhco.py>


```


is the data that I'm putting into numpy not the right format maybe?  Any suggestions?

---

### Post by unutbu on 2009-09-03
Check fhco.txt for empty lines, or lines that do not have exactly the right number of comma-separated-values. 

numpy.array tries to predict the shape of the array, but it gets confused if each row does not have the same length.
Printing data could help you see the problem:

[PHP]
data = []
for row in csv.reader(open('fhco.txt')):
    data.append(row)
print(data)[/PHP]

And this code fixes the problem (I think) without you having to manually edit fhco.txt:
[PHP]#!/usr/bin/env python
import csv
from numpy import array
data = []
num_columns=None

for row in csv.reader(open('fhco.txt')):
    if not num_columns:
        data.append(row)
        num_columns=len(row)
    elif len(row)>=num_columns:
        data.append(row[:num_columns])

header    = data[0]
values    = array(data[1:])
print(values)
[/PHP]

---

### Post by filifunk on 2009-09-07
this may be tedious, but could you or someone explain what is going on there?

first off, it works, so thanks a ton!

I don't understand the whole idea behind num_columns.  For instance what does "if not num_columns:" mean?

since num_columns means None then that line iterates through the file and asks "if not None?"

I don't understand.

---

### Post by unutbu on 2009-09-07
When I looked at your original code, I tried to guess what fhco.txt looked like.
Since it was a csv file, it did not take too much creativity to come up with
```

a,b,c
1,2,3,4

5,6,7,8
```

If you save that in fhco.txt, and run the original code, you get 
```

ValueError: setting an array element with a sequence
```

Bingo. That is the same error as the one you posted. I then took a flying leap and assumed that whatever was causing my ValueError was the same as whatever was causing your ValueError.

In the case above, data[1:] is 
[PHP]
[['1', '2', '3', '4'], 
 [], 
 ['5', '6', '7', '8']][/PHP]

The rows do not have the same length. (The middle row is of 0 length!)
[PHP]
array(data[1:])[/PHP]

fails when the rows do not all have the same length.

You could say, the problem is not that your original code is wrong, and rather, it is fhco.txt that is malformed. You could fix the problem by removing all empty lines from fhco.txt and making sure each line has exactly the same number of elements separated by commas. But that is a pain and the program is too brittle. 

Now there are many ways to fix this problem.
If the snag really was just that fhco.txt had some empty lines, then this would have been a simpler way to modify the code to make it less brittle:

[PHP]
#!/usr/bin/env python
import csv
from numpy import array
data = []
for row in csv.reader(open('fhco.txt')):
    if row:
        data.append(row)
header    = data[0]
values    = array(data[1:])
[/PHP]
Here, all I do is add "if row:" before appending row to data.

"if row" is True if the length of row is > 0, and it is false if row equals and empty list. So this tells python to append row to data as long as row is not an empty list (i.e. corresponding to an empty line in fhco.txt).

That solves the problem if the problem with fhco.txt was errant empty lines.

But what if your fhco.txt was really malformed -- something like this:
```

a,b,c
1,2,3,4
5,6,7
```

Now the problem is that some rows have 4 elements, and some rows only have 3.

array must be fed a list of lists, where each row has the same number of elements.
The first row is a header. I guessed this because you wrote
[PHP]
header=data[0][/PHP]

So the header must declare how many columns are expected.
After reading the first line of fhco.txt, we can find out the correct number of columns. That is what num_columns is used for.

I initialize num_columns to start out equal to None:
[PHP]
num_columns=None[/PHP]

Then we enter the for loop:
[PHP]
for row in csv.reader(open('fhco.txt')):
    if not num_columns:
        data.append(row)
        num_columns=len(row)[/PHP]

Since num_columns is None, "if not num_columns" is equivalent to "if not None" and, like a double-negative, "not None" is True. So we enter the if clause the first time through the loop. The row (header) gets appended to data, and we now set num_columns equal to the length of row (i.e. the number of items in the header.)

The next time through the loop, "if not num_columns" becomes something like "if not 4". "not 4" is False because all numbers other than 0 are regarded as True. So for the second and all subsequent times through the loop, this part is skipped:
[PHP]
    if not num_columns:
        data.append(row)
        num_columns=len(row)[/PHP]

and we go on to 
[PHP]
    elif len(row)>=num_columns:
        data.append(row[:num_columns])[/PHP]

Now we require that the length of row is greater than or equal to num_columns.
We need that to be true or else we can't create a well-formed row for the call to array().
On lines where row has at least num_columns elements, row[:num_columns] is a list of the first num_columns elements. We feed that to data. 

Thus the code ensures that each row in data has exactly num_columns elements.
Once that happens, array is happy and no more error.

---

### Post by filifunk on 2009-09-07
this sentence is tripping me up:

"not 4" is False because all numbers other than 0 are regarded as True"

I get that all numbers other than 0 are regarded as True because I went to my python shell and did the whole bool(0) = False and bool(0) = True.

but why does that apply when "not 4" is what's being tested?  If you get a row with 5 columns it just seems like that would be true?

I'm obviously wrong, your explanation is quite thorough and you're kind of my hero right now haha.  Just having trouble making the logical leap.  Anyone else feel free to enter.

---

### Post by unutbu on 2009-09-07
Suppose num_columns = 4 and suppose we wrote
```

if num_columns:
    code block...
```

Then we would expect "code block" to be executed, since, as you say, "all numbers other than 0 are regarded as True". 

So if we insert a "not" into the conditional:
```

if not num_columns:
    code block...

```
then we would now expect "code block" to not be executed. 

On the other hand, when num_columns = None, then we do expect "code block" to be executed.

Notice that in the above I hardly mention true and false values. This is closer to the way I think. I'm not actually trying to do any boolean logic -- I'm trying to avoid it if possible :) All I'm doing is starting with a simple if statement:
```

if num_columns:
```

and then adding a "not" to reverse the way the "if ..." block gets executed.

Hope this helps.

---

