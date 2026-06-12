---
title: "Python: get parameter list"
date: 2009-08-21
forum: Programming Talk
---

### Post by kumoshk on 2009-08-21
In Python, is it possible to get the parameter list of a function object? I mean, so I can store it in a variable, compare it to another function's, or some such.

---

### Post by smartbei on 2009-08-21
You can use func.func_code.co_varnames. Here is an example:
```

def f(a,b,c):
    d = 7
    print a,b,c,d
print f.func_code.co_argcount
print f.func_code.co_varnames

```
As you can see co_varnames holdes the names of all of the variables used in the function, and co_argcount holds the number of arguments the function receives. The first co_argcount names from co_varnames are the arguments.

Hope that helps!

---

### Post by delfick on 2009-08-21
you can also get it within a function using the inspect module

for example, something that I've used in a project recently

[php]
import inspect
def aFunction(self, param1, param2, param3, param4, etc):
        
    #set everything passed in to a self.xxx attribute
    import inspect
    args, _, _, _ = inspect.getargvalues(inspect.currentframe())
    for arg in args:
        setattr(self, arg, locals()[arg])
[/php]

---

### Post by kumoshk on 2009-08-21
Awesome!

someFunction.func_code.co_argcount

was essentially what I was looking for.

Thanks for the help, and the extra information, too.

---

### Post by kumoshk on 2009-08-21
Hmm, what about default values? I think there's a way to get just those (actually, I saw it earlier, but I don't know where the page is that I saw it on).

That page also listed some of the stuff you said, but I didn't know you had to reference func_code before co_varnames and such.

---

### Post by kumoshk on 2009-08-21
Ah, looks like I recorded the information after all.

Here's how to do it:
someFunction.func_defaults (however, this doesn't tell which argument it's for or that it starts on; there might be another way to do that).

---

### Post by kumoshk on 2009-08-21
> **delfick said:**
> args, _, _, _ = inspect.getargvalues(inspect.currentframe())
What are the underscores followed by commas for? (i.e. _, _, _)?

---

### Post by delfick on 2009-08-21
> **kumoshk said:**
> What are the underscores followed by commas for? (i.e. _, _, _)?

that function gives back (args, varargs, keywords, locals)

but because I only use args, I only give a meaningful name to that and _ to the rest.

---

### Post by kumoshk on 2009-08-21
Ah, thanks. I was worried that might be some funky syntax that might be useful to know in future (I've come across a lot of that, lately: there's more to Python than meets the eye, at first).

---

