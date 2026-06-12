---
title: "How &quot;point&quot; to an item in a dictionary using a list with unknown no. dimentions"
date: 2010-02-20
forum: Programming Talk
---

### Post by MadnessRed on 2010-02-20
Hi, this may seem a bit weird but what I would like to know if there is a way to access an item in a dictionary where there is a variable number of dimensions.

Eg, say I had

```

dict = {
  'a' : 0,
  'b' : {
    'c' : 1,
    'd' : { 'e' : 7 }
  }
}

```

I want to select an element from that dictionary, and I have a list giving the location.

eg
```

location1 = ['b','d','e'] 
location2 = ['b',c']
location3 = ['a']

```

using those lists, how could I find and change the value?

I am aware that I could do...
```

val = dict
for r in location1:
    val = cur[r]

```
And that would give me the value, but then how would I change that value in the original dict?

---

### Post by MadnessRed on 2010-02-20
ok, i found a sollution but I dont like it, it seems wrong, it seems that changing a list or dictionary changes its original value

```

val = dict
for r in location1[:-1]:
    val = val[r]
val[location1[-1:][0] = newval

```

---

### Post by Bachstelze on 2010-02-20
This seems to work:

```
firas@momiji ~ % cat test.py 
d = {                        
  'a' : 0,                   
  'b' : {                    
    'c' : 1,                 
    'd' : { 'e' : 7 }        
  }
}

location1 = ['b','d','e']
location2 = ['b','c']
location3 = ['a']

def getItem(d, l):
    for i in l:
        d = d[i]
    return d

def setItem(d, l, x):
    oldd = d
    for i in l[:-1]:
        d = d[i]
    d[l[-1]] = x
    return oldd

print(getItem(d, location1))
print(d)
d = setItem(d, location2, 4)
print(d)
d = setItem(d, location3, 5)
print(d)

firas@momiji ~ % python test.py
7
{'a': 0, 'b': {'c': 1, 'd': {'e': 7}}}
{'a': 0, 'b': {'c': 4, 'd': {'e': 7}}}
{'a': 5, 'b': {'c': 4, 'd': {'e': 7}}}


```

---

### Post by MadnessRed on 2010-02-20
> **Bachstelze said:**
> This seems to work:

```
firas@momiji ~ % cat test.py 
d = {                        
  'a' : 0,                   
  'b' : {                    
    'c' : 1,                 
    'd' : { 'e' : 7 }        
  }
}

location1 = ['b','d','e']
location2 = ['b','c']
location3 = ['a']

def getItem(d, l):
    for i in l:
        d = d[i]
    return d

def setItem(d, l, x):
    oldd = d
    for i in l[:-1]:
        d = d[i]
    d[l[-1]] = x
    return oldd

print(getItem(d, location1))
print(d)
d = setItem(d, location2, 4)
print(d)
d = setItem(d, location3, 5)
print(d)

firas@momiji ~ % python test.py
7
{'a': 0, 'b': {'c': 1, 'd': {'e': 7}}}
{'a': 0, 'b': {'c': 4, 'd': {'e': 7}}}
{'a': 5, 'b': {'c': 4, 'd': {'e': 7}}}


```

ty

---

