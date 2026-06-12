---
title: "Sorting in Python"
date: 2009-03-21
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-03-21
I have an enumerated object. And i want to sort it on the second element of the tuples in every element of the resulting list. Can someone help me.

What i am trying to say is:

a=[5,3,6]
b=enumerate(a)
so be will be something like[(0,5),(1,3),(2,6)]

I want to sort b with respect to 5,3,6
so i should get
[(1,3),(0,5),(2,6)]

Can someone help.

---

### Post by Can+~ on 2009-03-21
[FONT="Courier New"]b.sort(lambda x, y: x[1]-y[1])[/FONT]

[http://wiki.python.org/moin/HowTo/Sorting](http://wiki.python.org/moin/HowTo/Sorting)

---

### Post by 7raTEYdCql on 2009-03-21
The fact that i am working on an enumerated object, it doesnt support the function sort.

---

### Post by Can+~ on 2009-03-21
> **i.mehrzad said:**
> The fact that i am working on an enumerated object, it doesnt support the function sort.

```
a = [5, 3, 6]
b = enumerate(a)
b = [i for i in sorted(b, lambda x,y:x[1]-y[1])]

```

Same idea, just using sorted(), since enumerate is basically an iterator, and if you want to iterate over it, remove the generator expression:

```
a = [5, 3, 6]
b = enumerate(a)
for i in sorted(b, lambda x,y:x[1]-y[1]):
	print i
```

---

### Post by 7raTEYdCql on 2009-03-21
Thanks alot

---

### Post by 7raTEYdCql on 2009-03-21
why are you using x[1]-y[1]

Why cant you use any other variable like x[0]-y[0] or x[2]-y[2] or x[2]-y[1]

---

### Post by simeon87 on 2009-03-21
> **i.mehrzad said:**
> why are you using x[1]-y[1]

Why cant you use any other variable like x[0]-y[0] or x[2]-y[2] or x[2]-y[1]

I don't know Python but I'm guessing that it refers to the index of the element in the tuple. You want to sort by the second element in the tuple so that would be the element of x at index 1.

---

### Post by Can+~ on 2009-03-21
> **simeon87 said:**
> I don't know Python but I'm guessing that it refers to the index of the element in the tuple. You want to sort by the second element in the tuple so that would be the element of x at index 1.

That's right.

The default sort() method and function accept a function called "cmp", that basically compares two values, and uses that to sort the sequence.

You can override that function handling an implicit lambda function or an explicit function (def).

In this case, I used it with a lambda which sorts based on the second element.

---

### Post by ghostdog74 on 2009-03-22
```

>>> l=[(0,5),(1,3),(2,6)]
>>> import operator
>>> sorted(l, key=operator.itemgetter(1))
[(1, 3), (0, 5), (2, 6)]


```

---

