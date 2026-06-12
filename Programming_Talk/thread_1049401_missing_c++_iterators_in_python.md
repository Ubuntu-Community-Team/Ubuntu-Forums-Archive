---
title: "missing c++ iterators in python"
date: 2009-01-24
forum: Programming Talk
---

### Post by glok_twen on 2009-01-24
hi. been programming in python a while now and very much like the easy of dev and conciseness of the code. however one thing i miss is the ability in c++ to use an iterator to find a specific object in a say a vector (with one stmt). then, to be able to pass that iterator to other routines with one var only (the iterator itself) and still have access to the whole vector in the called routine. in python i have been doing this:

```
pos=0
for pos,abar in enumerate(subList):
    if abar.date==dte.date: break

```

then, passing both pos (my would-be iterator) and also subList around to any routine where i need it.

this is clumsy since i use multiple statements for the find (i'm pretty sure there is a list function i should be using instead of course), but then need to pass around both the position number and also the list variables.

is there a more readable way to do this?

---

### Post by CptPicard on 2009-01-24
Actually I can't quite think of a 1:1 compatible analogue for all cases, but C++ iterators are semantically weak anyway as a matter of principle because C++ does not support closures or continuation-like capture of computation state.

It depends a little on what you're doing, but check out two things -- the Python "iterator protocol" (what you need to support in an object to be able to iterate over some other object) -- this kind of an object works essentially the same as a C++ iterator does -- and then the "yield" statement, which allows you to return from the current frame and go back to it to get the next "return value".

---

### Post by dribeas on 2009-01-24
> **CptPicard said:**
> Actually I can't quite think of a 1:1 compatible analogue for all cases, but C++ iterators are semantically weak anyway as a matter of principle because C++ does not support closures or continuation-like capture of computation state.

It depends a little on what you're doing, but check out two things -- the Python "iterator protocol" (what you need to support in an object to be able to iterate over some other object) -- this kind of an object works essentially the same as a C++ iterator does -- and then the "yield" statement, which allows you to return from the current frame and go back to it to get the next "return value".

Sometimes I have a hard time following your assertions. In this case, I will have to admit my ignorance and ask what is it that make c++ iterators semantically weak and how closures are related to it.

---

### Post by CptPicard on 2009-01-24
> **dribeas said:**
> Sometimes I have a hard time following your assertions. In this case, I will have to admit my ignorance and ask what is it that make c++ iterators semantically weak and how closures are related to it.

Sure, let's go :)

In writing a C++ iterator -- like in writing a Java iterator, or like writing an iterator object in any similar language, or even writing a basic Python iterator -- you have to often write a lot of supporting stuff for bookkeeping... like, think writing a tree walking iterator: you essentially need something like a parent linked tree or a separately maintained stack for your path in the tree, or something like that. The object needs something to know what the "next item" is going to be, and it is then explicitly computed and returned.

In higher-level languages you often have more automatic mechanisms for capturing the state you are in, so that you can just package it into an object and then return there at will. This is of course what continuations do. Python "almost" has continuations but not quite -- you can't get out of deeply nested function calls, "yield" only maintains context for the "top level" call.

Closures are related because, of course, they also capture state (the current scope) and lambdas in particular allow for delayed execution as in Lisp-style lazy lists. You can create an iterable process by consing together the first item and then the delayed rest-of-list. A C++ iterator can be built to yield "the next value" of some computation as well of course, but building this kind of stuff in (say) Lisp just falls out very naturally from the basic building blocks of the language...

---

### Post by Wybiral on 2009-01-24
You know, you can actually just use the 'iter' function to return the iterator of an object and call it's 'next' method until it raises a StopIteration exception.

```

def func(it):
    try:
        a = it.next()
        b = it.next()
        c = it.next()
    except StopIteration:
        raise ValueError('not enough values to iterate')
    return (a + b) * c

it = iter(range(10))

print it.next()
print func(it)

for x in it:
    print x
    
print func(it)

```

---

### Post by CptPicard on 2009-01-24
Yep, it's the iterator protocol that I pointed out...

---

