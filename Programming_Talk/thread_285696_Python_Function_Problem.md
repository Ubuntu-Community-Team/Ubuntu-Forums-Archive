---
title: "Python: Function Problem"
date: 2006-10-27
forum: Programming Talk
---

### Post by JRaz on 2006-10-27
I'm new to python so go easy :P

Anyway I have the following code

```
from Tkinter import *

root=Tk()

def function1(name):
	print 'function1'

def function2(name):
	print 'function2'

lbl1=Label(root,text='Function1')
lbl1.bind('<1>',function1)
lbl1.pack()

lbl2=Label(root,text='Function2')
lbl2.bind('<1>',function2(0))
lbl2.pack()

root.mainloop()
```

Basically the problem is this the second function gets run on program execution and then cant be run on mouse click whereas the first function is only run on mouse click (the way i want it ).

The only difference is that function2 gets a variable passed to it.

---

### Post by duff on 2006-10-27
"function1" is a function object.
"function2(0)" is a function call which returns None.

---

### Post by JRaz on 2006-10-27
> **duff said:**
> "function1" is a function object.
"function2(0)" is a function call which returns None.
which means?

---

### Post by skymt on 2006-10-27
> **JRaz said:**
> which means?

It means you have to replace "function2(0)" with just "function2":```
lbl2.bind('<1>',function2(0))
```

---

### Post by JRaz on 2006-10-27
But the point is i WANT to pass a value (in this case 0) to the function, I just don't want it to run on program execution.

---

### Post by skymt on 2006-10-27
> **JRaz said:**
> But the point is i WANT to pass a value (in this case 0) to the function, I just don't want it to run on program execution.

1. "function()" means "run this function". When used as a function argument, it passes the result, as you would expect. You wouldn't want "newSquare(20, sqrt(36))" to pass a number and a function object called "sqrt", you would want it to do what it does: pass two numbers.

2. "function" means "this is a function". "doSomething(function, function()" passes two values to doSomething. One is the function, the other is the result of the function.

bind expects a function object, so you would use the second form.

That's just basic Python syntax. If always want function2 to act like it was passed "0", code it to do so.

---

### Post by JRaz on 2006-10-27
so how would I achieve the following without using multiple functions and preventing them running on startup.

```
def function(name):
	print name

lbl1=Label(root,text='Function1')
lbl1.bind('<1>',function('bob')
lbl1.pack()

lbl2=Label(root,text='Function2')
lbl2.bind('<1>',function('ben'))
lbl2.pack()
```

---

### Post by skymt on 2006-10-27
When Tkinter runs a callback function, it passes an event object:

```
from Tkinter import *

root=Tk()

def function(event):
	print event.widget.cget("text")

lbl1=Label(root,text='bob')
lbl1.bind('<1>',function)
lbl1.pack()

lbl2=Label(root,text='ben')
lbl2.bind('<1>',function)
lbl2.pack()
```

[This guide](http://www.pythonware.com/library/tkinter/introduction/events-and-bindings.htm) explains the Tkinter event system in detail.

---

### Post by duff on 2006-10-27
> **JRaz said:**
> But the point is i WANT to pass a value (in this case 0) to the function, I just don't want it to run on program execution.

You want a [lambda function](http://en.wikipedia.org/wiki/Lambda_calculus)...replace "function2(0)" with "lambda: function2(0)".

---

### Post by skymt on 2006-10-27
> **duff said:**
> You want a [lambda function](http://en.wikipedia.org/wiki/Lambda_calculus)...replace "function2(0)" with "lambda: function2(0)".

That will also work, but catching the event is cleaner.

---

### Post by duff on 2006-10-27
That wiki page probably has too much theory if you haven't seen it before.  Here's a quick example (basically **lambda** returns a function object allowing you delay a function call and bind parameters)

```

def func(a,b):
   print a,b


f = lambda: func(2,3)
g = lambda x: func(x,6)
h = lambda x: func(3,x)

func(1,2)
f()
g(1)
h(1)
```

When ran, will print out:

```
1 2
2 3
1 6
3 1
```

---

