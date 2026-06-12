---
title: "How to get list of data[key] of dictionary in Python ?"
date: 2009-02-03
forum: Programming Talk
---

### Post by vietwow on 2009-02-03
Hi all,

I have a dictionary "my" : 

1 a
2 b
3 c
4 d
....


In Python, if I use :

list = my.keys()

I would get a list of all keys in dictionary "my" (inorge all value of keys). Now, I just care about value of key, not key, so I need to get a list of all value of keys in dictionary "my" (inorge all keys). How can I dow this ?

Regards,
Thanx

---

### Post by maximinus_uk on 2009-02-03
Assuming:
```
 my={1:"a",2:"b",3:"c",4:"d"}

```

You can do:

```

foo=[]
for a,b in my.iteritems():
    foo.append(b)
print foo

```

Maybe not the best way, but any answer is better than none!

---

### Post by imdano on 2009-02-03
```
my.values()
```

---

### Post by thornmastr on 2009-02-03
Get a list of all the values that occur in the dictionary.

d.values()

---

