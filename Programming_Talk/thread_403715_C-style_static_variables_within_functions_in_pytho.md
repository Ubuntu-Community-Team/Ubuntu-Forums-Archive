---
title: "C-style static variables within functions in python"
date: 2007-04-07
forum: Programming Talk
---

### Post by MadeR on 2007-04-07
I need something like this in python:
```
void f(void)
{
    static int i = 0;
    i++;
}

```
without using a class.

I found another guy having the same problem
[http://mail.python.org/pipermail/tutor/2002-December/018964.html](http://mail.python.org/pipermail/tutor/2002-December/018964.html)

someone suggested a solution like this:
```

def x(a=[0]):
    a[0] += 1
    print a

```

First of all I do not understand why the value of a is preserved between each call.
Second: why the following code does not work:
```

def x(a=0):
    a += 1
    print a

```
Why python stores somewhere a set/tuple/list/dictionary/etc and not simple C-types?
Because the low level implementation in C relies on classes and not on native simple type?
In this case, what happens in Jhyton?

---

### Post by pmasiar on 2007-04-07
Static variable is somewhat tricky: it is not local (so cannot be allocated on the stack) but also not global (value is available only inside certain function).

Guido decided there are many different usages for that, and many different ways to implement it, optimized for special cases. I found nice implementation using decorators - tricky :-)

Very simple and straightforward way is to use "protected" global variable. Of course Python assumes that programmers are consenting adults, so there is no enforced protection (and I will ignore any complaints about it - complain to pydev list :-) ) but here it goes:

```

_gstat = 10     # define global variable as "protected" - begins with _
def gstat(init=10):
    global _gstat # use global variable - derived from function name
    print _gstat
    _gstat += 1

```

> **MadeR said:**
> 
someone suggested a solution like this:
```

def x(a=[0]):
    a[0] += 1
    print a

```

First of all I do not understand why the value of a is preserved between each call.


Very clever solution. It creates anonymous list, which is referred only inside function. Value is preserved (and  not garbage collected), because reference to it is used inside function.

> 
Second: why the following code does not work:
```

def x(a=0):
    a += 1
    print a

```

because scalar 0 is passed by value, not by reference.

> 
Why python stores somewhere a set/tuple/list/dictionary/etc and not simple C-types?
Because the low level implementation in C relies on classes and not on native simple type?

There is no "simple" type for tuple etc in C - they are all objects, allocated at heap.

> In this case, what happens in Jhyton?

It is Jyton :-) and basic behavior like passing object by reference, should be the same.

---

### Post by duff on 2007-04-07
Since functions are objects anyway, you can access it's __dict__ member variable ```
#!/usr/bin/env python

def foo(x):
	foo.__dict__.setdefault('count', 0)
	foo.count += 1
	print foo.count, x

foo('foo')
foo('bar')
```

---

### Post by MadeR on 2007-04-08
> **pmasiar said:**
> 



Very clever solution. It creates anonymous list, which is referred only inside function. Value is preserved (and  not garbage collected), because reference to it is used inside function.


because scalar 0 is passed by value, not by reference.

well here the question is: why that value is preserved between function calls?
even though default values belong to the parent environment (and I do not understand the reason why), it should be delete when function call ends and the reference should be destroyed (default value should be used only upon function call; and yes, this way leads to having a reserved word ("persistent"?) to implement local static variables) 
OR
the same should occur also to simple types such as int, float and so on.
where do I err?

---

### Post by pmasiar on 2007-04-08
> **MadeR said:**
> why that value is preserved between function calls?
even though default values belong to the parent environment (and I do not understand the reason why),

Because default value is not a scalar 0, but a list. List is passed by reference, so reference to (anonymous) list, created in enclosing function, is kept in function.

>  it should be delete[d] when function call ends and the reference should be destroyed (default value should be used only upon function call; 

Not so. Default value is kept in case any function call will not provide argument - it is interpreted and no way to tell when function call will provide argument and when not (and default will be used). 

Trick is, default value is a reference, and inside of the function body you modify referenced object. Reference stays the same, you change referenced object - it is allowed.

> the same should occur also to simple types such as int, float 

No. Scalars are passed by value. In fact, even objects are passed by value: value is reference (address in memory).

Imagine if scalars were passed by reference too:

```

def increment(val):
    val += 1

increment(1)  # create literal constant 1 
              # function will increment it
print 1       # prints 2: literal constant has value 2 now

```

Of course it is not possible - because scalar is passed by value, not by reference.

---

