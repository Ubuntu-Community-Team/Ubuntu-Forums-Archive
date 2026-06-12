---
title: "Overloading generators in Python 2.5"
date: 2008-10-08
forum: Programming Talk
---

### Post by Hooked2 on 2008-10-08
I've been using the Ubuntu forms for quite some time now - they are an invaluable source of information! I do have a question out there for those well-versed in python:

How do I overload the functionality of all generators? Specifically I'd like to do something like this:

```

def f(): 
  for n in range(5): yield n

for x in f()+f():
   print x

print list(f()+f())

```

And expect that the output would be something like:
```

1
2
3
4
5
1
2
3
4
5
[1,2,3,4,5,1,2,3,4,5]

```

If I could somehow access (overload) the __add__ function of generators that would be ideal, but I can't seem to find out how to do that. I understand that the above example can be done w/o generators, but I would like to have the functionality (and readable code!) that comes from overloading. Thanks for the help!

---

### Post by days_of_ruin on 2008-10-08
You can't operator overload functions.

---

### Post by unutbu on 2008-10-08
[PHP]#!/usr/bin/env python
def f():
    for n in range(1,6): yield n
    for n in range(1,6): yield n

for x in f():
    print x
print list(f())
[/PHP]

Outputs:
```
1
2
3
4
5
1
2
3
4
5
[1, 2, 3, 4, 5, 1, 2, 3, 4, 5]
```

Or, you could do it this way:
[PHP]#!/usr/bin/env python
   
class A():
    def __init__(self,f):
        self.f=f
    def __add__(self,rhs):
        def g():
            for elt in self.f():
                yield elt
            for elt in rhs.f():
                yield elt
        return A(g)
    def __call__(self):
        return self.f()

def f():
    for n in range(1,6): yield n

a=A(f)
for x in (a+a)():
    print x
print list((a+a)())[/PHP]

---

### Post by Hooked2 on 2008-10-08
Thats great ubutnu! I was using a function call of:

```

>>> def f():
	for n in range(1,6): yield n

>>> def multigen(*args):
	for a in args:
		for g in a(): yield g

		
>>> list(multigen(f,f))
[0, 1, 2, 3, 4, 0, 1, 2, 3, 4]
```

This had the visual disadvantage of not being able to see the '+' as a concatenation. The original question still remains, can we add functions onto predefined types? For example the type dict has the member functions pop, keys, etc... and can be called be using the '.' operator. Can one add a function onto all dict datatypes eg. like pop_firstsortedkey(self), or __add__(self, rhs) ?

---

### Post by Hooked2 on 2008-10-08
How did you get colored Python? I was using the CODE tags, but this just creates the block not the smart coloring.

---

### Post by unutbu on 2008-10-08
Objects such as dicts and lists can most definitely be subclassed, just like any other class. For example:

[php]#!/usr/bin/env python  
class subdict(dict):
    def pop_firstsortedkey(self):
        return sorted(self.keys())[0]

c=subdict({'leaping':'lizards','holy':'smokes','happy':'halloween'})
print c
#{'leaping': 'lizards', 'holy': 'smokes', 'happy': 'halloween'}
print c.pop_firstsortedkey()
#happy
[/php]

Functions are objects, too, but I don't know if it is possible to subclass the function type.
You can make any class callable by defining the __call__ method. This is what I did in my previous post. Doing so makes any object sort of like a function, but with the benefits of being an object.

I'm not sure if this answers your question, but I hope it helps.

To add color to your code, click the "php" icon instead of the "#" icon. The php icon is two icons to the right of the # icon.

PS: Here is a nifty trick I learned from LaRoza: if you click the quote button on a post you can see the formatting that was used to generate the post.

---

