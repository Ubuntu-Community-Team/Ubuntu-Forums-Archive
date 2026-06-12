---
title: "function method for arguments."
date: 2010-03-25
forum: Programming Talk
---

### Post by awinterbreeze77 on 2010-03-25
Python Question:
Need to find and use a method that gets the arguments for a function, so that like funcName.arguments() returns either the value of the arguments assuming
```

def functionName(Imawesome1, Imawesome2):
blah blah blah
```

or the number of arguments called for. Yeah, so is there a method that can return the value of the number of arguments called for by a function?

Please let me know!

Thanks,
Anthony

---

### Post by nvteighen on 2010-03-25
I'm not sure in which situations this may be of use... What are you trying to do? I can't recall any trivial way to do this and there might be a better solution for what you want.

---

### Post by matja on 2010-03-25
Hi,

If I'm not misunderstanding your question, the [inspect]("http://docs.python.org/library/inspect.html#module-inspect") module is what you're looking for.

```

>>> import inspect
>>> def foo(bar, baz=1): pass
... 
>>> inspect.getargspec(foo)
ArgSpec(args=['bar', 'baz'], varargs=None, keywords=None, defaults=(1,))

```

nvteighen still pose an interesting question.

Regards,
Mattias

---

### Post by Can+~ on 2010-03-25
Maybe you're better off with a Decorator? It can read the arguments of a called function before even executing the first line.

---

### Post by nvteighen on 2010-03-26
> **matja said:**
> Hi,

If I'm not misunderstanding your question, the [inspect]("http://docs.python.org/library/inspect.html#module-inspect") module is what you're looking for.

```

>>> import inspect
>>> def foo(bar, baz=1): pass
... 
>>> inspect.getargspec(foo)
ArgSpec(args=['bar', 'baz'], varargs=None, keywords=None, defaults=(1,))

```


Very interesting! Didn't know of that.

> 
nvteighen still pose an interesting question.


My question derives from the fact that inspecting arguments is useless unless you're trying to write some sort of compiler or interpreter... some sort of Python-implemented-on-Python (PyPy?), for example. which doesn't seem to be the case. In all other occasions, the Python interpreter itself will do this for you... pass the arguments and if something went wrong, you'll get an exception.

---

### Post by awinterbreeze77 on 2010-03-26
I admit that pulling the values of arguments of a function (which you input yourself) or getting the number of arguments (which you also input yourself when you wrote the code) might seem totally useless, but it's not. I need to write a standard code for a flexible function; that is, a function that can take any variable (int, string, float, whatever) and do whatever it wants with it/them. For me, the next leap in the evolution of my understanding of python is writing a function that is able to process a wide array of user inputs per function without as little modifying of the code as possible. Is there a better way?

---

### Post by nvteighen on 2010-03-26
> **awinterbreeze77 said:**
> I admit that pulling the values of arguments of a function (which you input yourself) or getting the number of arguments (which you also input yourself when you wrote the code) might seem totally useless, but it's not. I need to write a standard code for a flexible function; that is, a function that can take any variable (int, string, float, whatever) and do whatever it wants with it/them. For me, the next leap in the evolution of my understanding of python is writing a function that is able to process a wide array of user inputs per function without as little modifying of the code as possible. Is there a better way?

Hm... you want a generic function.

Generic functions are a bit double-edged. There are really useful but you can quite easily end up grouping totally different behaivors under a single name and make everything too complex... like making a function be like a swiss-knive that makes too much things for too much different data types.

In Python, the best you can do is use a variable argument list. It's quite easy to do and use:
```

def some_func(*args):
    return reduce(+, args)

```

'args' is just a list... the weird thing is how you declare it by using that *. There is also the possibility to pass that list "spliced" by using *args, so you can pass it as a new argument list.

Then, it'd be just about checking the arguments' types and do what is specified.

Another solution would be that you create your own custom data structures inheriting from the standard classes and extend them with the desired behaivor.

---

