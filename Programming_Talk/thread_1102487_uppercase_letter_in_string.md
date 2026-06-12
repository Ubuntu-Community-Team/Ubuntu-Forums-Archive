---
title: "uppercase letter in string?"
date: 2009-03-21
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-03-21
How do i check if a string has a uppercase letter in Python??

I searched on the internet but only found stuff that converts Uppercase letters to lower etc??

---

### Post by geirha on 2009-03-21
```
>>> help(str.isupper)
```

---

### Post by 7raTEYdCql on 2009-03-21
I have to return the index of the uppercase alphabet.

---

### Post by 7raTEYdCql on 2009-03-21
isupper checks if all the charachters are upper.

I want to return the index of the character that is upper, not necessary all the characters are upper.

---

### Post by simeon87 on 2009-03-21
> **i.mehrzad said:**
> isupper checks if all the charachters are upper.

I want to return the index of the character that is upper, not necessary all the characters are upper.

```

>>> str.isupper("aaA"[2])
True

```

---

### Post by geirha on 2009-03-21
Then you iterate the string and check character for character.
```

>>> s= "helLo"
>>> for i,c in enumerate(s):
...     if c.isupper():
...         print i
...         break
... 
3
>>> 

```

---

### Post by 7raTEYdCql on 2009-03-21
How useful is the function enumerate. I mean it can be used in which kind of situations?

---

### Post by simeon87 on 2009-03-21
> **i.mehrzad said:**
> How useful is the function enumerate. I mean it can be used in which kind of situations?

Use the documentation? [http://docs.python.org/library/functions.html](http://docs.python.org/library/functions.html)

---

### Post by Can+~ on 2009-03-21
> **i.mehrzad said:**
> How useful is the function enumerate. I mean it can be used in which kind of situations?

The usual python [FONT="Courier New"]for[/FONT] loop iterates over the elements of a given iterable sequence.

[PHP]for x in ("hello", 5, "world", (9, 3.14)):
	print x[/PHP]

```
hello
5
world
(9, 3.1400000000000001)
```

This is usually the only thing you need to do with a sequence, to work with the values it contain, but other times you'll need to also know what is the index in said sequence, that's when enumerate is useful.

Btw, why do you want to know what's the index of the first uppercase character?

---

### Post by ghostdog74 on 2009-03-22
```

>>> import re
>>> print re.search("[A-Z]","aAbxx").end()
2
>>> print re.search("[A-Z]","aabXx").end()
4
>>> print re.search("[A-Z]","aabcX").end()
5
>>> print re.search("[A-Z]","aabcxdTd").end()
7


```

---

### Post by Sprut1 on 2009-03-23
You can also write an listcomp:

```

a = "hello World"
result = [i for i,c in enumerate(a) if c.isupper()]
print result
>>> [6]

```

I'd say this is the python way of doing it.

---

### Post by ghostdog74 on 2009-03-23
```

>>> a = "hello World"
>>> map(str.isupper,a).index(True)
6
>>>        

```

---

