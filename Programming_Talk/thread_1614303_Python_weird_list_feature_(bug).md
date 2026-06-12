---
title: "Python weird list feature (bug?)"
date: 2010-11-05
forum: Programming Talk
---

### Post by epicoder on 2010-11-05
I've noticed an interesting behavior in python 2.6 with lists.
If you assign string 'string' to a, then run this code:
```
a='string'
b=a
b=''
print a
```
a will still equal 'string'. However, if a is a list:
```
a=['item1', 'item2']
b=a
del b[0]
print a
```
a will be just ['item2']. While this is rather annoying, it is fortunately easy to work around.

Thoughts?

---

### Post by DaithiF on 2010-11-05
Why is this surprising?  Strings in python are immutable, lists are mutable.  This is the expected behaviour.

---

### Post by DanielWaterworth on 2010-11-05
what you are suggesting is a bug is one of the key principles of python.

---

### Post by dv3500ea on 2010-11-05
This is common to a lot of scripting languages. Ruby and Javascript have this behaviour too.

It is because arrays (and most other objects) are implicitly passed around as references in these languages. Numbers and strings are passed around by value for ease of use more than anything else.

Perl takes a different approach and requires references to be explicit. This makes complex data structures complicated to work with.

---

### Post by epicoder on 2010-11-05
Thanks for all the prompt replies. The reason I was surprised was that in my experience, none of the other programming languages I've used have done this.

SOLVED

---

### Post by raydeen on 2010-11-05
What you need to do is instead of 

```
b = a
```

code it as

```
b = a[::]
```

The second example makes an exact copy of the list object assigned to a and assigns it to b. The first simply assigns both a and b to the same list object in memory.

---

### Post by schauerlich on 2010-11-05
> **sh228 said:**
> I've noticed an interesting behavior in python 2.6 with lists.
If you assign string 'string' to a, then run this code:
```
a='string'
b=a
b=''
print a
```
a will still equal 'string'. However, if a is a list:
```
a=['item1', 'item2']
b=a
del b[0]
print a
```
a will be just ['item2']. While this is rather annoying, it is fortunately easy to work around.

Thoughts?

In python, variables are just names for objects, not the objects themselves. If you're familiar with C or C++, you can think of every variable as a pointer to a generic Object type (ignoring the whole virtual mess). Here's what you're doing:

```

#a = "string"
#b = a
a -- "string"
b --/

# b = ""
a -- "string"
b -- ""

# now, a still refers to "string"
```

The second example:

```
# a = [item1, item2]
# b = a
a -- [item1, item2]
b --/

# del b[0]
a -- [item2]
b --/

# a still refers to the same, now changed, list
```

---

