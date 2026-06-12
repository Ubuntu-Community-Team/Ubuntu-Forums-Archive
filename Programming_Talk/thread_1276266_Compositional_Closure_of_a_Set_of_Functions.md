---
title: "Compositional Closure of a Set of Functions"
date: 2009-09-26
forum: Programming Talk
---

### Post by eabod on 2009-09-26
The Python procedure below is intended to compositionally close ([http://en.wikipedia.org/wiki/Closure_(mathematics)]("http://en.wikipedia.org/wiki/Closure_(mathematics)")) a given set of functions x. The idea is to take each 2-element (i.e. 2-function) combination from x and simply add the (left and right) compositions of the two functions to x. Once that is done, x is compared with what it was before all the compositions were added to it, and if x changed, the process is repeated on the changed x. This continues until throwing in all the pairwise compositions of functions in x does not change x. Why is the code below not achieving what I desire? (My only suspicion is that the break statement in the except clause is not returning the execution to the outer while loop as I intended.)

```

    def compclosure(x): #x is a set of functions
        from itertools import combinations
        xp = set([])
        while xp != x:
            combos = combinations(x,2)
            xp=x
            while True:
                try:
                    s=combos.next()
                    x.add(compose(s[0],s[1]))
                    x.add(compose(s[1],s[0]))
                except StopIteration:
                    break
                    #if there is no s.next(), then
                    #go back to the outer while loop
        return x

```

If someone has a better (e.g. more efficient) way to find the compositional closure of a given set of functions, I'd be delighted to hear it.

Any other comments are also welcome.

---

### Post by unutbu on 2009-09-26
[list]
[*] If f is a function in x, compose(f,f) would be in the closure of x.
As it stands, I don't think combinations(x,2) picks up this possibility, since 
combinations generates pairs of distinct elements.

[*]I don't think you can use set equality to compare xp with x
 
[PHP]while xp != x:[/PHP]

Python doesn't know when two functions are equal. For example,
[PHP]f = lambda z: z
g = lambda z: z
assert(f==g)[/PHP]

raises an AssertionError because id(f)!=id(g). You may need to make a Function class and define the __eq__ method to define when two functions are supposed to be equal. That could be quite difficult for arbitrary functions!
[*] Just out of curiosity, could you post the definition of the compose function and an example of the elements of x?
[/list]

---

### Post by eabod on 2009-09-26
Thanks for the reply. I address each of your bullets individually below.

> **unutbu said:**
> [list]
[*] If f is a function in x, compose(f,f) would be in the closure of x.
As it stands, I don't think combinations(x,2) picks up this possibility, since 
combinations generates pairs of distinct elements.
[/list]

You're right, I need to fix that.

> **unutbu said:**
> [list]
[*]I don't think you can use set equality to compare xp with x
 
[PHP]while xp != x:[/PHP]

Python doesn't know when two functions are equal. For example,
[PHP]f = lambda z: z
g = lambda z: z
assert(f==g)[/PHP]

raises an AssertionError because id(f)!=id(g). You may need to make a Function class and define the __eq__ method to define when two functions are supposed to be equal. That could be quite difficult for arbitrary functions!
[/list]

The statement
```
while xp != x:
```
is actually comparing two *sets* of functions. I tested the != logical operator on a few sets and it seems to work.

> **unutbu said:**
> [list]
[*] Just out of curiosity, could you post the definition of the compose function and an example of the elements of x?
[/list]

These are functions from the three element set {0,1,2} to itself. There are 27 of them and I've represented them by ordered triples (i.e. 3-tuples). Thus the input of my procedure, x, is a subset of {(a,b,c): 0 <= a,b,c <= 26}. The compose function looks like
```

def compose (f, g):
    t = f[g[0]],f[g[1]],f[g[2]]
    return t

```

---

### Post by Can+~ on 2009-09-26
[PHP]#!/usr/bin/env python

def compose(funca, funcb):
	"""Compose to functions f(...) and g(...) into (fog)(...)"""
	def composed(*args, **kaargs):
		return funca(funcb(*args, **kaargs))
	
	return composed

def ncompose(*funcs, **kfuncs):
	"""Compose a group of functions into (fogoh...)(...)"""
	# Pop the last element
	composed = funcs[-1]
	funcs = funcs[0:-1]
	
	# Pack the last function, into the following 
	for func in reversed(funcs):
		composed = compose(func, composed)
		

	return composed

f = lambda x: x+1
g = lambda x: x*2
h = lambda x: x-3

# ((10-3)*2)+1 = 15
print (ncompose(f, g, h))(10)

# Closure test (typical base+offset closure)
closurator = lambda base: lambda x: base+x
x = closurator(10)

# (10+5)*2 = 30
print (ncompose(g, x))(5)
[/PHP]

Took me a while, but there you go. N-ary composition.

*edited: tested with closures, surprised that it worked fine.

---

### Post by unutbu on 2009-09-26
I think this works, but I don't have a clear idea on how to test its correctness.
[PHP]
def compclosure(x):
    from itertools import product
    xp = set()
    while xp != x:
        xp=x.copy()
        combos = product(x,x)
        for s in combos:
            x.add(compose(s[0],s[1]))            
    return xp
[/PHP]

---

### Post by Can+~ on 2009-09-26
Damnit, how did I write all that code, and not realize that I was replicating the "reduce" function.

This is with reduce:

[PHP]def compose(funca, funcb):
	"""Compose functions f(...) and g(...) into (fog)(...)"""
	return lambda *args, **kaargs: funca(funcb(*args, **kaargs))

def ncompose(*funcs, **kfuncs):
    """Compose a group of functions into (fogoh...)(...)"""
    return reduce(compose, funcs)  [/PHP]

As simple as it gets, compose is a function that takes two functions and produce one, using "reduce" over a group of functions passed should've been my first reaction, instead I did some ugly hack.

*edit: Even smaller!

---

### Post by unutbu on 2009-09-26
Edit: hehe, you beat me to it. :)

Can+~, that's pretty neat. 
There is also this:
[PHP]
def ncompose(*funcs):
    return reduce(compose,funcs)
[/PHP]

---

### Post by Can+~ on 2009-09-26
> **unutbu said:**
> Can+~, that's pretty neat. 
There is also this:
[PHP]
def ncompose(*funcs):
    return reduce(compose,funcs)
[/PHP]

I also realized of my mistake :lolflag:, though you posted one second too late.

---

### Post by Can+~ on 2009-09-26
[PHP]def compose(*funcs, **kfuncs):
    """Compose a group of functions into (fogoh...)(...)"""
    return reduce(lambda f, g: lambda *args, **kaargs: f(g(*args, **kaargs)), funcs)[/PHP]

Now it became a three-liner, if you want to go to new extremes, then:

[PHP]compose = lambda *funcs: reduce(lambda f, g: lambda *args, **kaargs: f(g(*args, **kaargs)), funcs)[/PHP]

one-lined. Almost lispean, although, pretty hard on the eyes, maybe with some spaces it would look more friendly.

---

### Post by eabod on 2009-09-26
I'm not trying to compose functions, but rather to close a set of functions under the operation of pairwise composition.

---

### Post by Can+~ on 2009-09-26
> **eabod said:**
> I'm not trying to compose functions, but rather to close a set of functions under the operation of pairwise composition.

Oh, so you want combinations of compositions.

Well, let me review your original code first:

[PHP]            while True:
                try:
                    s=combos.next()
                    x.add(compose(s[0],s[1]))
                    x.add(compose(s[1],s[0]))
                except StopIteration:
                    break
                    #if there is no s.next(), then
                    #go back to the outer while loop[/PHP]

StopIteration is not meant to be used like this. StopIteration is an internal exception used by for loops, for objects which have the .next method.

So, your code, swapping this while for a for:

[PHP]    def compclosure(x): #x is a set of functions
        from itertools import combinations
        xp = set([])
        while xp != x:
            xp=x
            for s in combinations(x, 2):
                x.add(compose(s[0],s[1]))
                x.add(compose(s[1],s[0]))
        return x[/PHP]

Which becomes more readable. (You should also move the import statement outside the function)

Now, I'm not sure about your algorithm. Do you want to try every combination of two functions until... what?

---

### Post by eabod on 2009-09-26
> **eabod said:**
> I'm not trying to compose functions, but rather to close a set of functions under the operation of pairwise composition.
Of course, that requires the composition of functions, but actually only binary composition, since composition is associative. I have the binary composition procedure defined already (called "compose"; see my 2nd post above). The code I posted originally uses the compose procedure.

---

### Post by Can+~ on 2009-09-26
Your algorithm would do something like:

input: (f, g, h)
[PHP]
x = (empty)
is (f, g, h) equal to x? No, then:
    x=(fof, fog, foh, gof, gog, goh, hof, hog, hoh)
is (f, g, h) equal to x? No, then:
    <infinite loop>[/PHP]

Also, python can't compare "functions":

[PHP]a = lambda x: x+1
b = lambda x: x+1

if a == b:
	print "Equal"[/PHP]

So I'm not sure what are you trying to accomplish.

---

### Post by eabod on 2009-09-27
> **Can+~ said:**
> 
Also, python can't compare "functions":

[PHP]a = lambda x: x+1
b = lambda x: x+1

if a == b:
	print "Equal"[/PHP]

So I'm not sure what are you trying to accomplish.

The functions in question are from the three element set {0,1,2} to itself. There are 27 of them and I've represented them by ordered triples (i.e. 3-tuples); e.g. (1,2,0) is the function 0->1, 1->2, 2->0. Thus the input of my procedure, x, is a subset of {(a,b,c): 0 <= a,b,c <= 26}. So I think in this case, Python can compare these "functions".

> **Can+~ said:**
> Your algorithm would do something like:

input: (f, g, h)
[PHP]
x = (empty)
is (f, g, h) equal to x? No, then:
    x=(fof, fog, foh, gof, gog, goh, hof, hog, hoh)
is (f, g, h) equal to x? No, then:
    <infinite loop>[/PHP]


Are you saying that my code results in an infinite loop? If so, why? I think that since there are only 27 functions, the loop must terminate eventually.

I think I just realized the problem. I intended xp to remain the same as the previous x (hence the name xp), so I could use it to compare with the updated x. It seems that whenever x is updated, so is xp (so x and xp are apparently point to the same thing). How can I create a copy of x that won't be updated whenever x is?

By the way, I took the advice of your previous post. I didn't know that I could do 
[PHP]
        ...
        combos = combinations(x,2)
        for s in combos:
        ...
[/PHP]
So thanks.

---

### Post by m649B on 2009-09-27
I think this works:

```
def lstComp(setlst):
    newset = setlst
    for i in setlst.copy():
        for j in setlst.copy():
            newset.add(compose(i, j))
    if newset == setlst:
        return newset
    else:
        lstComp(newset)
```setlst is a Set object; I had to import Set at the beginning. "compose" is your compose function from the first post. Is this what you were thinking of?

edit: Does this work differently for versions 2.6 and up? I'm using 2.5.2.

---

### Post by eabod on 2009-09-27
What's the difference between Set and set?

---

### Post by eabod on 2009-09-27
Ok, I think using the .copy() method resolved my problem. Thanks everyone.

---

### Post by CptPicard on 2009-09-27
> **unutbu said:**
> You may need to make a Function class and define the __eq__ method to define when two functions are supposed to be equal. That could be quite difficult for arbitrary functions!

It is computationally intractable in the general case actually...

---

### Post by Can+~ on 2009-09-27
> **eabod said:**
> The functions in question are from the three element set {0,1,2} to itself. There are 27 of them and I've represented them by ordered triples (i.e. 3-tuples); e.g. (1,2,0) is the function 0->1, 1->2, 2->0. Thus the input of my procedure, x, is a subset of {(a,b,c): 0 <= a,b,c <= 26}. So I think in this case, Python can compare these "functions"

Well, I didn't know about the nature of the elements inside the input set, so I assumed this were real functions (lambda, def) and not mappings.

Great that you got it working.

---

