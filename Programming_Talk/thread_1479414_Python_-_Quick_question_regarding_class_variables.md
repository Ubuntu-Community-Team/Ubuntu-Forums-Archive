---
title: "Python - Quick question regarding class variables"
date: 2010-05-10
forum: Programming Talk
---

### Post by Bodsda on 2010-05-10
Hi Guys,

I am (once again) attempting to understand GUI programming and classes. I am getting the hang of it now, seems to be making sense, but I just stumbled on something which I need a bit more explanation for. 

1) When defining a function in a class (This is known as a method?) most guides put self as the first parameter. I think this means that the function inherits something (what?) from its parent class, but I am not certain, could someone elaborate?

2) When defining a variable, what is the difference between
```

class Test:
    def __init__(self):
        self.foo = 5

```
and
```

class Test:
    def __init__(self):
        foo = 5

```

3) What would happen if I defined a function in a class without self as the first parameter?

Thanks for your assistance in advance,
Bodsda :)

---

### Post by Tony Flury on 2010-05-10
> **Bodsda said:**
> Hi Guys,

I am (once again) attempting to understand GUI programming and classes. I am getting the hang of it now, seems to be making sense, but I just stumbled on something which I need a bit more explanation for. 

1) When defining a function in a class (This is known as a method?) most guides put self as the first parameter. I think this means that the function inherits something (what?) from its parent class, but I am not certain, could someone elaborate?

It does not inherit anything - what self is is a reference to the instance of the object - so if you have multiple instances of the same class, when you call the method you are given a reference to the instance, and when you set a class variable it is set on that instance - so if you want each instance has a different value of the same variable - that after all is the point 

> 
2) When defining a variable, what is the difference between
```

class Test:
    def __init__(self):
        self.foo = 5

```

This sets a class variable (or attribute) on that instance called foo of the value of 5. That attribute called "foo" is available in every method of that class.

> 
and
```

class Test:
    def __init__(self):
        foo = 5

```

This simply sets a variable called foo which is only accessible (in scope) inside the __init__ function - any other method on that class wont see foo.

> 
3) What would happen if I defined a function in a class without self as the first parameter?

You will get an error that the function has been passed too many parameters - since "self" is always passed.

---

### Post by Bodsda on 2010-05-10
> **Tony Flury said:**
> It does not inherit anything - what self is is a reference to the instance of the object - so if you have multiple instances of the same class, when you call the method you are given a reference to the instance, and when you set a class variable it is set on that instance - so if you want each instance has a different value of the same variable - that after all is the point 


This sets a class variable (or attribute) on that instance called foo of the value of 5. That attribute called "foo" is available in every method of that class.


This simply sets a variable called foo which is only accessible (in scope) inside the __init__ function - any other method on that class wont see foo.


You will get an error that the function has been passed too many parameters - since "self" is always passed.

Cheers for that Tony, that clears things up a bit :)

Thanks,
Bodsda

---

