---
title: "python decorators have me stumped"
date: 2008-09-22
forum: Programming Talk
---

### Post by meanburrito920 on 2008-09-22
I've been hearing some stuff about decorators in python recently and I decided to check it out. However, I'm not sure I exactly understand how it works. For instance, I found this code snippet:

[PHP]
>>> def print_args(function):
>>>     def wrapper(*args, **kwargs):
>>>         print 'Arguments:', args, kwargs
>>>         return function(*args, **kwargs)
>>>     return wrapper

>>> @print_args
>>> def write(text):
>>>     print text

>>> write('foo')
Arguments: ('foo',) {}
foo
[/PHP] 

I understand that it is passing the function write() into the function print_args(), but why does print_args return a function? does this basically just pass wrapper back through write() as the text arguement? It seems rather confusing, could anyone please shed some light on the concept?

---

### Post by Wybiral on 2008-09-23
Decorators work like this...

```

def decorator(func):
    return new function

@decorator
def function():
    pass

```

... is exactly the same as ...

```

def decorator(func):
    return new function

def function():
    pass

function = decorator(function)

```

If that helps, that's what the decorator is doing. The use of closure may be confusing you, so you might want to investigate that some if you haven't already (wrapper encloses function into its environment).

---

### Post by pmasiar on 2008-09-23
Decorators is quite advanced design pattern (even if trivial once you understand it), you don't have to dive into it until really ready (say, after at least year of programming, being comfortable solving simpler problems)

For me, "head-first design patterns" was the book explaining patterns in a way I could grok.

---

