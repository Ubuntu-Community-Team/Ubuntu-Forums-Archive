---
title: "[Python3] Select [1]  from map() iterator"
date: 2012-01-05
forum: Programming Talk
---

### Post by kramer65 on 2012-01-05
Hello,


My title is maybe a bit awkward, but I didn't really know how to describe it differently.

I have a dictionary from which I want to take some numbers with an "if in" construct:
```
some_dict = {'2001-10-11': 12, '2001-10-12': 10.5, '2001-10-13': 11.7, '2001-10-14': 12.1, }

datum = '2010-02-13'
if datum in some_dict:
    print(some_dict[datum])
else:
    # do something else
```
    
I now put the whole construction with which I made the dictionary into a map() construct which returns an iteration which in python2 (when map() still created a list instead of an iterator) would look like this (just to show it):
```
python2_maplist = [('2001-10-11', 12), ('2001-10-12', 10.5), ('2001-10-13' 11.7), ('2001-10-14', 12.1)]
```

At this point I don't know however, how I would check if some date is in there and if it is in there how to do something with the second part (python2_maplist[that iteration][1]).

I kind of have a hard time explaining this, but I hope I you guys understand.

All tips are welcome!

---

### Post by Bachstelze on 2012-01-05
I'm not sure if that's what you want, but you can use [font=monospace]in[/font] on an iterator:

```
firas@av104151 ~ % python3
Python 3.2 (r32:88452, Feb 20 2011, 11:12:31) 
[GCC 4.2.1 (Apple Inc. build 5664)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> t = [0, 1, 2, 3]
>>> '1' in map(str, t)
True
>>> '4' in map(str, t)
False

```

alternatively, you can construct a list by using [font=monospace]list()[/font]:

```
>>> list(map(str, t))
['0', '1', '2', '3']

```

---

### Post by kramer65 on 2012-01-05
As I think of it I just though of quite a simple solution:

```

datum = '2010-02-13'
for i, j in map_object:
    if i == datum:
        print(j)
        break

```

Since I need to loop over the map object a zillion times looping over it only seems really stupid. Isn't there a faster way to do this?

---

### Post by Bachstelze on 2012-01-05
Since a Python dictionary is basically a hash table, the most efficient way is probably to just to access the data in a try/except and catch the KeyError exception to indicate that the data is not there.

---

### Post by kramer65 on 2012-01-05
> **Bachstelze said:**
> I'm not sure if that's what you want, but you can use [font=monospace]in[/font] on an iterator:

```
firas@av104151 ~ % python3
Python 3.2 (r32:88452, Feb 20 2011, 11:12:31) 
[GCC 4.2.1 (Apple Inc. build 5664)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> t = [0, 1, 2, 3]
>>> '1' in map(str, t)
True
>>> '4' in map(str, t)
False

```

alternatively, you can construct a list by using [font=monospace]list()[/font]:

```
>>> list(map(str, t))
['0', '1', '2', '3']

```

I understand your solutions. The thing is that there are always two things linked together: a date and a number. The lists you create just consist of single values though.

The following for example, doesn't really work:

```
>>> some_list = [1,2,3,4]
>>> def plus10(x):
	return x, x + 10

>>> map_object = map(plus10, some_list)
>>> two = 2
>>> if two in map_object:
	print('true')
else:
	print('nope')

	
nope
```

---

### Post by Bachstelze on 2012-01-05
So something like this

```
>>> def foo(dict, date):
...     try:
...         data = dict[date]
...         print(data)
...     except KeyError:
...         print('Not found')
... 
>>> some_dict = {'2001-10-11': 12, '2001-10-12': 10.5, '2001-10-13': 11.7, '2001-10-14': 12.1, }
>>> foo(some_dict, '2001-10-12')
10.5
>>> foo(some_dict, '2001-10-18')
Not found

```

---

### Post by kramer65 on 2012-01-05
Yes indeed. Only that I don't want to know it for a dictionary, but for a map object which you create with map() (in python 3).
So something you create with the following code:

```

>>> some_list = [1,2,3,4]
>>> def plus10(x):
	return x, x + 10

>>> map_object = map(plus10, some_list)

```
From the map_object I now want to print the second returned thing for where the first thing is 3 (so the result would be 13).

My problems are that an iterable (which a map object in python 3 is) is not subscriptable and that I cannot do a "if x in map_object" for a map object created with map() in python3.

---

### Post by lukeiamyourfather on 2012-01-05
Someone correct me if I'm wrong but an iterator inherently can't be addressed like a list (e.g. foo[1]) because nothing exists yet. There's only a method to return the next item of the iterator.

---

### Post by Bachstelze on 2012-01-05
> **kramer65 said:**
> Yes indeed. Only that I don't want to know it for a dictionary, but for a map object which you create with map() (in python 3).
So something you create with the following code:

```

>>> some_list = [1,2,3,4]
>>> def plus10(x):
	return x, x + 10

>>> map_object = map(plus10, some_list)

```
From the map_object I now want to print the second returned thing for where the first thing is 3 (so the result would be 13).

My problems are that an iterable (which a map object in python 3 is) is not subscriptable and that I cannot do a "if x in map_object" for a map object created with map() in python3.

Then your solution in #3 should work. You can probably make it more time-efficient if you are willing to trade off some space, by creating a list out of the iterator with list(), then sorting it and using a binary search algorithm.

*EDIT:* or even constructing a dict and using #6. You would need to run some benchmark to compare the efficiency of all those methods, though, if you want to know for sure which is the most efficient.

*EDIT 2:* but that's assuming the dataset doesn't change too often...

---

### Post by kramer65 on 2012-01-05
> **Bachstelze said:**
> 
*EDIT 2:* but that's assuming the dataset doesn't change too often...
To start with your last point. No the dataset doesn't change while the program runs.

> **Bachstelze said:**
> You would need to run some benchmark to compare the efficiency of all those methods, though, if you want to know for sure which is the most efficient.

I am going to do that. I am pretty surprised though, that there isn't an easy way to do this.

What is (apart from the lower memory consumption while running) actually the big advantage with iterables that they changed the result of map() from lists to iterables?

---

### Post by simeon87 on 2012-01-05
Just change it to a dict:

```
data_dict = dict([i for i in map_object]])
```

After that, you can do:

```
if date in data_dict:
    ....

```

> What is (apart from the lower memory consumption while running) actually the big advantage with iterables that they changed the result of map() from lists to iterables?

Often, you just need the values and you don't need them all in a list. And if you still want a list, you can convert the map object into a list yourself. The benefits are lower memory consumption and computation time (many values don't need to be computed if you stop the loop earlier).

---

