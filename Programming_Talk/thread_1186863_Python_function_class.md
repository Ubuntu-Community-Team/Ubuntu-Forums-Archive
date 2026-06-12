---
title: "Python function class"
date: 2009-06-13
forum: Programming Talk
---

### Post by kumoshk on 2009-06-13
Functions are objects in Python. So, I suppose there must be a function class.

How can get a list of the parameters of any given function, in, say, a list?

How can I pass in a list or dictionary such that it is no longer a list or dictionary, but each object in it is passed in as a parameter?

I need to call a function with a static set of parameters&#8212;however, I need a tricky way of getting a variable amount of parameters in it, without having to pass a list or such in directly.

```

def func(self): #self /has/ to be the only parameter
    self.fn(self.args) #this is a dictionary, but I want it split up into the items in it instead
def params(self, *args):
    self.myArgs={}
    i=0
    for x in args:
        self.myArgs[i]=x
        i+=0

```

My first question alludes to an unmentioned solution I have on mind, given the right answer.

---

### Post by delfick on 2009-06-14
> **kumoshk said:**
> How can get a list of the parameters of any given function, in, say, a list?

[http://docs.python.org/library/inspect.html](http://docs.python.org/library/inspect.html)

> How can I pass in a list or dictionary such that it is no longer a list or dictionary, but each object in it is passed in as a parameter?

lets say you have a definition such as 

[php]
def func(a, b, c, d):
    pass
[/php]

and a list called 'theList' defined as [1, 2, 3, 4]

then you can call the function with the contents of theList as position parameters by prepending it with a single Asterisk.

i.e. func(*theList)
would be the same as calling func(theList[0], theList[1], theList[2], theList[3])

To do the same with a dictionary requires two Asterisks.

so say we have a dictionary called 'theDict' defined as {'a' : 1, 'b' : 2, 'c' : 3, 'd' : 4} then we can called the function as

func(**theDict)
which would be the same as calling func(a=theDict['a'], b = theDict['b'], c = theDict['c'], d = theDict['d'])

Note that positional arguements must always come before named arguements, so if you use both notations, then the single asterisk has to before a double asterisk.

so func(*args, **kwargs)

never, func(**kwargs, *args)

> I need to call a function with a static set of parameters—however, I need a tricky way of getting a variable amount of parameters in it, without having to pass a list or such in directly.

define it with a asterisk prepending one of the parameters

for example 

[php]
def func(*params):
    print params

"""calling that with func(1, 2, 3, 4) would print [1, 2, 3, 4] to the screen"""
[/php]

and the same can be done with key word arguements

[php]
def func(**kwargs):
    print kwargs

"""calling that with func(name="ad") would print {'name' : 'ad'}"""
[/php]

> 
```

def func(self): #self /has/ to be the only parameter
    self.fn(self.args) #this is a dictionary, but I want it split up into the items in it instead
def params(self, *args):
    self.myArgs={}
    i=0
    for x in args:
        self.myArgs[i]=x
        i+=0

```

if you have a dictionary, you can get a list of all the keys by calling theDict.keys(). 
A list of all the values by calling theDict.values()

or a list of (key, value) tuples by calling theDict.items()

---

### Post by kumoshk on 2009-06-14
Ah, thanks for the thorough reply!

It works well, now (passing in a list with *listName as a parameter). I was making a timer class, just in case you were curious.

The end result looks something like this:
```

t=timer(3, myFunction, *vars) #seconds, function, function's parameter list
t.start()

```

I couldn't change the number of parameters passed in the run function of the threading.Thread class—so, that's why the question, since it seemed like I had to call my function inside it with a hard-coded parameter list, which wasn't good.

Thanks again!

---

### Post by delfick on 2009-06-14
> **kumoshk said:**
> Ah, thanks for the thorough reply!

no probs :)

> 
I couldn't change the number of parameters passed in the run function of the threading.Thread class—so, that's why the question, since it seemed like I had to call my function inside it with a hard-coded parameter list, which wasn't good.

ahh, that makes sense :)

---

