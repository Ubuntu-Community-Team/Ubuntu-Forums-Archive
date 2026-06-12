---
title: "Python thinks &quot;a&quot; isn't &quot;a&quot;?"
date: 2008-03-08
forum: Programming Talk
---

### Post by xelapond on 2008-03-08
Hello everyone, 

I am writing a program in python to allow my AVR Development Board to send a piece of data to my computer over serial.  I am going to pick this up with Python, and then process and act upon that specific piece of data.  I wrote a simple check to test to concept, but it does now work, though it does not loot like there is anything wrong.
```
>>> SerialData = ser.read()
>>> print SerialData
a
>>> if SerialData is "a":
...     print "hello"
...
>>>
```

Does anybody know why Python does not think A is A?

Thanks a ton, 

Alex

---

### Post by ghostdog74 on 2008-03-09
use the "==" operator..

---

### Post by Martin Witte on 2008-03-09
not knowing what your class does - it could be caused by something like this:
[PHP]
#!/usr/bin/env python
class NotWhatItSeemsToBe(object):
    def __init__(self, arg):
        self.content = arg

    def __str__(self):
        return str(self.content)


test = NotWhatItSeemsToBe('a')

if test == 'a':
    print 'we have an a'

if str(test) == 'a':
    print 'the string is an a'
[/PHP]

You can fix that by adding a __eq__ method to your class

[PHP]#!/usr/bin/env python
class NotWhatItSeemsToBe(object):
    def __init__(self, arg):
        self.content = arg

    def __str__(self):
        return str(self.content)

    def __eq__(self, other):
        if self.content == other:
            return True
        else:
            return False
        
test = NotWhatItSeemsToBe('a')

if test == 'a':
    print 'we have an a'

if str(test) == 'a':
    print 'the string is an a'
[/PHP]

---

### Post by xelapond on 2008-03-09
Thanks both of you.  Making it == worked.

Thanks again, 

Alex

---

### Post by Smygis on 2008-03-15
in python is does not check the content of the variable but its identety.

```

>>> aList = [0,1,2]
>>> otherList = aList
>>> aList is otherList
True
>>> otherList.append(10)
>>> aList is otherList
True
>>> aList
[0, 1, 2, 10]
>>> otherList = aList[:]
>>> aList is otherList
False
>>> otherList.pop()
10
>>> otherList
[0, 1, 2]
>>> aList
[0, 1, 2, 10]
>>>

```

---

### Post by Wybiral on 2008-03-15
> **Smygis said:**
> in python is does not check the content of the variable but its identety.

Exactly. Be VERY careful with this. "is" checks to see if two objects are a reference to the same object. Even if you don't assign the variable to the same object, sometimes Python will save memory by referencing the same object for multiple immutable variables, other times it will NOT. Don't rely on this unless you need to check if a variable is a reference to a certain object, for instance:
```

>>> a = [1, 2, 3]
>>> b = [1, 2, 3]
>>> c = a
>>> c is a
True
>>> c is b
False
>>> b is a
False

```

But as I said, it will sometimes reuse immutable objects, especially small integers. It is _not_ reliable and will not usually work for larger integers, it's just a side effect of Pythons memory optimization. Here's an example:

```

>>> a = 1
>>> b = 1
>>> a is b
True
>>> a = 10000
>>> b = 10000
>>> a is b
False

```

The most common use is for things like "a is None" since "None" is an instance of an object that is referenced whenever you assign a variable to "None".

---

### Post by mssever on 2008-03-15
> **Wybiral said:**
> The most common use is for things like "a is None" since "None" is an instance of an object that is referenced whenever you assign a variable to "None".

That makes me curious. Why do Python people frequently recommend a is None over a == None?

---

### Post by LaRoza on 2008-03-15
> **mssever said:**
> That makes me curious. Why do Python people frequently recommend a is None over a == None?

I think there is only one None.

---

### Post by Wybiral on 2008-03-15
Because "None" isn't just value, it's an instance. When you say "a = None" it's like saying "a = b" where "b" is some arbitrary object instance. You can still check if it equals "None", but technically you're still checking if the variables are the same object. Maybe it's just to clarify that you want to know if it IS "None", not if it has a value of "None".

---

### Post by mssever on 2008-03-15
> **LaRoza said:**
> I think there is only one None.

I'm sure, as it would be silly to have more than one (ditto for True and False). But is [FONT=Courier New]is[/FONT] more efficient than [FONT=Courier New]==[/FONT]? Or is it merely a convention?

---

### Post by LaRoza on 2008-03-15
> **mssever said:**
> I'm sure, as it would be silly to have more than one (ditto for True and False). But is [FONT=Courier New]is[/FONT] more efficient than [FONT=Courier New]==[/FONT]? Or is it merely a convention?

Is is probably more efficient, but I doubt it really matters (I think of it as a "pointer" type of deal)

---

### Post by Smygis on 2008-03-19
> **mssever said:**
> I'm sure, as it would be silly to have more than one (ditto for True and False). But is [FONT=Courier New]is[/FONT] more efficient than [FONT=Courier New]==[/FONT]? Or is it merely a convention?

```

>>> import timeit
>>> t = timeit.Timer()
>>> t.timeit(None is None)
9.059906005859375e-06
>>> t.timeit(None == None)
6.9141387939453125e-06
>>> 

```

(Thats not a absolut truth)

---

### Post by Quikee on 2008-03-20
> **Smygis said:**
> ```

>>> import timeit
>>> t = timeit.Timer()
>>> t.timeit(None is None)
9.059906005859375e-06
>>> t.timeit(None == None)
6.9141387939453125e-06
>>> 

```

(Thats not a absolut truth)

For me it is. If I use multiple executions (10M) using '==' takes almost twice the time than 'is'. 

>>> timeit.Timer('None == None').timeit(10000000)
1.034465517743854
>>> timeit.Timer('None is None').timeit(10000000)
0.65500147213109017

However this is so trivial that we should not even be discussing this as nobody will ever notice the 'performance boost'. ;)

---

