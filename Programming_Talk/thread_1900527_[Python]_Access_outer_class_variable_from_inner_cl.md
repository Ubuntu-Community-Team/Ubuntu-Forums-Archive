---
title: "[Python] Access outer class variable from inner class"
date: 2011-12-26
forum: Programming Talk
---

### Post by Frozen Forest on 2011-12-26
It's possible to do this in Python?

[PHP]
class Outer:
    some_var = None
    def init(self, som):
        self.some_var = som

    class Inner:
        def func(self):
            Outer.some_var = 2 # don't work
[/PHP]

---

### Post by nvteighen on 2011-12-26
> **Frozen Forest said:**
> It's possible to do this in Python?

[PHP]
class Outer:
    some_var = None
    def init(self, som):
        self.some_var = som

    class Inner:
        def func(self):
            Outer.some_var = 2 # don't work
[/PHP]

That doesn't make any sense to me... The constructor should be named *__init__*, not *init*... at least if you want your class to be instantiable in the usual way, e.g. *a = Outer(7)*.

For instance, self.some_var is a different variable than Outer.some_var... This happens because you're overwriting the variable when setting it as an instance attribute (*self.some_var*). Look at this:

```

ugi@UGI:~/Escritorio$ python
Python 2.7.2+ (default, Dec  1 2011, 01:55:02) 
[GCC 4.6.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import zz # This is because of how I saved your code...
>>> a = zz.Outer(7)
>>> b = zz.Outer(3)
>>> b.some_var
3
>>> a.some_var
7
>>> a.Inner.func()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unbound method func() must be called with Inner instance as first argument (got nothing instead)
>>> a.Inner().func()
>>> a.some_var
7
>>> b.some_var
3
>>> 

```


Another problem is that with your design, func is an instance method, not a "static method"... In order to call it, one has to create an Inner instance, e.g. an anonymous one like I did above (*a.Inner().func()*). Otherwise, you get that TypeError exception you see above. Again, if it properly called, Inner.func has no effects because the Outer.some_var variable has been shadowed by self.some_var.

This works:
```

class Outer:
    some_var = None
    def __init__(self, som):
        Outer.some_var = som

    class Inner:
        def func(self):
            Outer.some_var = 2

```

However, please notice how the value now changes in both instances *a* and *b*, as expected from a class variable:

```

ugi@UGI:~/Escritorio$ python
Python 2.7.2+ (default, Dec  1 2011, 01:55:02) 
[GCC 4.6.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import zz
>>> a = zz.Outer(3)
>>> a.some_var
3
>>> b = zz.Outer(5)
>>> b.some_var
5
>>> a.some_var
5
>>> a.Inner().func()
>>> a.some_var
2
>>> b.some_var
2
>>> 

```

Anyway, this is terrible design... what are you trying to do?

---

### Post by Frozen Forest on 2011-12-26
Thanks thought it was related to access problem, but as your did work was I able to debug the problem to how I did use *self*. Since I'm new to python did I thought it was the called object and not the calling one. Anyway it's fixed now.

---

### Post by emiller12345 on 2011-12-26
That is interesting.  If I'm not mistaken, some_var is considered a static variable of the Outer class.  Is there a simple way of making it non-static? I'm just curious...

Thanks

---

### Post by nvteighen on 2011-12-26
> **emiller12345 said:**
> That is interesting.  If I'm not mistaken, some_var is considered a static variable of the Outer class.  Is there a simple way of making it non-static? I'm just curious...

Thanks

It is static, but when you create self.some_var, the issue is that you get a non-static variable that shadows the static one.

---

