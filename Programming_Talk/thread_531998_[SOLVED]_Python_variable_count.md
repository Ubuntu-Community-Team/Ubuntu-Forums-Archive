---
title: "[SOLVED] Python variable count"
date: 2007-08-22
forum: Programming Talk
---

### Post by DamjanDimitrioski on 2007-08-22
In almost all the programming languages, the command ++ will make some variable to have +1 value.
Now, how can i use that in Python, instead of g = g+1?

---

### Post by Nekiruhs on 2007-08-22
g += 1

---

### Post by DamjanDimitrioski on 2007-08-22
Sorry i can't understand it, please give me an example!

---

### Post by LaRoza on 2007-08-22
> **DamjanDimitrioski said:**
> Sorry i can't understand it, please give me an example!

These snippets do the same thing:

```

while (x < 5)
{
   ++ x;
}

```


In Python:
```

while (x <5):
    +(+x)

```
Also, you can use
x+=1

The above shorthand is common to increment number by any number, with most operations, so

x = x + 1 == x += 1 

x = x *2 == x *= 2

Most languages have this, like C++, Python, and other modern languages.

---

### Post by DamjanDimitrioski on 2007-08-22
Thanks, i will try it now.

---

### Post by pmasiar on 2007-08-22
Python does not have ++x, because it is against "explicit is better than implicit" rule: how much you want to increase x? So you need to say explicitly: add one: "x += 1"

---

