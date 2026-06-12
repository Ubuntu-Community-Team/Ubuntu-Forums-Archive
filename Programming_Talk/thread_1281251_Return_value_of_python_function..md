---
title: "Return value of python function."
date: 2009-10-03
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-10-03
I have lately been trying to write the code for a sudoku solver. My problem has something to do, with the return value of one of the functions.

If someone has the patience, can they please tell me why the return value of the main function to the sukusolver function is None??

This is my code, which i am referring to here.
```

def main(idata,status):	#Recursive
	
	//code
	
	if count>0:
		main(idata,status)
	else:
		return idata

def sukusolver():	#This is the start of the program

	//code

	rmain=main(idata,status)	
	#I don't know how idata has become a global variable. Something fishy out here. But it is still working. :). You can check rmain, doesn't have the value of idata even after returning idata from main. It has the value None. I don't know why??

```

---

### Post by 7raTEYdCql on 2009-10-03
Main is calling itself recursively over and over again till count==0, that means main is returning correct value over and over again. Well i guess i am confused. Can someone explain to me the concept of return etc.. again.

I seem to have got things all boggled up.

---

### Post by matja on 2009-10-03
Hi i.mehrzad,

The return statement is fairly straight-forward. If there is an explicit return with an explicit value, that value is returned, i.e. this function returns 1:
```

def foo():
    return 1

```
If no explicit value is given, the default value is None, so this function returns None:
```

def bar():
    return

```
The same goes for functions without a return statement, so bar could be defined as
```

def bar():
    pass # means do nothing

```
and still return None.

I think it's this implicit return of None that you're seeing. If the first call to main results in count > 0, then main will be called again. However, when that call eventually returns the execution will continue after that statement and reach the end of the function without encountering a return statement. The function will then return the default value of None. I think this is what you want:
```

def main(idata, status):
    # code
    if count > 0:
        return main(idata, status)
    else:
        return idata

def sukusolver():
    # code
    rmain = main(idata, status)

```

Hope this helps and good luck!

/Mattias

---

### Post by nvteighen on 2009-10-03
Hm... Apart from the implicit return, there's a slightly important issue when building recursive procedures you are overlooking a bit.

The best way to recurse is using tail-recursion. This means to handle all limit cases first and only recurse once at the last return statement of your code. That recursive call will be "prepared" by setting variables conditionally before calling the recursion.

Example:
```

def collector(n):

    def loop(n, col):
        if n == 0:
            return col
        else:
            return loop(n - 1, [n, col])

    return loop(n, [])

print collector(78)

```

Ok, that's an awkward translation of some Lisp code, but the idea is there... The loop "local function" is where the recursion is performed to simulate an iteration.

This code also shows the advantages of lists constructed from cons pairs... and also how unsuitable Python is for writing pure-functional code...

---

### Post by Bachstelze on 2009-10-03
> **nvteighen said:**
> 
This code also shows the advantages of lists constructed from cons pairs... and also how unsuitable Python is for writing pure-functional code...

Given that Python is not a pure-functional language, it kind of makes sense...

---

### Post by jjalocha on 2009-10-03
If I remember well, the Scheme (a Lisp dialect) specification explicitly requires the interpreter to optimize tail recursive calls. Does Python do such a thing? What benefits do I get in Python by using tail recursion?

---

### Post by nvteighen on 2009-10-03
> **jjalocha said:**
> If I remember well, the Scheme (a Lisp dialect) specification explicitly requires the interpreter to optimize tail recursive calls. Does Python do such a thing? What benefits do I get in Python by using tail recursion?

The benefit that tail-recursive style is the clearest way to learn how to use recursion. I know it doesn't cover anything, but it's quite good to have it in mind.

---

### Post by 7raTEYdCql on 2009-10-03
OK, i get it, but i still didn't understand how idata became a global value function. Or was it that a copy of idata wasn't made in the main namespace. They were dealing with the original 2-d matrix?

---

### Post by unutbu on 2009-10-03
Python will assign a meaning to idata based on the [LEGB (Local,Enclosed,Global,Builtin) variable scoping rule]("http://stackoverflow.com/questions/291978/short-description-of-python-scoping-rules"). 

You may also enjoy looking at Peter Norvig's solution:
[http://norvig.com/sudoku.html](http://norvig.com/sudoku.html)

---

### Post by Can+~ on 2009-10-03
Also, global declarations can't be altered, unless you use the global statement

[PHP]#!/usr/bin/env python

cant_touch_this = 10

# First test
def touch_this():
	cant_touch_this = 5
	
	print "inner:", cant_touch_this

touch_this()

print "outer:", cant_touch_this

# Second global
def touch_this():
	global cant_touch_this
	cant_touch_this = 5
	
	print "inner:", cant_touch_this

touch_this()

print "outer:", cant_touch_this
[/PHP]

Without global, you can only see global variables, but in the moment you do "global_name = 2", you get a local variable.

---

### Post by unutbu on 2009-10-03
Ah yes! The MC Hammer rule ;)

---

### Post by matburton on 2009-10-04
> **i.mehrzad said:**
> I have lately been trying to write the code for a sudoku solver

Snap! I did exactly the same recently as a method of learning Python

(Well technically I ported a sudoku solver I wrote when I was learning Lua)

Anyway in case it's of interest it's [[COLOR="Blue"]_here_[/COLOR]]("http://matburton.svn.beanstalkapp.com/sudoku/trunk")

You can try it out by running puzzles/sudoku17/solve.py

Any review comments from anyone much appreciated :)

---

