---
title: "Python can't find the correct constructor?"
date: 2009-07-30
forum: Programming Talk
---

### Post by spupy on 2009-07-30
I have this class:
```
class TClient:
    def __init__(self, options):
        self.__init__(server=options.server, port=options.port, user=options.username, password=options.password)

    def __init__(self, server="127.0.0.1", port=8080, http_proxy="\"\"", username="", password=""):
        self.server = server
        self.port = str(port)
        self.http_proxy = http_proxy
        self.username = username
        self.password = password
```

Is this the correct (python) way to call another constructor of the same class?
Anyway, I first used this line to instantiate the class TClient:
```
client = TClient(server=opts.server, port=opts.port, username=opts.username, password=opts.password)
```
and it's working ok. However, when I try (the variable opts is an OptionParser):
```
client = TClient(options=opts)
```
I though it should call the constructor with the single argument. Python says:
```
TypeError: __init__() got an unexpected keyword argument 'options'
```
Meaning, python tries to pass the opts argument to the wrong constructor (the long one), although I specified the name of argument. If I use:
```
client = TClient(opts)
```
(not naming the argument), python silently calls the wrong constructor.

I already solved the problem another way, but I would like to know why is this behavior occurring. Any thoughts?

---

### Post by unutbu on 2009-07-30
```
class TClient:
    def __init__(self, options):
        ...

    def __init__(self, server="127.0.0.1", port=8080, http_proxy="\"\"", username="", password=""):
        ...
```

This defines TClient.__init__ twice. You can only have one. The Python interpreter will override the first definition with the second, so as far as the Python interpreter is concerned, you've only defined TClient with the long definition:
```

class TClient:
    def __init__(self, server="127.0.0.1", port=8080, http_proxy="\"\"", username="", password=""):
        ...


```

---

### Post by dandaman0061 on 2009-07-30
If you want an "either or" constructor, one way to do it would be with some fancy kwargs logic.

```

class TClient(object):
    def __init__(self, **kwargs):
        if 'options' in kwargs:
            server = options.server
            port = options.port
            # etc...
        else:
            server = kwargs['server']
            port = kwargs['port']
            # etc...

```
Or... a bit more easily extendable
```

class TClient(object):
    _dflt_kwargs = {
        'server': "127.0.0.1",
        'port': "8080",
        'http_proxy': '""',
        'username': "",
        # etc...
    }
    def __init__(self, **kwargs):
        option = kwargs.get('option', None)
        if option is not None:
            for kw, dflt in self._dflt_kwargs.items():
                setattr(self, getattr(option, kw, dflt))
        else:
            for kw, dflt in self._dflt_kwargs.items():
                setattr(self, kwargs.get(kw, dflt))
        # all of the '_dflt_kwargs' will be set on self by this point

```
In the above code... you just have to add to the class attribute '_dflt_kwargs' if you ever want to add more attrs later.

---

### Post by spupy on 2009-07-31
> **unutbu said:**
> This defines TClient.__init__ twice. You can only have one. The Python interpreter will override the first definition with the second, so as far as the Python interpreter is concerned, you've only defined TClient with the long definition:

I see. Is it not strange to have only one constructor? What is the idea behind this?

Btw, in my case (the opts var is an OptionParser), the solution is pretty elegant:
```
def __init__(self, options):
        self.__dict__ = vars(options)
```

---

### Post by unutbu on 2009-07-31
Perhaps we have different mental models of what the constructor is supposed to do.
Maybe you have experience in a language with which I do not?

In python, the real "constructor" is the __new__ method. When you create a class instance,
```

client = TClient(...)
```

Python first calls TClient.__new__(). This method is expected to return an object -- the class instance "client". If anything deserves to be called a constructor, I suppose __new__ would be it.

Next TClient.__init__() is called. This is an initializer, not a constructor.
Notice that the first argument to __init__(self,...) is self. self is the class instance that __new__() created. self has already been created by the time __init__ gets called.
The commands you put in __init__(...) shape, mold, or initialize (rather than construct) the class instance.

So with this mental model, do you see how (at least in Python) it is natural to have only one __init__ method?

```

def __init__(self, options):
        self.__dict__ = vars(options)
```

That's a neat trick you are using to update self's attributes with those from OptionParser. However, I think you still have to decide on one and only one call signature for __init__:
```

def __init__(self, options):
```

or
```

def __init__(self, server="127.0.0.1", port=8080, http_proxy="\"\"", username="", password=""):

```

---

### Post by spupy on 2009-07-31
> **unutbu said:**
> Perhaps we have different mental models of what the constructor is supposed to do.
Maybe you have experience in a language with which I do not?

In python, the real "constructor" is the __new__ method. When you create a class instance,
```

client = TClient(...)
```

Python first calls TClient.__new__(). This method is expected to return an object -- the class instance "client". If anything deserves to be called a constructor, I suppose __new__ would be it.

Next TClient.__init__() is called. This is an initializer, not a constructor.
Notice that the first argument to __init__(self,...) is self. self is the class instance that __new__() created. self has already been created by the time __init__ gets called.
The commands you put in __init__(...) shape, mold, or initialize (rather than construct) the class instance.

So with this mental model, do you see how (at least in Python) it is natural to have only one __init__ method?

```

def __init__(self, options):
        self.__dict__ = vars(options)
```

Thank you very much for your explanation. Now it makes sense.

> **unutbu said:**
> 

That's a neat trick you are using to update self's attributes with those from OptionParser. However, I think you still have to decide on one and only one call signature for __init__:
```

def __init__(self, options):
```

or
```

def __init__(self, server="127.0.0.1", port=8080, http_proxy="\"\"", username="", password=""):

```

Yeah, I did decide - only the shorter one is left.

---

### Post by nvteighen on 2009-08-01
It seems like you were trying to emulate C++ polymorphic constructors or something like that... In C++ you have to declare several constructors to do this kind of stuff because C++ is statically typed, so it needs to know the parameters' types at compile time... 

In Python, that's nonsense, as it's dynamically typed... So one unique constructor that determines its own behaivor at runtime is all you need :)

---

