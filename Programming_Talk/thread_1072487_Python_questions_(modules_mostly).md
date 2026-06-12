---
title: "Python questions (modules mostly)"
date: 2009-02-17
forum: Programming Talk
---

### Post by tom66 on 2009-02-17
If I have two files, app.py, and text.py, can I, from app.py:

```

import text

text.defA()
text.defB(text.varA)

```

assuming text has the function/routine definitions of defA, defB and the variable of varA? And can I do something like this from text.py:

```

def defA():
    main.doSomethingInteresting(main.var1 + main.var2 + varA + 23.5)
    defB()

```

Would that work? 

From the text.py module, is it necessary to *import main* if *main* already imports *text* itself? 

Thanks. Just trying to get my head around Pythons's modules.

---

### Post by Can+~ on 2009-02-17
It could possibly work, but it doesn't make sense. The idea of using modules in python is to create reusable building blocks, if you bind yourself to a function that is on the main file, then the function won't work unless you specifically create that function.

In cases like this, it's smarter to append the function to the text module, or handing the function (you can handle functions through arguments).

[PHP]
#text module
def somefunc(mainfunc):
    mainfunc(...)

#main
text.somefunc(doSomethingInteresting)
[/PHP]

Here's a functional example:

[PHP]def do_operation(mathop):
	return mathop(2, 3)

print(do_operation(lambda x,y: x+y))
print(do_operation(lambda x,y: x*y))[/PHP]

---

### Post by tom66 on 2009-02-17
So what would be an equivalent of *including* a file, like in PHP or in C? Can I even do this? I don't want to put everything in one file as it creates a mess which I'd rather avoid.

---

### Post by Can+~ on 2009-02-17
> **tom66 said:**
> So what would be an equivalent of *including* a file, like in PHP or in C? Can I even do this? I don't want to put everything in one file as it creates a mess which I'd rather avoid.

Make the function return the arguments you need and use them chained:

external_func(main_func())

I mean, if the A function needs B function always, maybe it makes sense to merge them. If not, then it makes sense to make them usable one after another via arguments and return values.

x -> f(x) -> y -> g(y) -> z = g(f(x))

With this approach, both functions are usable on their own.

---

### Post by tom66 on 2009-02-17
Okay, that makes sense. Thanks.

---

