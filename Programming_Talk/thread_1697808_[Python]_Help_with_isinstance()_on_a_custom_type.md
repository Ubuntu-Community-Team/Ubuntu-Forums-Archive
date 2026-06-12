---
title: "[Python] Help with isinstance() on a custom type"
date: 2011-03-01
forum: Programming Talk
---

### Post by blazemore on 2011-03-01
I am using BeautifulSoup and have BeautifulSoup.py in the same folder as my program.

Running type() on a specific object I want to check against gives me this output:
```
<class 'BeautifulSoup.NavigableString'>
```

How can I use isinstance on any other item to see if it is of this type?

using isinstance(item, <class 'BeautifulSoup.NavigableString'>) doesn't work.

---

### Post by MadCow108 on 2011-03-01
```
isinstance(obj, BeautifulSoup.NavigableString)
```
or
```
a = BeautifulSoup.NavigableString(...)
isinstance(obj, type(a)
```

---

### Post by blazemore on 2011-03-01
> **MadCow108 said:**
> ```
isinstance(obj, BeautifulSoup.NavigableString)
```or
```
a = BeautifulSoup.NavigableString(...)
isinstance(obj, type(a)
```

The first one gives me something like BeautifulSoup has no attribute NavigableString.
I'll try the second one in a minut.e
Thanks.

---

