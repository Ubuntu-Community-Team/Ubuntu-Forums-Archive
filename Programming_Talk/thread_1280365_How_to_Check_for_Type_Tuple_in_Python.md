---
title: "How to Check for Type Tuple in Python?"
date: 2009-10-02
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-10-02
Ey guys, I am wondering how to check for type tuple in Python. I know I can use type() to see what type an object is but I need to be able to check it with an if statement. Here is what I have tried:
```

>>> tup = (98)
>>> type(tup)
<type 'int'> #HUH?
>>> tup = ('98') 
>>> type(tup)
<type 'str'> #HUH?
>>> tup = ('98',0)
>>> type(tup)
<type 'tuple'>
>>> type(tup) == 'tuple'
False
>>> type(tup)[1] == 'tuple'
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'type' object is unsubscriptable

```
What I am doing is obviously not working, how would I go about this? And what about checking for tuples with a single int or string in them(look at the lines that I commented with a "HUH?").

Thanks.

---

### Post by sam191 on 2009-10-02
If you want a tuple with a single string or number you have to include a comma after it.

```
 
>>> tup = (98,)
>>> type(tup)
<type 'tuple'>
>>> tup = ('hello',)
>>> type(tup)
<type 'tuple'>
>>> 


```

hope this helps

---

### Post by wmcbrine on 2009-10-02
> **StunnerAlpha said:**
> What I am doing is obviously not working, how would I go about this?You were close -- just leave off the quotes:

```
>>> tup = (98,)
>>> type(tup)
<type 'tuple'>
>>> type(tup) == 'tuple'
False
>>> type(tup) == tuple
True
```

---

### Post by StunnerAlpha on 2009-10-02
Ah ok, I see. Thanks guys.

---

