---
title: "[beginner question] python module problem"
date: 2009-11-04
forum: Programming Talk
---

### Post by emigrant on 2009-11-04
hi all,
in one directory i have two files:

[LIST=1]
[*]seqc.py
[*]reference
[/LIST]
seqc.py:
```
#!/usr/bin/python
#file name: seqc.py

name='testinggg'

shoplist=['apple','mango','carrot','banana']

print 'item 0 is', shoplist[0]
print 'item 1 is', shoplist[1]

print 'item -1 is', shoplist[-1]
print 'item -2 is', shoplist[-2]

print 'item 1 to 3 is', shoplist[1:3]
print 'item 2 to end is', shoplist[2:]
print 'item 1 to -1 is', shoplist[1:-1]
print 'item 1 to end is', shoplist[:]

print 'item 2 to -1', shoplist[2:-1]

name='abc'

print 'characters 1 to 3 is', name[1:3]
print 'characters 2 to end is', name [2:]
print 'characters 1 to -1 is', name [1:-1]
print 'characters start to end is', name [:]
```

in the second file reference
what i wanted to do has been commented for the time being(since it did'nt work)
and i put a simple command instead

```
print seqc.name
```

but still not working and i get a weird output which i put at the far bottom:
any help would be greatly appreciated :)


```
#!/usr/bin/python
#file name: reference

import seqc

print seqc.name



#shoplist1=seqc.shoplist

#print shoplist1[:]

```


```
item 0 is apple
item 1 is mango
item -1 is banana
item -2 is carrot
item 1 to 3 is ['mango', 'carrot']
item 2 to end is ['carrot', 'banana']
item 1 to -1 is ['mango', 'carrot']
item 1 to end is ['apple', 'mango', 'carrot', 'banana']
item 2 to -1 ['carrot']
characters 1 to 3 is bc
characters 2 to end is c
characters 1 to -1 is b
characters start to end is abc
abc
```

---

### Post by Arndt on 2009-11-04
> **emigrant said:**
> hi all,
in one directory i have two files:

[LIST=1]
[*]seqc.py
[*]reference
[/LIST]
seqc.py:
```
#!/usr/bin/python
#file name: seqc.py

name='testinggg'

shoplist=['apple','mango','carrot','banana']

print 'item 0 is', shoplist[0]
print 'item 1 is', shoplist[1]

print 'item -1 is', shoplist[-1]
print 'item -2 is', shoplist[-2]

print 'item 1 to 3 is', shoplist[1:3]
print 'item 2 to end is', shoplist[2:]
print 'item 1 to -1 is', shoplist[1:-1]
print 'item 1 to end is', shoplist[:]

print 'item 2 to -1', shoplist[2:-1]

name='abc'

print 'characters 1 to 3 is', name[1:3]
print 'characters 2 to end is', name [2:]
print 'characters 1 to -1 is', name [1:-1]
print 'characters start to end is', name [:]
```

in the second file reference
what i wanted to do has been commented for the time being(since it did'nt work)
and i put a simple command instead

```
print seqc.name
```

but still not working and i get a weird output which i put at the far bottom:
any help would be greatly appreciated :)


```
#!/usr/bin/python
#file name: reference

import seqc

print seqc.name



#shoplist1=seqc.shoplist

#print shoplist1[:]

```


```
item 0 is apple
item 1 is mango
item -1 is banana
item -2 is carrot
item 1 to 3 is ['mango', 'carrot']
item 2 to end is ['carrot', 'banana']
item 1 to -1 is ['mango', 'carrot']
item 1 to end is ['apple', 'mango', 'carrot', 'banana']
item 2 to -1 ['carrot']
characters 1 to 3 is bc
characters 2 to end is c
characters 1 to -1 is b
characters start to end is abc
abc
```

What is it you find weird?

I can use the lines you commented out, without error.

---

### Post by emigrant on 2009-11-04
hi,
my problem is
if i do (in the second file)

```

print seqc.name
```should'nt the output be (importing 'name' from first file):
```
testinggg
```

---

### Post by emigrant on 2009-11-04
from the lines i commented i expect as the output:

```

['apple','mango','carrot','banana']


```

---

### Post by Arndt on 2009-11-04
> **emigrant said:**
> from the lines i commented i expect as the output:

```

['apple','mango','carrot','banana']


```

That's what I get, too.

And seqc.name will show the current value of the variable, not the one it got in its first assignment.

---

### Post by emigrant on 2009-11-04
> **Arndt said:**
> That's what I get, too.

And seqc.name will show the current value of the variable, not the one it got in its first assignment.

yeah. i bit modified the second and now i get what i wanted but with some additional.
the stuff in red, i don't want

```
#!/usr/bin/python
#file name: reference

import seqc

print seqc.name
shoplist1=seqc.shoplist
print shoplist1[:]

```


```
[COLOR=Red]item 0 is apple
item 1 is mango
item -1 is banana
item -2 is carrot
item 1 to 3 is ['mango', 'carrot']
item 2 to end is ['carrot', 'banana']
item 1 to -1 is ['mango', 'carrot']
item 1 to end is ['apple', 'mango', 'carrot', 'banana']
item 2 to -1 ['carrot']
characters 1 to 3 is bc
characters 2 to end is c
characters 1 to -1 is b
characters start to end is abc[/COLOR]
abc
['apple', 'mango', 'carrot', 'banana']

```

---

### Post by Arndt on 2009-11-05
> **emigrant said:**
> yeah. i bit modified the second and now i get what i wanted but with some additional.
the stuff in red, i don't want

```
#!/usr/bin/python
#file name: reference

import seqc

print seqc.name
shoplist1=seqc.shoplist
print shoplist1[:]

```


```
[COLOR=Red]item 0 is apple
item 1 is mango
item -1 is banana
item -2 is carrot
item 1 to 3 is ['mango', 'carrot']
item 2 to end is ['carrot', 'banana']
item 1 to -1 is ['mango', 'carrot']
item 1 to end is ['apple', 'mango', 'carrot', 'banana']
item 2 to -1 ['carrot']
characters 1 to 3 is bc
characters 2 to end is c
characters 1 to -1 is b
characters start to end is abc[/COLOR]
abc
['apple', 'mango', 'carrot', 'banana']

```

Then you have to encapsulate the print lines so that they don't get run when the module is loaded. For example inside a function, or by doing this comparison:

```
if __name__ == "__main__":
```

What is your source for learning about Python?

---

### Post by emigrant on 2009-11-05
hi,
'A byte of python' is my source of learning python:
[http://www.ibiblio.org/g2swap/byteofpython/read/](http://www.ibiblio.org/g2swap/byteofpython/read/)

---

