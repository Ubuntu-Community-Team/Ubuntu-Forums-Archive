---
title: "General Programing question...."
date: 2010-12-24
forum: Programming Talk
---

### Post by stamatiou on 2010-12-24
Hey guys,
I need some help in programing....
I haven't understood when we put these things in the parentheses, it depends on the function-module or whatever we call it what should we put?

---

### Post by squenson on 2010-12-24
Which programming language do you use?

---

### Post by stamatiou on 2010-12-24
> **squenson said:**
> Which programming language do you use?
Python

---

### Post by Arndt on 2010-12-24
> **stamatiou said:**
> Python

An example maybe?

Parentheses are used for many kinds of groupings. Tuples is one, function arguments is another, ordinary precedence grouping in arithmetic is a third.

---

### Post by CptPicard on 2010-12-24
I take it that you're still trying to understand function parameters, no?

Of course they depend on what the function is and what it does. You just need to read the documentation or the function itself to figure out how to use it.

Say, you have a function that adds 1 to any number:

```

def add_one(x):
  return x+1

```

Now, add_one(1) would be two, add_one(2) would be three... so on.

---

