---
title: "[SOLVED] Python fibonacci"
date: 2008-10-22
forum: Programming Talk
---

### Post by alberto ferreira on 2008-10-22
what is 
> a, b = b, a + b
supposed to mean?

Isn't it supposed to do the same that:
[PHP]a=b
b=a+b[/PHP]
??

Because my program isn't yielding the right results:
[PHP]def fibo(limit):
    a=0
    b=1
    list=[]
    for n in xrange(1,limit):
        b = a + b
        list.append(b)
        a = b
    return list

print fibo(10)[/PHP]

I'm starting to learn python, do you have advice on where to start? I've already read [www.python.org's](www.python.org's) tutorial but i'm still lost in the sea...

---

### Post by snova on 2008-10-22
I'm quite sure that it's shorthand for:

[PHP]
a = b
b = a + b
[/PHP]

It could stand being changed. It's needlessly confusing for an introductory tutorial. I think I just glossed over it when I read it the first time without really figuring out how it worked. Better variable names would also be appropriate.

---

### Post by pp. on 2008-10-22
> **alberto ferreira said:**
> 
Isn't it supposed to do the same that:
[PHP]a=b
b=a+b[/PHP]

I suggest to draw up a small table of three rows and two columns.

In the first row, enter the initial values for a and b.
In the second and first row, respectively, put the values for a and b after executing the first and the second line above.

Carefully look at how the values change from line to line.

---

### Post by y-lee on 2008-10-22
> **alberto ferreira said:**
> what is > a, b = b, a + b 

supposed to mean?


a, b = b, a + b means

```
a = b
b = a + b
```

One of the great thing about python is one can test ones code:

```
>>> a = 1
>>> b = 2
>>> a, b = b, a + b
>>> a
2
>>> b
3
>>>

```

---

### Post by pp. on 2008-10-22
> **y-lee said:**
> a, b = b, a + b means

```
a = b
b = a + b
```

One of the great thing about python is one can test ones code:


ahem. Do test 

```
a = b
b = a + b
```

---

### Post by jimi_hendrix on 2008-10-22
i know what the problem is

its your code it should be this i think:

[php]def fibo(limit):
    a=0
    b=1
    list=[1]
    for n in xrange(1,limit):
        b = a + b
        list.append(b)
        a = list[n-1]
    return list

print fibo(10)[/php]

---

### Post by Reiger on 2008-10-22
> **pp. said:**
> ahem. Do test 

```
a = b
b = a + b
```

Why indeed, because this would suggest **b= a+b** may safely be rewritten as **b= 2*b**. **jimi_hendrix** pointed out what --if my read-unfamiliar-language-code skill does not fail me-- should be a working solution.

---

### Post by Erdaron on 2008-10-22
OP: I think your code works. At least when I run it on my computer, the output agrees with the [Fibonacci sequence]("http://en.wikipedia.org/wiki/Fibonacci_number").

Also, just messing around in the python shell, it seems that the two statements are not equivalent.

Example one:
[PHP]>>> a = 2
>>> b = 3
>>> a, b = b, a+b
>>> a
3
>>> b
5[/PHP]

Example two:
[php]>>> a = 2
>>> b = 3
>>> a = b
>>> b = a+b
>>> a
3
>>> b
6
[/php]

It seems that if you are using just one line, the statements are executed "simultaneously." Perhaps someone with a greater knowledge can explain this behavior?

---

### Post by Paul Miller on 2008-10-22
This is called "tuple unpacking."  The line
[php]
a, b = b, a+b
[/php]
is actually equivalent to
[php]
tmp = a
a = b
b = a + tmp
[/php]

What's going on is that on the right hand side of the assignment, Python is creating a tuple containing the current (in this case) integer values of b and a+b.  It then assigns these things componentwise to a and b.  So, essentially, yeah, it's doing them "in parallel."

Another example:

[php]
x, y = y, x
[/php]
is equivalent to
[php]
temp = x
x = y
y = temp
[/php]
which, of course, swaps the values of x and y.

Hope that helps.

---

### Post by Erdaron on 2008-10-22
Paul Miller: thanks for the explanation. However, this seems like a rather complex behavior that's simply implied, but not expressly stated. It seems to me that the simpler interpretation of the statement should have been taken, not the complicated one. Is there a greater design concept here that I'm missing?

I can see this leading to very strange errors. For example, the two variables could be huge, and if Python cloned one of them just to execute this statement, it could crash the system.

---

### Post by y-lee on 2008-10-22
> **pp. said:**
> ahem. Do test 

```
a = b
b = a + b
```

Yeah you are right by saying a, b = b, a + b means

```
a = b
b = a + b
```

I was meaning b = the original value of a plus b as should have been clear by my command sequence:

```
>>> a = 1
>>> b = 2
>>> a, b = b, a + b
>>> a
2
>>> b
3
>>>

```

So i should have said a,b = b,a+b is the same as  
```
t = a
a = b
b = t + b
```

and Paul Miller explains why above :)

---

### Post by Lux Perpetua on 2008-10-22
> **Paul Miller said:**
> ...Exactly. ```
a, b = b, a+b
``` means the same thing as ```
(a, b) = (b, a+b)
``` which means: 

1. Evaluate the right-hand side. Say a = 1 and b = 1; then (b, a+b) evaluates to the tuple (1, 2).
2. Assign the now evaluated right-hand side componentwise to the left hand side. So my example now reduces to (a, b) = (1, 2), which is obvious: assign to a the value 1, and assign to b the value 2. 

This is emphatically *not* the same thing as ```
a = b
b = a + b
```Be aware of this, since misunderstandings like this can be the source of very hard-to-find bugs. 

Erdaron: tuple assignment is useful exactly for situations like this, when you want to update multiple things simultaneously. And the syntax is really perfectly logical, as you'll see if you follow my explanation above. Requiring the statement (a, b) = (b, a+b) to first assign a the value of b, *then* assign b the value of (the new) a+b would require not evaluating the right-hand side of the expression, which would be incredibly counterintuitive. Your point regarding huge temporaries is not germane; there's plenty that python does behind the scenes that you don't see. If you're really skirting the boundaries of your computer's resources, then you have to be aware of all of it (not just this), or better yet just revert to a WYSIWYG language like C.

---

### Post by Can+~ on 2008-10-22
[PHP]import math

def fib(n):
	
	sqrt5 = math.sqrt(5)
	k = 1.0/sqrt5 # numeric constant
	pos_sol = (1.0+sqrt5)/2.0 # positive solution
	neg_sol = (1.0-sqrt5)/2.0 # negative solution
	
	for i in xrange(1, n):
		yield k*(pos_sol**i) - k*(neg_sol**i)

for i in fib(20):
	print i[/PHP]

Made from the solution of a [Recurrence Relation](http://en.wikipedia.org/wiki/Recurrence_relation) go try it.

---

### Post by alberto ferreira on 2008-10-23
Thanks :)

---

