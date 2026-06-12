---
title: "Python: Looping through multiple lists in same iterations"
date: 2009-10-10
forum: Programming Talk
---

### Post by J V on 2009-10-10
I need to use a for loop to loop through a list, and loop through another list, at the same time:
```
for this in these, that in them:
```Something like that... Only the syntax can't be right, it keeps throwing me "ValueError: too many values to unpack"

Anyone know how to do this? Impossible? Too difficult?

Edit: Nvm, this is working, but now look at this...

```
>>>them = ["test1","test2"]
>>>for this in these, that in them:
>>>    print that
['test1', 'test2']
```

---

### Post by -grubby on 2009-10-10
I don't believe there's any builtin syntax for it, but you might want to try:

[php]
for this, that in zip(these, them):
[/php]

---

### Post by Choad on 2009-10-10
if the lists are the same size

```

for x in range (len(list1)):
  this = list1[x]
  that = list2[x]

```

or if it's a list of lists (a nested list) you can do a nested for loop

```

for this in list1:
  for that in this:

```

---

### Post by J V on 2009-10-10
I tried zip(), no luck, they are the same length, I checked, and they aren't nested lists (Thats another story lol)

---

### Post by -grubby on 2009-10-10
What doesn't work?

```

>>> these = ["a", "list", "of", "items"]
>>> them = ["spam", "spam", "spam", "eggs"]
>>> for this, that in zip(these, them):
...     print this, that
...
a spam
list spam
of spam
items eggs

```

---

### Post by J V on 2009-10-10
The problem is that:
```
>>>them = [['test11','test12'],['test21','test22']]
>>>for this,that in zip(these,them):
>>>    print that
test11,test12
```I don't know what happens, but it somehow manages to turn the sub-list into a string... And not even the one you would expect

---

### Post by Choad on 2009-10-10
```
>>> list1 = (1, 2, 3, 4, 5)
>>> list2 = ('a', 'b', 'c', 'd', 'e')
>>> for x in range(len(list1)):
...     this = list1[x]
...     that = list2[x]
...     print this, that
... 
1 a
2 b
3 c
4 d
5 e
>>> 

```

---

### Post by J V on 2009-10-10
Well that would work, but I already have a lot of sub-lists and I will probably have to spend an hour looking where I have one set of brackets too many and one too little...

Meh, it will do in the meanwhile...

edit: Ok, turns out something is wrong further up the code, I will bump when I find it...

---

### Post by J V on 2009-10-10
Ok! I've tracked it to this line:
```
        for stat in stats:
            print stat
# numbers,moreNumbers,evenMoreNumbers
            stat.split(",") # This line works, but it won't save to the list!
```

---

### Post by unutbu on 2009-10-10
stat is apparently a string with commas in it.
If you want to save the list in the variable stat, then try
```

stat=stat.split(",") returns a list
```

---

### Post by J V on 2009-10-10
The problem is that, while the variable stat should be a reference to stats[count] it actually creates a completley new variable, and, because I'm trying to save it back to stat, after that particular loop is over, the variable gets destroyed... (Well, it gets overwritten and the program looks for it somewhere else anyway)

---

### Post by Can+~ on 2009-10-10
> **J V said:**
> The problem is that, while the variable stat should be a reference to stats[count] it actually creates a completley new variable, and, because I'm trying to save it back to stat, after that particular loop is over, the variable gets destroyed... (Well, it gets overwritten and the program looks for it somewhere else anyway)

You mean doing something like, this?

[PHP]stats = ["1, 2, 3, 4", "A, B, C, D", "I, II, III, IV"]

stats = map(lambda astr: str.split(astr, ","), stats)

print stats[/PHP]

*edit: Noticed an error, I was splitting by " " instead of ",".

---

### Post by J V on 2009-10-10
Ehm... would that output:
```
[["1","2","3","4"],["A","B","C","D"],["I","II","III","IV]]
```

If so, then yes :)

---

### Post by Can+~ on 2009-10-10
> **J V said:**
> Ehm... would that output:
```
[["1","2","3","4"],["A","B","C","D"],["I","II","III","IV]]
```

If so, then yes :)

It does actually print.

```
[['1', ' 2', ' 3', ' 4'], ['A', ' B', ' C', ' D'], ['I', ' II', ' III', ' IV']]
```

And if you mind the spaces, you can remove them (not using strip, as it would require yet another map):

[PHP]stats = map(lambda astr: astr.replace(" ", "").split(","), stats)[/PHP]

Map works by applying a function to each element inside an iterable, in this case, an anonymous function. These are the little python treats for functional programmers.

---

### Post by J V on 2009-10-10
hehe, I know what map does but I can't seem to find anything on lambda :)

Thanks for the line of code, will use!

Edit: There woulden't be any way to make them all integers while we're at it?

---

### Post by Can+~ on 2009-10-10
> **J V said:**
> hehe, I know what map does but I can't seem to find anything on lambda :)

Thanks for the line of code, will use!

Edit: There woulden't be any way to make them all integers while we're at it?

[PHP]# Function that converts to integer for each element inside a list
# I feel that something like this already exists
int_all = lambda alist: map(int, alist)

# Two sets of strings splitted:
stats = map(lambda astr: int_all(astr.split(",")), stats)[/PHP]

One-lined:
[PHP]stats = map(lambda astr: map(int, astr.split(",")), stats)[/PHP]

edit: I realized that I was doing "lambda x: int(x)" when "int" suffices. duh.

---

### Post by J V on 2009-10-10
thanks :)

Anyone know how to catch right-clicks on a button?

---

