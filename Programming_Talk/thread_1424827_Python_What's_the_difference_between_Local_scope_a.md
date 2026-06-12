---
title: "Python: What's the difference between Local scope and Enclosing scope?"
date: 2010-03-08
forum: Programming Talk
---

### Post by koala114 on 2010-03-08
Python searchs name from the local (L) scope, then the local scopes of any enclosing (E) defs and lambdas, then the global (G) scope, and then the built-in (B) scope.

---

### Post by Tony Flury on 2010-03-08
The difference is :

Local scope - the scope of the function/method (i think)
Enclosing scope - scope of the module, class or containing function (in the case of closures etc).

---

### Post by Reiger on 2010-03-08
Hmm. I think the following examples &#8220;get&#8221; the difference between the scopes across:
```

def bar():
  # code here

def foo(): 
  #code here
  def bar():
    # code here

```

Similarly:
```

def x():
  # code...

def foo():
  x = # code ...
  # code...
  lambda x: # code...
  #code ...

```

---

