---
title: "Confusion about Python &quot;global&quot; variables"
date: 2007-10-22
forum: Programming Talk
---

### Post by dmsynck on 2007-10-22
Greetings,

I am trying to code a program in Python and am having trouble understanding the use of 'global' variables and how they affect scoping. Here is a snippet of example code, along with the error I am running into. 

```


def function3():

    pass

    return

def function2():

    foo2 - raw_input("Enter another name")

    if foo1 == foo2:
            function3()
    else:
            pass

    return

def function1():

    foo1 = raw_input("Enter a name")
           
    if foo1 == " ":
        foo1 = raw_input("You must enter a name ")
        function2()
    else:
        function2()

    return

def main():
   
    function1()

    return

if __name__ == "__main__":

    # Define all global variables and data structures
    global foo1
    global foo2
 
    main() 


```

The error I am getting occurs when the program hits function2 and tries to compare foo1 to foo2. The error is 'Name error: global name 'foo1' is not defined'

Since I am quite new to Python programming, I guess I don't understand why variables defined as 'global' are not accessible in every function.

Thanks in advance

dmsynck

---

### Post by Acglaphotis on 2007-10-22
Yeah, global statements should only be used inside def blocks, like this:

def x():
    y =  "hi"

y is a local variable because is inside a def block

x = 'hi'

x is a global variable because is outside the def.

def x():
    global x
    x = 'hi'
x is a global variable because you did a global x before using it. Keep in mind that local variables can only be used inside def, otherwise they won't be recognized.

EDIT: for some reason ubuntuforums removed my indentation?

---

### Post by pmasiar on 2007-10-22
You need to define 'global x ' in every function which should change global x. otherwise, Python will declare for you another variable named also x, which will be  'local" in given function.

But if you do not change x, you don't need to declare it as global.

If you don't declare var as global and don't initialize it, accessing value of non-defined variable is error. So it is simple, intuitive, all makes sense

[php]
x = 0

def change():
   """changing x: need global"""
    global x
    print 'adding 1'
    x += 1

def show():
    """not changing x: no global needed, if global x exist in context"""
    print 'show:', x

print x
show()
change()
show()
print x

# when run:
0
show: 0
adding 1
show: 1
1
[/php]

@ Acglaphotis: Use [ code] or [ php] tags around your code to keep indent

---

### Post by xtacocorex on 2007-10-22
```

def function2():

    foo2 - raw_input("Enter another name")

```
Should be
```

def function2():

    foo2 = raw_input("Enter another name")

```

---

### Post by dmsynck on 2007-10-22
Thanks,

I think I understand it now.

---

### Post by alberto ferreira on 2008-10-23
I can't set global variables:

I've made a module called fibo(.py) and it contains function fib2 that works flawlessly except it doensn't set the variable result as global:
[php]
def fib2(n,p): # return Fibonacci series up to n
    if int(p) == 1:
       print 'Result going global'
       global result
    global result
    result = []
    a, b = 0, 1
    for n in xrange(1,int(n)):
        result.append(b)
        a, b = b, a+b
    return result[/php]Then I have the 'program' itself:
[php]import sys
from fibo import *

limit = sys.argv[1]
even_list = []

print fib2(limit,1)
print result

for n in result:
    print n
    if n % 2 == 0:
        even_list.append(n)
        print 'Par:', n[/php]When run my program says that 'result' is going global showing that 'global result' is being executed, however, a few lines later when I need to perform the for loop with the variable 'result' it states that it hasn't been defined!?!?!?

Thanks in advance

---

### Post by snova on 2008-10-23
I'm not certain of the specifics of how "global" operates, but I would guess that it's because it doesn't work over module boundaries.

(And you should probably create your own thread rather than reawaken those over a year old.)

---

### Post by ghostdog74 on 2008-10-23
in your fib2() function, there's no need for 2 global statements.

in your main program, put global
```

global result
def fib2():
   ...
   ...
   global result
   ...

#main program.

```

---

### Post by yalyari on 2008-10-23
In module 'fibo.py', global name 'result' is declared *inside* function 'fib2', so it doesn't exist when the module is imported. It is created when function 'fib2' is *called*, which is after you made local copies of names using 'from fibo import *'. That's why you get NameError.

If you modify your main.py to use 'import fibo' and 'fibo.result', your program will work fine.

---

### Post by alberto ferreira on 2008-10-24
Thanks, and next time I'll do my own thread.

---

