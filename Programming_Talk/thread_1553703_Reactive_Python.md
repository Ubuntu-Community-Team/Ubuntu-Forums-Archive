---
title: "Reactive Python"
date: 2010-08-15
forum: Programming Talk
---

### Post by DanielWaterworth on 2010-08-15
Hi, I'm looking for feedback on an idea I've had. It's a (very) short library for dataflow programming in python. Here's a quick example of the API:

```
from dataflow import ReactiveVariable, reactive

a = ReactiveVariable('')
b = ReactiveVariable('')
out = ReactiveVariable('')

@reactive
def compose():
    out.value = a.value + ' ' + b.value

a.value = 'hello'
b.value = 'world'
print out.value
```It has some limitations. I'm certain I haven't covered all the edge cases. Also, it won't work well with cyclical dependencies. I'm still working out the best way to solve this.

Anyway, here's the initial version, licensed under GPLv3:

```
import types

class ReactiveVariable(object):
    def __init__(self, value=None):
        self._value = value
        self.callbacks = []
    
    def get_value(self):
        return self._value
    
    def set_value(self, value):
        if value != self._value:
            self._value = value
            for callback in self.callbacks:
                callback()
    
    value = property(get_value, set_value)

def reactive(fn, top=None):
    if not top:
        top = fn
    for name in fn.func_code.co_names:
        v = fn.func_globals.get(name)
        if isinstance(v, ReactiveVariable):
            v.callbacks.append(top)
        elif isinstance(v, types.FunctionType):
            reactive(v, top)
    return fn
```

edit: I've just thought up an even better API. I'll implement it tomorrow [=

---

### Post by worseisworser on 2010-08-15
Here's my dataflow/reactive/MVC library for Common Lisp:

```

SW-MVC> (let* ((a &#955;I"Hello")
               (b &#955;I"World")
               (out &#955;I(catstr ~a ~b)))
          ~out)
"HelloWorld"

SW-MVC> (let* ((a &#955;I"Hello")
               (b &#955;I"World")
               (out &#955;I(catstr ~a ~b)))
          (pprint ~out)
          (setf ~a "Goodbye")
          (pprint ~out))

"HelloWorld"
"GoodbyeWorld"

SW-MVC> (let* ((a &#955;I"Hello")
               (b &#955;I"World")
               (out &#955;I(with1 (catstr ~a ~b)
                        (format t "New result for OUT is ~A~%" it))))
          (setf ~a "Goodbye")
          ~out)
New result for OUT is HelloWorld
New result for OUT is GoodbyeWorld
"GoodbyeWorld"

SW-MVC>
```


..or same thing, but using objects (omg, OOP; the horror! .. *sigh* :) ):

```

SW-MVC> (defclass flow-test (self-ref)
          ((a :initform "Hello")
           (b :initform "World")
           (out :initform &#8593;&#955;F(catstr ¤a ¤b)))
          
          (:metaclass mvc-class))
#<MVC-CLASS FLOW-TEST>

SW-MVC> (with-object (make-instance 'flow-test)
          ¤out)
"HelloWorld"

SW-MVC> (with-object (make-instance 'flow-test)
          (setf ¤a "Goodbye")
          ¤out)
"GoodbyeWorld"


SW-MVC> (defclass flow-test (self-ref)
          ((a :initform "Hello")
           (b :initform "World")
           (out :initform &#8593;&#955;F(with1 (catstr ¤a ¤b)
                               (format t "New result for OUT is ~A~%" it))))
          
          (:metaclass mvc-class))
#<MVC-CLASS FLOW-TEST>

SW-MVC> (with-object (make-instance 'flow-test)
          (setf ¤a "Goodbye")
          ¤out)
New result for OUT is HelloWorld
New result for OUT is GoodbyeWorld
"GoodbyeWorld"

SW-MVC> 

```

It is thread safe; it uses STM ( [http://en.wikipedia.org/wiki/Software_transactional_memory](http://en.wikipedia.org/wiki/Software_transactional_memory) ) and can make use of multiple CPUs and cores as data and events flows or pulses through its networks.

It handles circular dependencies in a sane manner, and it is licensed under AGPLv3, here: [http://github.com/lnostdal/SW-MVC](http://github.com/lnostdal/SW-MVC)

edit: It has a lot of other more or less hidden, cool features. ;)

---

### Post by DanielWaterworth on 2010-08-15
I wish I understood LISP better. It has too many parenthesis for my liking.

---

### Post by worseisworser on 2010-08-15
Actually, I've heard Lisp tends to have fewer () characters than *equivalent* code in e.g. C/C++/Java.

C/C++/Java of course uses a mix of (){}[],; characters replacing the use of mostly only ( and ) in Lisp.

The weird characters I use are not common in Lisp; my libraries add that syntax -- though, I can type e.g.  *&#955;I(catstr ...)*  as  *(mk-icell (catstr ...))*  instead -- using "only standard Lisp syntax" if I want.

edit: Oh, and if you like AI, stuff like Lisp is a total blast of course! :) ..be sure to check out the PAIP book.

---

### Post by schauerlich on 2010-08-15
> **DanielWaterworth said:**
> I wish I understood LISP better. It has too many parenthesis for my liking.

You get used to it. Most decent editors make managing parentheses a whole lot easier.

also:
[Common Lisp](http://www.gigamonkeys.com/book/)
[Scheme](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-4.html#%_toc_start)

Have fun.

---

