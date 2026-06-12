---
title: "Input string manipulation in python to output integers"
date: 2009-04-25
forum: Programming Talk
---

### Post by Glenn Jones on 2009-04-25
First off apologies if this has been covered before.

So I recently decided to move away from matlab to scientific python for various reasons. I've had a lot of success up to now particularly with plotting various data using matplotlib. 

I would however like to learn more vanilla python and hence my question.

I have a file I wish to open with have integers separated by a tabs e.g.

19970426          4
19970417        304
19970417        308
19970423         55
19970423         61
19970427        222

I have managed to use python to open the file and print the data using the following:

```

f=open('file_path', 'r')
data=[line.strip() for line in f.readlines()]

```

and data looks like
 
In [35]: data
Out[35]: 
['19970426\t  4',
 '19970417\t304',
 '19970417\t308',
 '19970423\t 55',
 '19970423\t 61',
 '19970427\t222']

what I would like is to do is to convert data to integer array e.g.

data[0,:]=
[19970426,
19970417,
19970417,
19970423,
19970427]

data[1,:]=
[4,
304,
308,
55,
61,
222]

How do I do this? i.e. how do I manipulate the string?

Thanks

Glenn

---

### Post by bgs100 on 2009-04-25
[PHP]f=open('file_path', 'r')
data=[line.strip() for line in f.readlines()]
data2 = [[], []]
for i in data:
    data2[0].append(i.split('\t')[0].replace(' ', ''))
    data2[1].append(i.split('\t')[1].replace(' ', ''))
data = data2[/PHP]

Hope it helps

(Oh, and I have the "replace(' ', '')" because it appeared there was sometimes a space after a tab in your data)

---

### Post by geirha on 2009-04-25
This one, using two list comprehensions, puts the data in a list of tuples of ints...
```

data= [line.split() for line in file('file_path')]
# further convert strings to ints
data= [(int(x), int(y)) for x,y in data]

# Or all on one line:
data= [(int(x),int(y)) for x,y in [line.split() for line in file('file_path')]]
```

---

### Post by Glenn Jones on 2009-05-05
Thanks guys.

---

