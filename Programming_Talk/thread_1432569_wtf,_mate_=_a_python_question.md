---
title: "wtf, mate? = a python question"
date: 2010-03-17
forum: Programming Talk
---

### Post by vik_2010 on 2010-03-17
I'm new to python, but have a little java experience. I'm writing this method to find the index of the largest number in a list. What's wrong with it?

[PHP]
def getMaxIndex(list):
    index = 0
    maxindex=0
    maxsofar = 0
    while index < len(list):
        if list[index]>maxsofar:
            maxindex=index
            maxsofar=maxindex
            print "maxindex is now",maxindex
        index = index +1
    return maxindex
     
    [/PHP]

---

### Post by schauerlich on 2010-03-17
I believe you want "maxsofar" to be the maximum **value** found so far, not the maximum **index**, right? You store the value of maxindex in maxsofar, meaning it's holding an index instead of a value.

```
[color=#008000]**def**[/color] [color=#0000FF]getMaxIndex[/color]([color=#008000]list[/color]):
    index [color=#666666]=[/color] [color=#666666]0[/color]
    maxindex[color=#666666]=[/color][color=#666666]0[/color]
    maxsofar [color=#666666]=[/color] [color=#666666]0[/color]
    [color=#008000]**while**[/color] index [color=#666666]<[/color] [color=#008000]len[/color]([color=#008000]list[/color]):
        [color=#008000]**if**[/color] [color=#008000]list[/color][index] [color=#666666]>[/color] maxsofar:
            maxindex [color=#666666]=[/color] index
            maxsofar [color=#666666]=[/color] [color=#008000]list[/color][index]
            [color=#008000]**print**[/color] [color=#BA2121]"maxindex is now"[/color], maxindex
        index [color=#666666]+=[/color] [color=#666666]1[/color]
    [color=#008000]**return**[/color] maxindex

```

---

### Post by vik_2010 on 2010-03-17
thanks

---

### Post by diesch on 2010-03-17
A more Pythonic way to write this is

```
def getMaxIndex(list):
    maxindex = 0
    maxsofar = 0
    for index, value in enumerate(list):
        if value > maxsofar:
            maxindex = index
            maxsofar = value
            print "maxindex is now", maxindex
    return maxindex

```A shorter but less clear way is

```

def getMaxIndex2(list):
    return max((b,a) for (a,b) in enumerate(list))[1]

```

And  of course there's
```

def getMaxIndex(list):
    return list.index(max(list))

```

---

### Post by geirha on 2010-03-17
Using enumerate is easier/prettier.
```

def getMaxIndex(list):
  maxvalue = maxindex = 0
  for index, value in enumerate(list):
    if value > maxvalue:
      maxindex, maxvalue = index, value
  return maxindex

```

Combine that with the max function, and you can do it on one line.
```

def getMaxIndex(list):
  return max(enumerate(list), key=lambda x:x[1])[0]

```

Less readable, but can you desipher it?

EDIT: Argh, diech beat me by milliseconds, I'm sure. :)

---

