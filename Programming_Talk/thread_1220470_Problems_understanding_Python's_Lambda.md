---
title: "Problems understanding Python's Lambda"
date: 2009-07-22
forum: Programming Talk
---

### Post by SoftwareExplorer on 2009-07-22
I'm reading through the python tutorial because I want to be able to give back to the community and not just be a bystander. 

Anyways, I was getting everthing until I got to the lambda section of the tutorial and now I keep getting confused:
```
4.7.5. Lambda Forms

By popular demand, a few features commonly found in functional programming languages like 
Lisp have been added to Python. With the lambda keyword, small anonymous functions can be 
created. Here&#8217;s a function that returns the sum of its two arguments: lambda a, b: a+b. 
Lambda forms can be used wherever function objects are required. They are syntactically 
restricted to a single expression. Semantically, they are just syntactic sugar for a normal 
function definition. Like nested function definitions, lambda forms can reference variables 
from the containing scope:

>>> def make_incrementor(n):
...     return lambda x: x + n
...
>>> f = make_incrementor(42)
>>> f(0)
42
>>> f(1)
43


```
Where did the variable 'x' come from? Where is it getting it's value?
What is actually happening when it says f = make_incrementor(42)?  I get that the variable 'n' comes from make_incrementor's definition and is whatever gets passed to the make_incrementor function.

---

### Post by CptPicard on 2009-07-22
Welcome to the wonderful world of lambdas and closures... ;) They are actually a rather profound language feature, too bad python's lambdas are just limited to one-liners...

> **SoftwareExplorer said:**
> 
Where did the variable 'x' come from? Where is it getting it's value?

What lambda does is that it defines an anonymous function object on the spot. In this case, 'x' is the single parameter to the lambda.

> 
What is actually happening when it says f = make_incrementor(42)?

We go to make_incrementor and find that what we do there is form one of these lambda-functions (here, one that takes one parameter called 'x' and adds 42 to it) and then return it. This function that we just created and returned is then bound to f. Then, we can call f like any other function with a parameter, which ends up as the 'x' of the lambda definition, therefore, we get f(0) = 0 + 42 and so on.


> I get that the variable 'n' comes from make_incrementor's definition and is whatever gets passed to the make_incrementor function.

And in this case, "n" is said to be in the lambda's closure, that is, it's one of the variable bindings that is visible from the definition of the lambda. This is a powerful feature -- it lets you "grab context" for later access when you actually invoke the lambda function (like we do for the particular value "42" here).

---

### Post by SoftwareExplorer on 2009-07-23
Thanks! It makes so much more sense now.

> **CptPicard said:**
> 
And in this case, "n" is said to be in the lambda's closure, that is, it's one of the variable bindings that is visible from the definition of the lambda. This is a powerful feature -- it lets you "grab context" for later access when you actually invoke the lambda function (like we do for the particular value "42" here).

Not sure I understand this yet, but I'll try to go over it again in the morning. Care to explain it further?

---

### Post by soltanis on 2009-07-23
Basically, when you do a lambda like CptPicard said, it'll "capture" n the way it is when the call was invoked. So say you do this:

```

def make_incrementor(n):
     return lambda x: x + n

```

When you call make_incrementor with an argument n, that variable falls into the "closure" of the lambda function that was returned. In other words, say you do this:

```

# I'm going to make a particular incrementor for n = 2
inc2 = make_incrementor(2)

# Now here's another one, but n = 28
inc28 = make_incrementor(28)

print(inc28(10)) # = 38
print(inc2(10)) # = 12

```

You might've noticed two things. First, I made more than one instance of the function, but they don't increment by the same amount (the n of one function isn't the same as the n of the other function). Second, no matter what else I do (except delete the functions or set them equal to something else) the n I originally passed to make_incrementor remains the same. In other words, it didn't go away, and here's the kicker, *even when the function make_incrementor returned*. That's not normal behavior for variables, since according to normal scope rules they disappear when the function they're in returns.

Basically, a closure is a little private namespace of variables that persist (and can actually be modified), even after the function which created it has returned. You might think this is a pretty useless feature; in Common Lisp, it's basically how object orientation is implemented. It's quite an amazing feature.

---

### Post by nvteighen on 2009-07-23
> **CptPicard said:**
> Welcome to the wonderful world of lambdas and closures... ;) They are actually a rather profound language feature, too bad python's lambdas are just limited to one-liners...

Good news: I discovered that you can do multiline closures in Python :) They aren't anonymous lambdas, but they do enclose the values.

```

def abc(n):
    def nnn(z):
        result = 0
        if n > z:
            result = n - z
        else:
            result = n + z

        return result

    return nnn

myfunc = abc(4)
print myfunc(5)
print myfunc(1)

```

---

### Post by CptPicard on 2009-07-23
> **nvteighen said:**
> Good news: I discovered that you can do multiline closures in Python :) They aren't anonymous lambdas, but they do enclose the values.

Uhm... good idea just returning the inner function. I have been stupid enough to "return lambda x: nnn(x)"... :)

This is actually another good example of what I mean by python's consistency and orthogonality -- because things are consistently "designed right", stuff "just works" as you would expect...

---

### Post by SoftwareExplorer on 2009-07-23
So this closure thing means that each time you run the make_incrementer() function it gives that specific lambda its very own 'n' that is still there after the make_incrementor is finished running. And each time make_incrementor is run it makes another separate 'n'. Did I get it all right?

---

