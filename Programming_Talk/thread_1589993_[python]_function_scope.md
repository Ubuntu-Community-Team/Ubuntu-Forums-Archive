---
title: "[python] function scope"
date: 2010-10-07
forum: Programming Talk
---

### Post by mo.reina on 2010-10-07
supposing i have the following code, where function N is located in the main function:

```
def main():
l = []

def N(data):
  l.append(data)
```

and i pass function N to a class or outer function, located outside the main function:

```
def do_something(func):
func('1234')
```

what happens to function N?  is the string '1234' passed to function N, which is located in the main function, therefore being appended to the list, or is the code of function N run inside of the outer function, raising an error since there is no list called l in the outer function?

---

### Post by spjackson on 2010-10-07
> **mo.reina said:**
> supposing i have the following code, where function N is located in the main function:

```
def main():
l = []

def N(data):
  l.append(data)
```and i pass function N to a class or outer function, located outside the main function:

```
def do_something(func):
func('1234')
```what happens to function N?  is the string '1234' passed to function N, which is located in the main function, therefore being appended to the list, or is the code of function N run inside of the outer function, raising an error since there is no list called l in the outer function?
The string '1234' is appended to the list declared in N's module. It is fairly simple to demonstrate this with very little more code than you have posted here.

---

### Post by mo.reina on 2010-10-07
> **spjackson said:**
> The string '1234' is appended to the list declared in N's module. It is fairly simple to demonstrate this with very little more code than you have posted here.

yeah that's what has happening when I was running some Twisted code, but I wasn't sure if it was standard python behavior or something that the guys at Twisted came up with.

So basically when you pass a function to another function/class, you're just passing a reference, and the code is executed in the environment that it is written in, not in the function/class where it was passed?

---

### Post by spjackson on 2010-10-07
> **mo.reina said:**
> So basically when you pass a function to another function/class, you're just passing a reference, and the code is executed in the environment that it is written in, not in the function/class where it was passed?
Well, that depends precisely what you mean by "environment". If you are talking about scope and name resolution, then yes, as I've already said. Otherwise, it depends what you mean.

Here's a reference for you [http://docs.python.org/tutorial/classes.html](http://docs.python.org/tutorial/classes.html)

"It is important to realize that scopes are determined textually: the global scope of a function defined in a module is that module’s namespace, no matter from where or by what alias the function is called."

---

### Post by mo.reina on 2010-10-07
> **spjackson said:**
> Well, that depends precisely what you mean by "environment". If you are talking about scope and name resolution, then yes, as I've already said. Otherwise, it depends what you mean.

Here's a reference for you [http://docs.python.org/tutorial/classes.html](http://docs.python.org/tutorial/classes.html)

"It is important to realize that scopes are determined textually: the global scope of a function defined in a module is that module’s namespace, no matter from where or by what alias the function is called."

great that answered my question, thanks.

---

