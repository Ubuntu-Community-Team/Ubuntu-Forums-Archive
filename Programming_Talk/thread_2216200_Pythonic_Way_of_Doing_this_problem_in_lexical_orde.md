---
title: "Pythonic Way of Doing this problem in lexical order"
date: 2014-04-10
forum: Programming Talk
---

### Post by Yozuru on 2014-04-10
[COLOR=#000000][FONT=Verdana]Hello good people, I am doing practice problems for python 3.3. I managed to finish it and got it to work, however, I was wondering if there is a pythonic way of doing this. I understand the basic premise of it but I want to know the inner workings of the program itself.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Here is a pastebin of what I have for the not so pythonic way: [My Code]("http://pastebin.com/uy3LwFKw")
[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]So I was wondering how I would write a function that compared two lists, and skipping the longest common prefix, look at the element in both list where there is a difference. From there, it would either return 0, 1, or -1.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]For example: 
List1 = [0, 1, 2]
List2 = [0, 1, 3][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]This would return as -1.
[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Many thanks in advance for any input you can provide as I really do appreciate working with you all on this.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by lukeiamyourfather on 2014-04-10
There are a lot of ways to do this, this is my take on it. Also what do you mean by skip the longest common prefix?

```

>>> foo = [0,1,2]
>>> bar = [0,1,3]
>>> def compare(first,second):
...     if first > second:
...             return 1
...     elif first < second:
...             return -1
...     else:
...             return 0
... 
>>> map(compare,foo,bar)
[0, 0, -1]

```

---

### Post by ofnuts on 2014-04-10
Use the build-in cmp(), which also works on lists:
```

cmp(foo,bar)

```

A possible solution to do it "by hand" (ie not using cmp() to compare lists), not optimal since it scans the shortest of the lists:

```

cmp(*filter(lambda x:cmp(*x),zip(foo,bar))[0])

```

In slow motion:

[LIST]
[*]zip(foo,bar) makes a list of tuples (one tuple element from each list)
[*]cmp(*x) compare the two elements of the tuples
[*]taking a 0 returned from cmp(...) as False, filter(...) keep only those tuples where elements of foo and bar are unequal
[*][0] takes the first
[*]cmp(*...) re-compares the tuple contents to give the final result
[/LIST]

---

### Post by lukeiamyourfather on 2014-04-11
> **ofnuts said:**
> Use the build-in cmp(), which also works on lists:
```

cmp(foo,bar)

```


Nice! That's much less complicated than mine.

---

### Post by ofnuts on 2014-04-11
> **lukeiamyourfather said:**
> Nice! That's much less complicated than mine.

You solution wasn't complete since it didn't retrieve the first unequal items.
```

(filter(None,map(cmp,foo,bar))+[0])[0]

```

where:
[LIST]
[*]filter(None,...) using identity, keeps only the non-null elements
[*]+[0] makes sure that the filnal list is never empty (which would happen if the inputs are equal)
[*][0] takes the first.
[/LIST]

---

### Post by Yozuru on 2014-04-12
Many thanks to all of you for your inputs. I have a better understanding of the material! Its interesting that there is so many different ways of doing this. 

When I mean skipping the longest common prefix, it skips the numbers that are the same.

---

