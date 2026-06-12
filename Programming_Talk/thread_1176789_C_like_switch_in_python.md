---
title: "C like switch in python"
date: 2009-06-02
forum: Programming Talk
---

### Post by mvalviar on 2009-06-02
There is no switch (as in switch program structure in C like languages). How can I implement a switch with 'fall through' 'cases'?

---

### Post by Can+~ on 2009-06-02
I guess a dictionary in which multiple keys point to the same function/data

[PHP]# Sample functions
def square(x):
    return x**2

def double(x):
    return x*2

# Switch-case analog ("a" and "b" are "fall through", "c" is not)
opdict = {"a":square, "b":square, "c":double}

# Example (random access O(1))
print opdict["b"](5)

# Example 2 (checking everything)
for operation in "abc":
    print operation, opdict[operation](3)[/PHP]

Also notice that

```
>>> opdict["a"] is opdict["b"]
True
```

So both refer to the same address.

---

### Post by benj1 on 2009-06-02
whats wrong with

if x:
elif y:
elif z:
else:

ive seen something done with a dictionary af lambdas aswell

like:
result = { 'a': lambda val: val*5, 'b': lambda val: val*10}[case](val)

but whats the point

---

### Post by crdlb on 2009-06-02
> **benj1 said:**
> but whats the point

For one, it's much faster to do a single dictionary lookup. It can also help with code organization, particularly if you want to pass arguments to each function or class. For very simple cases, if-elif-elif-else is fine though.

---

### Post by simeon87 on 2009-06-02
elif can be used to write a switch, see [http://docs.python.org/tutorial/controlflow.html#if-statements](http://docs.python.org/tutorial/controlflow.html#if-statements).

---

### Post by benj1 on 2009-06-02
> **crdlb said:**
> For one, it's much faster to do a single dictionary lookup. It can also help with code organization, particularly if you want to pass arguments to each function or class. For very simple cases, if-elif-elif-else is fine though.

very true, but as far as i know for C (don't know about other languages) there isn't a speed advantage in most cases, so in that case the 'pythonic' alternative would be if else, but i think im just splitting hairs so ignore me :)

---

### Post by delfick on 2009-06-03
you could always use a combination of try..catch and a dictionary.

[php]
key = 4
try:
  result = {
    1 : 'one',
    2 : 'two',
    3 : 'three',
    4 : 'four',
    5 : 'five',
    6 : 'six',
    7 : 'seven',
    8 : 'eight',
  }[key]
except KeyError:
  result = 'one < key > eight'
[/php]

bad example, but that's beside the point :p

---

