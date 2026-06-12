---
title: "[Python] Passing an Integer/boolean by reference"
date: 2008-04-12
forum: Programming Talk
---

### Post by aashay on 2008-04-12
I have been reading around about how integers are immutable and all... But none of the articles mentioned how to make them otherwise.
Basically what I want to emulate is passing by reference like in C++
```

a=0
def inc(a):
     a+=1
inc(a)

```

After this, a is still 0 as expected. I need it to be 1
The variable, boolean in my case, ends up traveling through various functions in a new thread. I just need to be able to tell when its value is changing from a different thread.
The solution I am using now is appending the integer to a list and using that instead. But I really want a better, more correct way to do this.
**In short: How do I pass an integer by reference in Python**

---

### Post by alexforcefive on 2008-04-12
I think you would need to do:

```
a=0
def inc(a):
    a+=1
    return a

a = inc(a)
```

---

### Post by aashay on 2008-04-12
I cant return the integer/boolean. As I mentioned, it is in another thread altogether.

---

### Post by ghostdog74 on 2008-04-12
you can use[ global]("http://www.wellho.net/resources/ex.php4?item=y105/locvar.py"). but use it carefully.

---

### Post by aashay on 2008-04-12
Actually I cant do that either as the variable to be passed is not predetermined. It's kind of tough to explain but I just tried the global way and it didn't work.
Say you were to swap two variables(the classic pass by reference example). Using no return statements (returning tuple etc), how would I make the function work for any two variables that I pass to it?

---

### Post by LaRoza on 2008-04-12
> **aashay said:**
> Actually I cant do that either as the variable to be passed is not predetermined. It's kind of tough to explain but I just tried the global way and it didn't work.
Say you were to swap two variables(the classic pass by reference example). Using no return statements (returning tuple etc), how would I make the function work for any two variables that I pass to it?

Try using a singleton.

---

### Post by Can+~ on 2008-04-12
Dictionaries are passed by reference:

[PHP]def myFunc(refdict, key):
	refdict[key] = not refdict[key]

a = {"val":False}

print "before:",a #prints before:{"val":False}

myFunc(a, "val")

print "after:",a #prints after:{"val":True}[/PHP]

Kinda overkill, but way better than using Globals.

---

### Post by smartbei on 2008-04-12
Fact is, in python, everything is passed by reference. The problem is that when you change (add, subtract, multiply, etc.) an int, string, or tuple what actually happens is that a totally new object is created. That is the definition of an immutable type. You can't change that.

the easiest way to do what you are trying is to pass a list or a dictionary, as Can+~ said.

I guess the question remains - what do you need to do? Perhaps we could provide ideas for a minor restructuring so that this is not necessary.

---

### Post by pmasiar on 2008-04-12
You can pass list with single element:

[php]
def swap(x,y):
    x[0], y[0] = y[0], x[0]

>>> a = [1]
>>> b = [22]
>>> swap(a,b)
>>> a
[22]
[/php]

---

### Post by Wybiral on 2008-04-12
As others have said, integers are immutable. If "a == 5" you can't actually change the value of "5", can you :) No, but you can make "a" equal something else. As others have mentioned, you basically have to wrap it in some mutable type like a List, Dict, or even a class where it's a member (this is especially favorable if there are other values you need to communicate between threads).

---

### Post by nanotube on 2008-04-12
my first thought is to just wrap it in a list (as others have also suggested). 
your code would simply become the following:
```

a=[0]
def inc(a):
     a[0]+=1
inc(a)
print a #this will produce output "[1]"
print a[0] #this will produce output "1"

```

---

### Post by aashay on 2008-04-13
> **aashay said:**
> 
The solution I am using now is appending the integer to a list and using that instead. But I really want a better, more correct way to do this.
This is what I'm doing:
I have created a server app with corresponding client side libraries. One of the function in the client side starts a thread which has a socket connection with the server. This thread is kept alive as long as the socket is. The programmer using the client library can pass a variable to the function creating the thread. The value of this variable will be modified from this thread according to what is happening over the socket. The point is since the programmer chooses the variable, he can then monitor it in some other thread if he wishes. So basically, I need to write the value in one thread and read it in another. I just need a simple boolean variable for the time being

---

### Post by nanotube on 2008-04-13
> **aashay said:**
> This is what I'm doing:
I have created a server app with corresponding client side libraries. One of the function in the client side starts a thread which has a socket connection with the server. This thread is kept alive as long as the socket is. The programmer using the client library can pass a variable to the function creating the thread. The value of this variable will be modified from this thread according to what is happening over the socket. The point is since the programmer chooses the variable, he can then monitor it in some other thread if he wishes. So basically, I need to write the value in one thread and read it in another. I just need a simple boolean variable for the time being

you can wrap booleans with a list just as well as an integer...

---

### Post by pmasiar on 2008-04-13
Seems like that variable is part of some object - it is one of the bunch of properties. Object is passed by reference, you may either change property directly (in simple case) or create mutator for that property, to be nice OO.

---

### Post by aashay on 2008-04-14
I kind of gave up on the whole thing and settled on using the lists method. Thanks for all the help anyway

---

### Post by LukeTeyssier on 2010-01-29
If you really need to use the language in a way that it doesn't want to let you, try abusing ctypes:

>>> from ctypes import *
>>> def inc(x):
...     x.value += 1
...
>>> y = c_int(0)
>>> y
c_long(0)
>>> inc(y)
>>> y
c_long(1)
>>> print y.value
1
>>> type (y.value)
<type 'int'>
>>>

---

