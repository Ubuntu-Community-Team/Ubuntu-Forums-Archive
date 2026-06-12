---
title: "about removing duplicate values from python dictionary ?"
date: 2012-08-14
forum: Programming Talk
---

### Post by prismctg on 2012-08-14
Suppose ```
a={1: 'url.txt', 2: x, 3: x, 4: z, 5: 'fb.txt''}
```
and i want this output
```
a={1:'url.txt',2:x,3:'fb.txt'}
``` 

so i basically want to remove duplicate values ; but how ?

---

### Post by the_unforgiven on 2012-08-14
> **prismctg said:**
> Suppose ```
a={1: 'url.txt', 2: x, 3: x, 4: z, 5: 'fb.txt''}
```
and i want this output
```
a={1:'url.txt',2:x,3:'fb.txt'}
``` 

so i basically want to remove duplicate values ; but how ?
You could invert the dict..
something like:
```
inverted = dict()
for (k, v) in a.iteritems():
    if not inverted.has_key(v):
        inverted[v] = k

```
This is to also maintain the first key for a duplicated value -- otherwise, you can skip the "has_key()" check and it'll store only the last key of the duplicated value.

To get back to original dict, you just need to invert this dict again - like:
```
new_dict = dict()
for (k, v) in inverted.iteritems():
    new_dict[v] = k

```

If you don't want to preserve the keys from original dict at all but just want integers as key, you could simply do:
```
new_dict = dict()
i = 1
for v in inverted.iterkeys():
    new_dict[i] = v
    i += 1

``` 

HTH ;)

---

### Post by prismctg on 2012-08-15
thank you so much :)

---

