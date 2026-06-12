---
title: "python return statement"
date: 2010-05-22
forum: Programming Talk
---

### Post by scorpious on 2010-05-22
So I'm following a python tutorial and in functions chapter it has a *return* statement. 
Can anyone tell me what this does? 
The tutorial's description is: [The return statement returns a value back to the place where the function was called] which I cant make any sense of.

cheers

---

### Post by lisati on 2010-05-22
I'm not a python programmer, so I'm answering here from what I know from other languages.

A function can be thought of a form of subroutine. In the absence of instructions to the contrary, a program will start with the first instruction, continue with each instruction in turn, and end with the last instruction. When you call a subroutine in your program, this orderly flow from start to end will be paused, the computer will make a note of where it is in your program, and do what the subroutine tells it to do. What the "return" statement does is tell the computer to go back to what it was doing before.

Hope this helps. 

Suggested reading: 
[http://en.wikipedia.org/wiki/Subroutine](http://en.wikipedia.org/wiki/Subroutine)
[http://en.wikipedia.org/wiki/Function_%28computer_science%29](http://en.wikipedia.org/wiki/Function_%28computer_science%29)

---

### Post by oldfred on 2010-05-22
I am self taught, so take it for what it is worth. A return in python also can return one or more values.

```
dgl_response,self.newstock = stockDlg.stock_run(stock_object)

def stock_run(self, newstock):
    code to calculate self.respnse
    code to calculate newstock 
    return self.response, newstock
```I call a def with a value and it returns two values in order in my example above. my naming does not look to good but it shows a call with 2 variables.

---

### Post by schauerlich on 2010-05-22
In python, a function has three things: input, side effects, and output. Input are the arguments give to the function that affect how it behaves or what its output will be. In the following example, "a" and "b" are the input to a function called "foo".

```
foo(a, b)
```

Side effects are everything that a function does that changes data that is used by something other than that function. In this example, changing x is a side effect.

```
x = 4

def foo(a):
    global x
    x = a
```

Output is what a function spits out, or "returns". Remember in algebra, when you had a function like 

```
f(x) = x + 4
```

? You could put something in, like 8, and get something out, in this case 12. You could change the above function to python like this:

```
def f(x):
    return x + 4
```

I can also do something like this:

```
a = 0
a = f(8)
```

Before we called the function, a was 0. When we call the function, it spit out "12", and we then assigned that to a - it now holds 12.

---

### Post by diesch on 2010-05-22
By default every function in Python returns *None* when it reaches the end of the function. Using the *return* statement you can return other values, and you can do it on any other point of the function's code, e.g.:

```

def foo(x):
  if x is None:
     return ""
  try:
     return x**2
  except TypeError:
     return '%s%s'%(x,x)

```

---

### Post by scorpious on 2010-05-22
Yes, I think I understand now. 

thanks guys :)

---

### Post by OgreProgrammer on 2010-05-23
> **scorpious said:**
> Yes, I think I understand now. 

thanks guys :)


Many happy returns.

---