### Post by CptPicard on 2009-07-23
Yes, as a matter of fact the lambda is able to access anything that is "lexically visible" (that is, in accessible scopes) at its definition point, even after it's been returned.

It's a handy mechanism for creating parametrized functions at runtime or delaying execution of something in some context... and from the closures, object-oriented programming falls out as a kind of consequence.

Theoretically speaking, lambdas are, at a minimum, all you need... lambda calculus is based on function definition and application.

---

### Post by dandaman0061 on 2009-07-23
This is expanding on nvteighen's post and may be beating a dead horse, but I'm of the opinion that the more angles of explanation the better ;)

Just know that in python, functions are objects too.  They can be assigned to/referenced by variables the same way that you assign integers to variables.
```

def func1():
    print 'within func1'


x = func1   # functions can be assigned to variables
            # NOTICE i didn't 'call' func1

print 'calling x:',
x()         # now 'calling' variable x actually calls 'func1'

# 'x' and 'func1' point to the same function object
#   notice their addresses are the same
print 'func1: ', func1
print 'x:     ', x
```

Now applying this to the lambda function, here is an equivalent:
```

def make_incrementor(n):
    def new_func(x):
        return x + n
    return new_func

x = make_incrementor(42)  # creates a new_func w/ n == 42
y = make_incrementor(56)  # creates a different new_func w/ n == 56

print 'x:', x
print 'y:', y
print 'x(1):', x(1)
print 'y(5):', y(5)
print 'x(0):', x(0)
```

Here is the output:
```

x: <function new_func at 0xb7f1e294>
y: <function new_func at 0xb7f1e2cc>
x(1): 43
y(5): 61
x(0): 42
```

Notice that both the 'x' and 'y' variables are 'new_func' functions but they are actually different objects (shown by them existing at different addresses).
FYI: The address of the function is the hex number in <function new_func at 0xb7f1e294>
Hope that helps.

---

### Post by Can+~ on 2009-07-23
> **dandaman0061 said:**
> This is expanding on nvteighen's post and may be beating a dead horse, but I'm of the opinion that the more angles of explanation the better ;)

And still beating the same horse, many things can be done with functions (Besides calling them and returning)

Passing them as arguments:
[PHP]def dosomething(task, a, b):
	return task(a, b)

print dosomething(lambda a,b: a**b, 5, 2)[/PHP]
(note: Alternative way could be to create a function (with [FONT="Courier New"]def[/FONT]) and passing it as argument)

Returning

[PHP]def dosomething():
	return lambda x, y: x+y

print dosomething()(2, 3)[/PHP]
(note: Again, can be used with alternative way (read previous note))

Storing

[PHP]tasks = { \
	"sum"  : lambda x,y: x+y,
	"sub"  : lambda x,y: x-y,
	"mult" : lambda x,y: x*y,
	"div"  : lambda x,y: x/y,
	"pow"  : lambda x,y: x**y
}

print tasks["sub"](6, 8)[/PHP]
(note: pair them with any Data Structure, in this example, a dictionary)

Function are not entirely "First-class citizens" but it's pretty close.

---

### Post by nvteighen on 2009-07-24
> **Can+~ said:**
> 
Function are not entirely "First-class citizens" but it's pretty close.

There comes a question... I always hear Python functions are not First-class Objects, but I haven't yet seen where the difference lies for example with Lisp.

In other words, can someone explain me which feature Python functions lack in order to not be First-class objects?

---

### Post by matthew.ball on 2009-07-24
What I get from it, is that basically functions are our "objects" - it is valid to use functions just like a variable there is no distinction.

A function [FONT="Courier New"]map[/FONT] takes as an argument a function f, and a list l, and the output of [FONT="Courier New"]map[/FONT] is the function f applied to each element of the list l - This is a first-order function (because it is able to accept another function as it's argument (or rather, substitute a function where ever a variable is valid - my own terms :p)).

I believe the behaviour is similar to a function pointer in C, though I don't believe C is considered first-class...

---

### Post by CptPicard on 2009-07-24
> **nvteighen said:**
> 
In other words, can someone explain me which feature Python functions lack in order to not be First-class objects?

Interesting question. It seems like functions even have the object-like namespace hash associated with them that objects have:

```

>>> def foo(x):
...     return x + 1
...
>>> foo
<function foo at 0xb7df46bc>
>>> foo.a = 5
>>> foo.a
5
>>> dir(foo)
['__call__', '__class__', '__closure__', '__code__', '__defaults__', '__delattr__', '__dict__', '__doc__', '__format__', '__get__', '__getattribute__', '__globals__', '__hash__', '__init__', '__module__', '__name__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', 'a', 'func_closure', 'func_code', 'func_defaults', 'func_dict', 'func_doc', 'func_globals','func_name']

```

They don't have the "self", but it's not needed, as the name of the function suffices and is unique... so I see no reason why not consider functions "first-class objects" as they apparently very much seem to be to the python runtime. Btw, I wonder if one can alter whatever is in the "func_closure".. :)


> **matthew.ball said:**
> This is a first-order function (because it is able to accept another function as it's argument (or rather, substitute a function where ever a variable is valid - my own terms :p)).

It's a "higher-order function" actually. :)

> 
I believe the behaviour is similar to a function pointer in C, 

In terms of passing a variable for "which function to call", yes. C of course lacks the closures... there is a gcc extension that at least allows nested functions to access enclosing scope as it is guaranteed to exist lower on the stack. Helps writing callbacks a lot.

---

### Post by SoftwareExplorer on 2009-07-26
Thanks for the help everyone. I get it alot better by now :)

---

