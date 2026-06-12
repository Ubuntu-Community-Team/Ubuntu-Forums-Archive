---
title: "[python] For Statement Problem - Creating a Simple Guitar Chord Dictionary"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-07-20
Hi,
I am trying to create a simple Chord Dictionary for a bit of fun.

This is what I have done...

```



a = 1     
b = 3
c = 4
d = 6
e = 8
fsharp = 10
aminor = a,c,e
# a b c d e and fsharp are the notes I need  
# aminor consists of three notes a,c,e which equals (1,4,8)


```

To get bminor I tried this statement... 

```

for i in aminor:
...      bminor = i + 2
...      print bminor

3
6
10 
# when I print bminor I get 10 but I want (3,6,10)


```

What can I do to get the answer I am looking for?
Do you have any other tips on what I could add to my chord dictionary or any useful math statements?

Thanks in advance!

---

### Post by ibutho on 2008-07-20
Change
```
aminor = a,c,e
```
to
```
aminor = [a,c,e]
```

---

### Post by The Cog on 2008-07-20
Try this:
```
>>> def transpose(notes, shift):
...     result = []
...     for note in notes:
...             result.append(note + shift)
...     return result
... 
>>> transpose(aminor, 2)
[3, 6, 10]
>>> for note in transpose(aminor, 2):
...     print note
... 
3
6
10
>>> 

```
You can transpose with negative numbers too, to shift downwards.

---

### Post by pluckypigeon on 2008-07-20
> **ibutho said:**
> Change
```
aminor = a,c,e
```
to
```
aminor = [a,c,e]
```

This didn't work.

---

### Post by pluckypigeon on 2008-07-20
> **The Cog said:**
> Try this:
```
>>> def transpose(notes, shift):
...     result = []
...     for note in notes:
...             result.append(note + shift)
...     return result
... 
>>> transpose(aminor, 2)
[3, 6, 10]
>>> for note in transpose(aminor, 2):
...     print note
... 
3
6
10
>>> 

```
You can transpose with negative numbers too, to shift downwards.

how would i get this to print bminor??

---

### Post by ibutho on 2008-07-20
> **pluckypigeon said:**
> This didn't work.

My apologies, I misunderstood your first post. I thought you just wanted to print the values. You can use lists to solve your problem. The code posted by The Cog or the one below should do
```

#!/usr/bin/env python

a = 1     
b = 3
c = 4
d = 6
e = 8

aminor = [a,c,e]
bminor = []
# a b c d e and fsharp are the notes I need  
# aminor consists of three notes a,c,e which equals (1,4,8)

for i in aminor:
      i = i + 2
      bminor.append(i)
      
#to print the values
for i in bminor:
	print i 

```

---

### Post by The Cog on 2008-07-20
[QUOTEhow would i get this to print bminor??[/QUOTE]

How about:
[B]bminor = transpose(aminor, 2)
print "B minor =", bminor[/B]
Otherwise, I don't think I understand where you are stuck.

---

### Post by ghostdog74 on 2008-07-20
> **pluckypigeon said:**
> 
What can I do to get the answer I am looking for?
Do you have any other tips on what I could add to my chord dictionary or any useful math statements?

Thanks in advance!

[code]
chords={}
chords["a"]=1
chords["b"]=3
chords["c"]=4
chords["d"]=6
chords["e"]=8
aminor=["a","c","e"]
....
#you do the rest

---

### Post by pluckypigeon on 2008-07-20
> **ibutho said:**
> 
```

#!/usr/bin/env python

a = 1     
b = 3
c = 4
d = 6
e = 8

aminor = [a,c,e]
bminor = []
# a b c d e and fsharp are the notes I need  
# aminor consists of three notes a,c,e which equals (1,4,8)

for i in aminor:
      i = i + 2
      bminor.append(i)
      
#to print the values
for i in bminor:
	print i 

```

I prefer to work with this as I understand it the most. Thanks to everyone for their help. I will study all of the statements.

---

