---
title: "Help with creating dictionary of this structure in Python"
date: 2009-11-10
forum: Programming Talk
---

### Post by Tradewind on 2009-11-10
I'm having trouble creating a dictionary of this structure. Based on a .txt file with two columns, I need to create a dictionary where each key is the first column's entries (but repeats won't appear as keys in the dictionary), and values are second column's entries (matched to the first column's entries). Example, this is what the .txt file looks like:

A 1
B 2
B 1
A 4
C 2
C 3
A 5
B 3

And the dictionary would look like this: there would only be three keys, since only A, B, and C appears on the list (repeats won't appear), and each key matched with a list of values consisting of the entries each key is matched with in the .txt file:
{'A': [1, 4, 5], 'B': [1, 2, 3], 'C': [2, 3]}

Thanks in advance if anyone could help me with this!

---

### Post by Can+~ on 2009-11-10
Default dict, I summon thee:

[PHP]#!/usr/bin/env python

from collections import defaultdict

dictfile = open("test.txt")
pairs = defaultdict(list)

for line in dictfile:
	key, value = line.split()
	pairs[key].append(value)


print pairs

dictfile.close()[/PHP]

Or if you prefer a normal dictionary, then change then use setdefault method:

[PHP]#!/usr/bin/env python

dictfile = open("test.txt")
pairs = {}

for line in dictfile:
	key, value = line.split()
	pairs.setdefault(key, []).append(value)

print pairs

dictfile.close()[/PHP]

The first one is faster, the second one is more natural.

*oh, you wanted to avoid repeated values too? Then swap the [] for a set().

---

### Post by Tradewind on 2009-11-11
Oh wow the second one worked perfectly. Thank you.
Could you please explain what it did, especially the "setdefault" part?
Oh and I was just wondering, when I was thinking about this problem I had the idea to just use a for loop to iterate over each pair of entries in the .txt file. Is it possible to create the same dictionary using for/while loops?

---

### Post by Can+~ on 2009-11-11
> **Tradewind said:**
> Oh wow the second one worked perfectly. Thank you.
Could you please explain what it did, especially the "setdefault" part?

```
mydict.setdefault(key, value)
```

setdefault gets the current element under key (passed as the first argument), and if not present, it will first add a default element (second argument), and then return it.

```
mydict.setdefault(key, value).append(...)
```

Therefore: If the key is there, then just return it, and we append to it. If it is not, first create a list inside, then return it, and we append to it. Easy.

> **Tradewind said:**
> Is it possible to create the same dictionary using for/while loops?

Well, yeah:

[PHP]#!/usr/bin/env python

dictfile = open("test.txt")
pairs = {}

for line in dictfile:
	key, value = line.split()
	
	# If key isn't in there, create a new one with an empty list
	if key not in pairs:
		pairs[key] = []
	
	# Now append
	pairs[key].append(value)

print pairs

dictfile.close()
[/PHP]

---

