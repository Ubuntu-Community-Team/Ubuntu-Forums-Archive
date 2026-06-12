---
title: "python method argument number"
date: 2007-04-08
forum: Programming Talk
---

### Post by moshy on 2007-04-08
Hello, trying to run a program (Landell), but connecting to msn it crashes and comes up with an error message. This isn't important because I can fix it by editing some python files it uses according to the stack trace. So basically I change

```

    ...
    
    def get_type(self):
        return self._type

    ...

    def __eq__(self, other):
        return (int(self) == int(other) and self.get_type() == other.get_type())
    
    ...

```

to

```

    ...
    
    def get_type():
        return self._type

    ...

    def __eq__(self, other):
        return (int(self) == int(other) and self.get_type() == other.get_type())
    
    ...

```

so get_type takes no arguments, and the error goes away and it doesn't crash, how clever am I. But I get a new one, when another python file uses get_type

```

File "/usr/lib/python2.5/site-packages/TelepathyButterfly/connection.py", line 391, in _get_handle_for_contact
    self._handles[handle.get_type(), handle.get_id()] = handle
TypeError: get_type() takes no arguments (1 given)

```

Clearly it is in actual fact not giving 1 argument.

And also if I change the first file so get_type actually takes one argument, by going 

```

return (int(self) == int(other) and self.get_type(self) == other.get_type(other))

```

it crashes and goes

```

TypeError: get_type() takes exactly 1 argument (2 given)

```

This all makes no sense to me

---

### Post by pmasiar on 2007-04-08
You need to read up on OOP in Python. In object methods, parameter self is required, you cannot remove it. Self refers to that instance - is explicit.

Obviously "fixing" code without understanding it can get you only that far. For rest, understanding is required. :-)

Error is somewhere else.

---

### Post by dwblas on 2007-04-08
```
def get_type(self):
        return self._type
``` "self" tells the compiler that this function is part of the class.  Without the self it is just another unrelated function, which is not bad except you return self._type which is a variable within the class, and you obviously call self.get_type() because of the error message, so Python is looking for a function within the class.

---

### Post by moshy on 2007-04-09
Right OK, I actually have no experience with python and was merely applying Java knowledge to python.

I take it the parameter 'self' is like making the method an instance method, and doesn't need to be passed as an argument when calling the method, because it is implied. And not having it there is like having 'static' in front of a Java method. Am I right?

If I am, this still doesn't help me, as it means I shouldn't have changed anything, which means that the program will go back to crashing.

Maybe I should just post what comes up in the terminal after it crashes in perhaps another thread.

Also, is there some sort of way to print to the output similar to System.out.println(), 'cause I can see it coming in handy.

---

### Post by ghostdog74 on 2007-04-09
> **moshy said:**
> 
I take it the parameter 'self' is like making the method an instance method, and doesn't need to be passed as an argument when calling the method, because it is implied. And not having it there is like having 'static' in front of a Java method. Am I right?

"self" is the conventional Python name for the instance of the object. It has the same role of "this" object in Java or the "this" pointer in C++.

> 
Also, is there some sort of way to print to the output similar to System.out.println(), 'cause I can see it coming in handy.
You can use the usual print statment , or 
```

import sys
sys.stdout.write("Test")

```

---

### Post by pmasiar on 2007-04-09
> **moshy said:**
> I take it the parameter 'self' is like making the method an instance method, and doesn't need to be passed as an argument when calling the method, because it is implied. And not having it there is like having 'static' in front of a Java method. Am I right?

No and no. Python does not believe in implicit parameters and magic like that. Staic method is inside a package but outside a class.

> Also, is there some sort of way to print to the output similar to System.out.println(), 'cause I can see it coming in handy.

print statement does not satisfy?

---

### Post by dwblas on 2007-04-09
You can wrap a try/except around the calling function or program and display any error messages as in
```
try :
   function/program_name
except :
    import traceback
    et, ev, tb = sys.exc_info()
    while tb :
        co = tb.tb_frame.f_code
        print "Filename = " + str(co.co_filename)
        print  "Error Line # = " + str(traceback.tb_lineno(tb))
        tb = tb.tb_next
    print "error type = ", et
    print "error var name  = ", ev
 
```Then you can perhaps provide a little more information on why it crashes.  As is, there isn't enough to tell why it crashes.

---

### Post by karmakillernz on 2007-04-11
> **moshy said:**
> Right OK, I actually have no experience with python and was merely applying Java knowledge to python.

I take it the parameter 'self' is like making the method an instance method, and doesn't need to be passed as an argument when calling the method, because it is implied. And not having it there is like having 'static' in front of a Java method. Am I right?

```

class MyClass(object):
    def hello(self, name):
        print "Hello", name
    
    @classmethod
    def hello2(cls, name):
        print "Hello from class method", name


# Create a new instance of MyClass.
inst = MyClass()

# The following two lines are exactly the same. 
# The first line is just "syntactic sugar" for the second line.
>>> inst.hello("Bob")
Hello, Bob

>>> MyClass.hello(inst, "Bob")
Hello, Bob

# You can call the class method without requiring an instance.
>>> MyClass.hello2("Bob") # => Hello, Bob
Hello from class method, Bob

# FYI, you can also call class methods on an instance if you wanted.
>>> inst.hello2("Bob")
Hello from class method, Bob

```

With this, hopefully you can see how Python OOP works and how passing self as the first parameter does make sense once you understand what's happening behind the scenes. :)

Just remember:
[LIST]
[*]If calling on an instance, self is passed as the first parameter for you
[*]If calling on a class, you must pass the instance as the first parameter yourself
[*]Unless of course, it is a class method
[/LIST]

---

