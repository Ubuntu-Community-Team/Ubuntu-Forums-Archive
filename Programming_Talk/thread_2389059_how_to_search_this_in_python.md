---
title: "how to search this in python"
date: 2018-04-10
forum: Programming Talk
---

### Post by zerop2 on 2018-04-10
there is error when words special characters in any order include special characters in any order

row1 = "search key   $ @ $  words today"
re.sub(r' ',r'(?=$*)(?= *)*', r'key words')
re.findall(re.sub(r' ',r'(?=$*)(?=@*)(?= *)*', r'key words'), row1, re.DOTALL)

>>> re.findall(re.sub(r' ',r'(?=$*)(?=@*)(?= *)*', r'key words'), row1, re.DOTALL)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "C:\Python27\lib\re.py", line 181, in findall
    return _compile(pattern, flags).findall(string)
  File "C:\Python27\lib\re.py", line 251, in _compile
    raise error, v # invalid expression
sre_constants.error: nothing to repeat

---

### Post by &amp;wP*!) on 2018-04-11
Next time when you need help, please state explicitly what you want to achieve exactly and what you got. In your post it is not clear what you want to achieve. Assuming that you want to remove non-ASCII characters in a text like:
```
 "search key $ @ $ words today"
```
Assuming $ and @ are not the only non-ASCII chars which have to be removed, then it is fairly easy:
```
>>> import re
>>> str="**search key** $ @ $ **words today**"
>>> x = re.sub('\W\s+', '', str, count=0, flags=0)
>>> print(x)
search key words today
```

Is that what you want to achieve?

---

