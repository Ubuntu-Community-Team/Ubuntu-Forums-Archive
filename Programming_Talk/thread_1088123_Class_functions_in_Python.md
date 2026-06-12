---
title: "Class functions in Python"
date: 2009-03-05
forum: Programming Talk
---

### Post by ranthal on 2009-03-05
So I just started learning Python and in my __init__ for a class I want to check if a certain name is valid so I created a function:

def valid(name):
    if name in nameAddrs:
        return True
    else:
        return False

where nameAddrs is a dictionary.  It works fine when I leave it outside of the class, but when it is inside it and I call it during init I receive:

Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "reg.py", line 62, in md
    reg = Class(name)
  File "reg.py", line 32, in __init__
    if valid(name):
NameError: global name 'valid' is not defined

Why is this?  Is there a better way to do this since a lot of the ideas behind Python are still new to me?

---

### Post by cabalas on 2009-03-05
with python the first argument of any method belonging to a class is the self keyword so for your code it would be: 

[PHP]
def valid(self, name):
	if name in nameAddrs:
		return True
	else:
		return False
[/PHP]

though you don't pass the self parameter when you call the function all that is taken care of automagically.

---

### Post by ranthal on 2009-03-05
> **cabalas said:**
> with python the first argument of any method belonging to a class is the self keyword

ok makes sense. just to clarify-even though the method doesn't utilize self anywhere it should still be included as the first argument so that Python knows it is a method of the class?

---

### Post by Can+~ on 2009-03-05
> **ranthal said:**
> ok makes sense. just to clarify-even though the method doesn't utilize self anywhere it should still be included as the first argument so that Python knows it is a method of the class?

Yes, but that's not the purpose of "self".

[FONT="Courier New"]self[/FONT] represents the class itself, and whenever you call a function inside a class (either from outside or inside), the class itself sends the "self" into said function. So whenever your function is called it's handled:

(self, the rest of the arguments....)

A function that only accepts one, will end up receiving 2 arguments (self and the other one), that raises an error.

[PHP]

class MyClass:
	a = 2

	def somefunc(self):
		a = 3
		print a # It will return 3
		print self.a # It will print 2
[/PHP]

Every variable defined inside somefunc is local to that scope, but variables declared in the class are accessible via "self". Also, to make sure you're clear, self does represent the current instance of said class. So if you do:

[PHP]class MyClass:
	a = 2

	def showa(self):
		print self.a # It will print 2

instance1 = MyClass()
instance2 = MyClass()

instance1.a = 5
instance2.a = 3

instance1.showa() # will print 5
instance2.showa() # will print 3
[/PHP]

---

### Post by ranthal on 2009-03-05
awesome, thanks guys. a lot of what i program in is C so Python looks a little foreign still.

---

### Post by wmcbrine on 2009-03-05
BTW, use [ code ] tags (without spaces) to preserve formatting.

Instead of this:

```
def valid(name):
    if name in nameAddrs:
        return True
    else:
        return False

```

just do this:

```
def valid(name):
    return name in nameAddrs

```

"name in nameAddrs" is already a boolean expression.

---

