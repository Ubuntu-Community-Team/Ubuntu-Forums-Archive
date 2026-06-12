---
title: "Extracting Integers from Strings in Python"
date: 2009-10-27
forum: Programming Talk
---

### Post by bluegreen7hi on 2009-10-27
Hello, 

I am trying to read a set of integers into a list from a data file. The data is as follows:


John 70
Mike 200
Jane 120
Sue 170

I would like to end up with a list of integers, distances = [70, 200, 120, 170].

This is what I have so far:
```

distances = []
text_file = open("test.txt", "r")

for line in text_file:
         for char in line.split(' '):
                  distances.append(char)

print(distances)

```
The output of this is: 
['John', '70\n', 'Mike', '200\n', 'Jane', '120\n', 'Sue', '170\n']

Now how can I remove the names and the line break indicators from this list, and also convert each number to an int?

Am I even close or am I going about this all wrong? I believe this is a fairly simple process, but my numerous Google searches have returned nothing of use to me. Any help would be greatly appreciated.

Thanks!

---

### Post by ghostdog74 on 2009-10-27
```

data=open("file").read().split()
integers = [i for i in data if i.isdigit() ]

```

---

### Post by Arndt on 2009-10-27
> **ghostdog74 said:**
> ```

data=open("file").read().split()
integers = [i for i in data if i.isdigit() ]

```

I'd like some error checking (meaning the program crashes - adapt as you see fit):

```
distances = []
text_file = open("test.txt", "r")

for line in text_file:
    l = line.split()
    distances.append(int(l[1]))

print(distances)
```

---

### Post by ssam on 2009-10-27
i usually use something like

```

distances = []
text_file = open("test.txt", "r")

for line in text_file:
         bits = line.split(' ')
         dist = bits[1].strip() # take the second bit (count from 0), and strip off any whitespace
                  distances.append(dist)

print(distances)

```

---

### Post by cybergalvez on 2009-10-27
give this a try it should give you want you want

```

import re

d = '''
John 70
Mike 200
Jane 120
Sue 170'''

nums = re.compile('.*?(\d+).*?', re.DOTALL|re.MULTILINE)
n = nums.findall(d)

```

this will output ['70', '200', '120', '170'] for n

---

### Post by ghostdog74 on 2009-10-27
> **cybergalvez said:**
> give this a try it should give you want you want

```

import re

d = '''
John 70
Mike 200
Jane 120
Sue 170'''

nums = re.compile('.*?(\d+).*?', re.DOTALL|re.MULTILINE)
n = nums.findall(d)

```

this will output ['70', '200', '120', '170'] for n

regex is overkill. And what is data is like this:
```

John1 70
Mike 200
Jane 120
Sue 170
John2 90

```

---

### Post by Can+~ on 2009-10-27
Python 2.x:
[PHP]#!/usr/bin/env python

input_file = open("asdf.txt")

datadict = {}

for line in input_file:
	name, value = line.strip().rsplit(" ", 1)
	
	datadict[name] = int(value)

print datadict

input_file.close()[/PHP]

Output:
```
{'Jane': 120, 'Mike': 200, 'John': 70, 'Sue': 170}
```

I used a dictionary, so you can access each pair. And used rsplit(" ", 1), so in case there's a composed name, like:

```
This is a name with spaces 300
```

Which my code prints as:

```
{'This is a name with spaces': 300}
```

Assuming that the last thing is always the number.

And if you want only the numbers, then, just swap the dictionary for a list, and append the number (variable "value"), and ignore the other (variable "name").

---

