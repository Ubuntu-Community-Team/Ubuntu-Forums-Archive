---
title: "Python - Convert word to list"
date: 2007-01-04
forum: Programming Talk
---

### Post by Mithrilhall on 2007-01-04
I would like to take a simple string in python and convert it into a list (1 character per element). Any suggestions?

```


txtTest = "Hello"

txtList[0] = "H"
txtList[1] = "e"
txtList[2] = "l"
txtList[3] = "l"
txtList[4] = "0"


```

---

### Post by meng on 2007-01-04
Have you had any thoughts as to how you would approach this?

---

### Post by pmasiar on 2007-01-04
string *is* list of characters. It is python after all - simple things are easy, hard things are possible :-)

```
>>> test = 'hello'
>>> test[1:3]
'el'

>>> for c in test: print c

h
e
l
l
o
```

Update: I stay corrected, string is *sequence* but not *list*. As meng said, it is not mutable (you cannot assign to elements). Difference depends on what methods you need to use on it. String has these methods: 

>>> dir(test)
['__add__', '__class__', '__contains__', '__delattr__', '__doc__', '__eq__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__getslice__', '__gt__', '__hash__', '__init__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__str__', 'capitalize', 'center', 'count', 'decode', 'encode', 'endswith', 'expandtabs', 'find', 'index', 'isalnum', 'isalpha', 'isdigit', 'islower', 'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'replace', 'rfind', 'rindex', 'rjust', 'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']

It has replace and translate, but no per-item assignment

---

### Post by meng on 2007-01-04
> **pmasiar said:**
> string *is* list of characters
Well I'm no expert, but I believe a list is mutable and a string isn't. So it's only a list of characters in the colloquial sense of the word.

---

### Post by &lt;mawe&gt; on 2007-01-04
Hi!

```
>>> txt = "hello"
>>> txt_list = list(txt)
>>> txt_list
['h', 'e', 'l', 'l', 'o']
```

Regards, mawe

---

### Post by pmasiar on 2007-01-04
Ok, you can use list complehension to convert it to real list if you so desire:

```
>>> parts = [c for c in test]
>>> parts
['h', 'e', 'l', 'l', 'o']
```

---

### Post by ghostdog74 on 2007-01-04
I believe this is what you want?
```

>>> test = 'hello'
>>> list(test)
['h', 'e', 'l', 'l', 'o']

```

---

### Post by Mithrilhall on 2007-01-04
Actually...what you have above works perfectly for what I need. I can't believe it was that easy! ](*,) 

> 
txtText = "Hello"

print txtText[0]

H




Thank you.

---

### Post by &lt;mawe&gt; on 2007-01-04
@ghostdog74: Isn't this exactly what I posted? ;)

---

### Post by pmasiar on 2007-01-04
> **Mithrilhall said:**
> Actually...what you have above works perfectly for what I need. I can't believe it was that easy! ](*,) 



It happens with me all the time: you start coding, you need something, and then you find python has build-in feature for it. In python lore, it is called "Guido's time machine".

I dug couple links for you: [how programming in python is different]("http://dirtsimple.org/2004/12/python-is-not-java.html") and [how the time machine came to existence]("http://mail.python.org/pipermail/python-list/2000-April/032164.html"). :-) Timbot is nick of python developer, presumably Tim Peters, but not believed be human - no human can respond to that many emails *and* write code *and still* [have sense of humor]("http://www.python.org/doc/Humor.html"). Because robots obviously cannot have sense of humor, timbot must be alien :-)

---

### Post by Mithrilhall on 2007-01-04
Thanks for the links pmasiar.

---

### Post by tseliot on 2007-01-04
> **<mawe> said:**
> Hi!

```
>>> txt = "hello"
>>> txt_list = list(txt)
>>> txt_list
['h', 'e', 'l', 'l', 'o']
```

Regards, mawe

OR, if you have time to waste (2 seconds? :p  ) and you don't want to use "list" (if you like "for" better) you can try with:
```
txtTest = 'Hello'
txtList = []

for i in txtTest:
    txtList.append(i)

print txtList
```

---

