---
title: "function arguments in python"
date: 2009-01-31
forum: Programming Talk
---

### Post by cguy on 2009-01-31
I have defined a class name C:

class C:
.............
<--end-->

Next I want to define a function which takes 3 arguments:
- an integer
- a string
- a class C type

How do I define it?

---

### Post by geirha on 2009-01-31
```
def func(a,b,c):
  if type(a) is not int or type(b) is not str or not isinstance(c,C):
    print "bad arguments etc..."
  ...

```

---

### Post by cguy on 2009-01-31
Thanks a million!


-------


Excuse me, but could you please check if you can connect to python.org?
Is the site down?

I couldn't connect to it at all in the past two weeks.

---

### Post by Martin Witte on 2009-01-31
This [link ]("http://www.python.org/") works, and  [this ]("http://python.org/")too

---

### Post by CptPicard on 2009-01-31
Mind you while that is a technically correct answer, it is philosophically wrong. :) In a duck typed language you just assume what is generally correct -- that your types are appropriate. This way you get automatic genericness. When you do need to check for conformance to some interface, it is recommended to check not the actual type of of object, but the existence of the specific attribute/function (using has_attr) you intend to make use of. This way, again, you keep your code as generic as possible.

---

### Post by cguy on 2009-01-31
@Martin: Not on my Ubuntu... :( (What could be the problem?) Thanks for the help!

Could you post a code snippet, CptPiccard?

---

### Post by Wybiral on 2009-01-31
> **cguy said:**
> @Martin: Not on my Ubuntu... :( (What could be the problem?) Thanks for the help!

Could you post a code snippet, CptPiccard?

I think what CptPicard means is that you don't want to rely on type-tests most of the time... This puts you back, essentially, in the world of static typing (but without the added compile-time benefit). What you want to do is rely on attributes, a more flexible approach.

For example, this func will work just fine on any instances that have a method, 'update':
```

def func(obj):
    if hasattr(obj, 'update'):
        return obj.update()
    else:
        raise ValueError('func requires an argument with an update method')

```

This way, existing and future types can use the same interface... Not to mention, the method can literally be assigned to some instance at any point in runtime.

---

### Post by Martin Witte on 2009-02-01
> **cguy said:**
> @Martin: Not on my Ubuntu... :( (What could be the problem?) Thanks for the help!

does it work via this [ link]("http://downforeveryoneorjustme.com/#")?

---

### Post by cguy on 2009-02-01
> It's just you. [www.python.org](www.python.org) is up.

This is really weird.

I connected a laptop to the same internet wire and I could open the page from it.

---

### Post by geirha on 2009-02-01
Sounds like there could be something in the web browser blocking the page then. Try opening it in a different web browser on the machine it isn't working on. In a terminal run ```
w3m http://www.python.org
```

---

### Post by cguy on 2009-02-01
Opening the page with w3m works, but neither opera or firefox can do it.
However, unlike opera, firefox can fetch the page title. (JUST the page title)

---

