---
title: "[Python] 'is' vs '=='"
date: 2009-05-03
forum: Programming Talk
---

### Post by Sinkingships7 on 2009-05-03
Can someone tell me the difference between
```

if x == y:
    // code

```
and
```

if x is y:
    // code

```
?

And, in this case, is there a difference between str objects and numbers being compared with 'is'?

---

### Post by Reiger on 2009-05-03
Google "Python is operator"; and behold:
[quote="http://stackoverflow.com/questions/306313/python-is-operator-behaves-unexpectedly-with-integers"] 
7 
 	
It depends on whether you're looking to see if 2 things are equal, or the same object. 

"is" checks to see if they are the same object, not just equal. The small ints are probably pointing to the same memory location for space efficiency 
In [29]: a = 3
In [30]: b = 3
In [31]: id(a)
Out[31]: 500729144
In [32]: id(b)
Out[32]: 500729144

You should use "==" to compare equality of arbitrary objects. You can specify the behavior with the __eq__, and __ne__ attributes.[/quote]:P

---

### Post by Sinkingships7 on 2009-05-03
> **Reiger said:**
> Google "Python is operator"; and behold:
:P

I thought it might have something to do with object comparison. Thank you!

I tried "Python difference is ==". I admit, that wasn't a very good attempt. :p

---

### Post by shadow_code on 2009-05-04
"is" is generally best to use when testing against the built-in constants. (None, False, True).

Noting that you can use "is not" for !=

---

### Post by imdano on 2009-05-04
> **shadow_code said:**
> "is" is generally best to use when testing against the built-in constants. (None, False, True).

Noting that you can use "is not" for !=Usually you don't want to use 'is' for True and False.  If you have a variable 'var' and you want to do a boolean check on it, 99% of the time you just want ```
if var:
    # do something
```Otherwise you'll run into things like this
```
>>> 1 is True
False
>>> 1 == True
True

```Most of the time you probably want a boolean comparison on 1 to be True.

---

### Post by regomodo on 2009-05-04
#

---

### Post by salvachn on 2009-05-06
'is' will first check the object types and then the values.
'==' will check only the values, not the type.

---

### Post by dandaman0061 on 2009-05-06
> **salvachn said:**
> 'is' will first check the object types and then the values.
'==' will check only the values, not the type.

Ummm... do you have a source on that?  I was pretty sure that 'is' checks the id() value of the objects.  Where most objects' id points to their address (or unique value).  'None' is an example of a singleton object where there will always be only one instance (thus only one id) so using 'is' works correctly.

```

a = [1]
b = [1]
print a == b  # True
print a is b  # False

print id(a)   # 3086172620L (on my machine this time)
print id(b)   # 3086163372L (same stipulation)

```

They are both the same type and contain the same value, BUT they are different instances so 'is' fails.

---

### Post by nvteighen on 2009-05-06
Heck... **is** compares the **id()** and returns True if equal. In other words, it's a pointer comparator. **==** just compares the values.

```

>>> class Test(object):
...     def __init__(self):
...             self.a = 9
... 
>>> a = Test()
>>> b = Test()
>>> a is b
False
>>> a == b
False
>>> c = a # copying reference!
>>> c is a
True
>>> id(a)
156339468
>>> id(b)
156339596
>>> id(c) # equal to id(a)
156339468

```

---

