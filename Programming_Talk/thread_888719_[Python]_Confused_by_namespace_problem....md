---
title: "[Python] Confused by namespace problem..."
date: 2008-08-13
forum: Programming Talk
---

### Post by Torajima on 2008-08-13
I'm trying to access class attributes from within a function (without resorting to declaring everything 'global')

Test class:
```
class Animal(): pass
cat = Animal()
cat.name = 'whiskers'
```

Test function:
```
def namespaceTest():
	print cat.name
```

This works fine as long as the function is defined in the Main namespace. But when imported as a module, I get the following error:
```
NameError: global name 'cat' is not defined
```

globals() shows that 'cat' is indeed in the the global namespace, so I'm a little confused...

---

### Post by TreeFinger on 2008-08-13
nevermind

---

### Post by Martin Witte on 2008-08-13
You can create a module cats as:

```
martin@toshibap200:~$ cat cats.py
class Animal(): pass
cat = Animal()
cat.name = 'whiskers'
martin@toshibap200:~$ 
```

And then use this as:
```

martin@toshibap200:~$ cat test.py
#!/usr/bin/env python
import cats
def namespaceTest():
	print cats.cat.name

namespaceTest()
martin@toshibap200:~$ 
```
so you print the member 'name' of object 'cat' created in module 'cats.py', which is imported in 'test.py'

---

### Post by Bachstelze on 2008-08-13
'cat' is in the global namespace but your module cannot access it (if you add a [font="courier New"]print globals()[/font] inside your namespaceTest() function, you'll see that it is not there), so you must pass it as a parameter to the function.

*EDIT: or do it the other way around indeed ;) The key thing is that your module cannot access objects that live outside of it. In the example Martin posted, it does not, it justs defines a new object that your main script will be able to access.*

---

### Post by Torajima on 2008-08-13
> **HymnToLife said:**
> The key thing is that your module cannot access objects that live outside of it.

I don't understand the reasoning behind this.

Why wouldn't a function imported from a module (into the global namespace) behave just like a function defined in that namespace?

---

### Post by days_of_ruin on 2008-08-13
Why in the world would you want to program like that?Its very
confusing.

---

### Post by Martin Witte on 2008-08-13
> **Torajima said:**
> I don't understand the reasoning behind this.

Why wouldn't a function imported from a module (into the global namespace) behave just like a function defined in that namespace?

If you import a module (see the [reference documentation]("http://docs.python.org/ref/import.html")) you can do this in two forms:

This imports a module cats, and then all names in that module
```
import cats
```

This imports the name cat from module cats
```
from cats import cat
```
I'm sensing you expect your python code to behave as the second form. The disadvantage is that if you have more names defined in your module you have to write more import statements. You can write 'from cats import *', it imports all names from module cats, but this is considered as bad practice: your namespace might get polluted - and behave unexpected if you import more modules like this defining the same name.

---

### Post by Bachstelze on 2008-08-13
> **Torajima said:**
> I don't understand the reasoning behind this.

Why wouldn't a function imported from a module (into the global namespace) behave just like a function defined in that namespace?

The functions defined in the module use a different global namespace to avoid clashes with that of the main program. It is very important because the person who wrote the module is not supposed to know how the person who will use it will name his variables, and *vice versa*.

Here, it is not a problem because you wrote both the module and the main program, so you know what the 'cat' variable refers to in both of them. However, in real life, it is not possible, because the person who wrote the module might have used a 'cat' variable for a completely different purpose.

> **Martin Witte said:**
> 

This imports the name cat from module cats
```
from cats import cat
```

Using the originally posted code, this will not work either. The only difference is that the function defined in the module will be called as namespaceTest() instead of myModule.namespaceTest(), but the result would be the same: no 'cat' name in the function's global namespace.

---

### Post by Torajima on 2008-08-13
> **days_of_ruin said:**
> Why in the world would you want to program like that?Its very
confusing.

The above example was just that, an example.

But I do need classes & functions that can communicate with one another, and passing a zillion arguments makes no sense to me.

---

### Post by Torajima on 2008-08-13
> **HymnToLife said:**
> The functions defined in the module use a different global namespace to avoid clashes with that of the main program. It is very important because the person who wrote the module is not supposed to know how the person who will use it will name his variables, and *vice versa*.

I understand what you're saying, but is there a way to override that behavior?

Here is a 'real world' example of the type of thing I'm trying to accomplish:

```
def truthTest(expression, if_true=True, if_false=False):
    """Ternary truth test for Python"""
    import types
    if type(expression) == types.StringType:
        expression = eval(expression)
    if type(expression) != types.BooleanType and False in expression:
        return False
    else:
        return (expression and [if_true] or [if_false])[0]
```

The point of this code is, I want to be able to evaluate both expressions and strings containing expressions.

---

### Post by nvteighen on 2008-08-13
> **Torajima said:**
> The above example was just that, an example.

But I do need classes & functions that can communicate with one another, and passing a zillion arguments makes no sense to me.
There is a reason to pass things through arguments; without globals only arguments and locals will be able to modify the function's behaivor. In other words: it's easier to debug.

If you feel you're passing a zillion of arguments, maybe you need to review your data structures. Or maybe trim your functions... There's definitely something wrong if that occurs.

EDIT: Use return values to communicate between functions!

---

### Post by Torajima on 2008-08-13
> **nvteighen said:**
> There is a reason to pass things through arguments; without globals only arguments and locals will be able to modify the function's behaivor. In other words: it's easier to debug.

Not modify, I only need to read the global variables, not write to them.

I simply want a function imported from a module to behave like a function defined within the main program.... look for a variable in the local scope, and if it's not defined there, look at variables in the main/global namespace.

If it isn't possible, I'll figure something else out, but if there is a way to make this work I'd love to hear it.

---

### Post by nvteighen on 2008-08-13
> **Torajima said:**
> Not modify, I only need to read the global variables, not write to them.

That's what I mean: you read them in a function, say in an if-statement... and you affect the function's behaivor because of the value a variable living outside has.

Of course, this doesn't mean globals are evil. For example, in C we have a nice global variable (errno) you can use to detect which was the last error produced. Probably, experience is the best judge to know when a global is the best to use.

> I simply want a function imported from a module to behave like a function defined within the main program.... look for a variable in the local scope, and if it's not defined there, look at variables in the main/global namespace.

If it isn't possible, I'll figure something else out, but if there is a way to make this work I'd love to hear it.

I hardly doubt you can do that... A local variable is only reachable when the function is loaded in memory and running (in technical terms: loaded in the stack).

Also, why do you need to know something is defined or not? Can't you just define it where you like and check the value from there?

---

