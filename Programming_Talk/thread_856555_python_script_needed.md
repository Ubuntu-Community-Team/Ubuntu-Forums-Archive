---
title: "python script needed"
date: 2008-07-11
forum: Programming Talk
---

### Post by MDSmith2 on 2008-07-11
I need (preferable all in one function)

[LIST=1]
[*]Asks the user to enter a int+int, int-int, etc problem
[*]checks the entry for +, -, etc then adds it up and
[*]prints the result.
[/LIST]
thanks

---

### Post by -grubby on 2008-07-11
Do you mean like a calculator? I tried to make one once, but I kept getting alot of type-errors

---

### Post by TreeFinger on 2008-07-11
Why do you need this? Why don't you program it yourself?

---

### Post by nvteighen on 2008-07-11
In Python, it can be deadly easy. If you have done some programming with any decent scripting language, you'll know that they usually include some way to evaluate maths.

In C, it may be an interesting exercise on string parsing, but it would be reduced just to that and a proper way to call the operation (pointer-to-function?).

(And in theory, I don't know Python... but started to play around with the console).

---

### Post by LaRoza on 2008-07-11
> **MDSmith2 said:**
> I need (preferable all in one function)

[LIST=1]
[*]Asks the user to enter a int+int, int-int, etc problem
[*]checks the entry for +, -, etc then adds it up and
[*]prints the result.
[/LIST]
thanks
[php]
#!/usr/bin/python
eval(raw_input("Enter: "))
[/php]

For writing something that parses a string, postfix notation is a lot easier to use. See [http://laroza.freehostia.com/home/apps/rpn/default.html](http://laroza.freehostia.com/home/apps/rpn/default.html)

---

### Post by LaRoza on 2008-07-11
> **nathangrubb said:**
> Do you mean like a calculator? I tried to make one once, but I kept getting alot of type-errors

raw_input() will return a string, so you have to convert to numbers.

---

### Post by -grubby on 2008-07-11
> **LaRoza said:**
> raw_input() will return a string, so you have to convert to numbers.

yes, but I did int(raw_input()). Shouldn't that return an integar? Also, plus signs, etc don't count as integars do they?

EDIT: Holy crap! Eval is awesome. Making a calculator with this should be dead easy. Also, does eval stand for evaluate?

---

### Post by LaRoza on 2008-07-11
> **nathangrubb said:**
> yes, but I did int(raw_input()). Shouldn't that return an integar? Also, plus signs, etc don't count as integars do they?
You should split it, then parse it.

```

>>> for sym in raw_input("Enter: ").split():
...     print sym
... 
Enter: 2 + 2 - 1 * 4
2
+
2
-
1
*
4
>>> 

```


> 
EDIT: Holy crap! Eval is awesome. Making a calculator with this should be dead easy. Also, does eval stand for evaluate?

Yes, it evaluates a string as a Python command. I don't recommend you use it.

---

### Post by -grubby on 2008-07-11
> **LaRoza said:**
> You should split it, then parse it.

```

>>> for sym in raw_input("Enter: ").split():
...     print sym
... 
Enter: 2 + 2 - 1 * 4
2
+
2
-
1
*
4
>>> 

```




Yes, it evaluates a string as a Python command. I don't recommend you use it.

Oh, I was thinking it just did math. Yeah, that sounds kind of dangerous

---

### Post by MDSmith2 on 2008-07-11
> **nathangrubb said:**
> Do you mean like a calculator? I tried to make one once, but I kept getting alot of type-errors
Yes, but i don't want you to give away the whole thing
> **TreeFinger said:**
> Why do you need this? Why don't you program it yourself?
I can make a calculator that takes input like so:
1
+
2
3
but Like that i can't get it to make q mean quit with the int(raw_input
> **LaRoza said:**
> [php]
#!/usr/bin/python
eval(raw_input("Enter: "))
[/php]For writing something that parses a string, postfix notation is a lot easier to use. See [http://laroza.freehostia.com/home/apps/rpn/default.html](http://laroza.freehostia.com/home/apps/rpn/default.html)
Not heard of eval, must investigate.
thanks

---

### Post by MDSmith2 on 2008-07-11
Thanks guys.
That was alot easier then I thought it would be.
if anyone cares, here it is

---

### Post by -grubby on 2008-07-11
> **MDSmith2 said:**
> Thanks guys.
That was alot easier then I thought it would be.
if anyone cares, here it is

Ooh.. I'll look at it. Thanks for giving the source :)

---

### Post by unutbu on 2008-07-11
How would I have to modify

```
while True:
     x = eval(raw_input(">>> "))
     if x == 'q':
          break
     print x
```

so that I could type

```
>>> print "hello"
```

and get it to evaluate? Currently I get
```

% test.py
>>> print "hello"
Traceback (most recent call last):
  File "/tmp/pybin/test.py", line 9, in <module>
    x = eval(raw_input(">>> "))
  File "<string>", line 1
    print "hello"
        ^
SyntaxError: invalid syntax
```

---

### Post by MDSmith2 on 2008-07-11
> **nathangrubb said:**
> Ooh.. I'll look at it. Thanks for giving the source :)
really not much to see.
I looked at another arithmetic calculator (in c++) and it had like 250 lines but this looks as big as a "Hello, World!" program with comments.

---

### Post by -grubby on 2008-07-11
> **MDSmith2 said:**
> really not much to see.
I looked at another arithmetic calculator (in c++) and it had like 250 lines but this looks as big as a "Hello, World!" program with comments.

But as LaRoza mentions, using eval() as a shortcut is bad. And if you don't enter a number or "q", it crashes..

---

### Post by MDSmith2 on 2008-07-11
> **nathangrubb said:**
> But as LaRoza mentions, using eval() as a shortcut is bad. And if you don't enter a number or "q", it crashes..
ya your right.
How would I do this better?

---

### Post by LaRoza on 2008-07-11
> **MDSmith2 said:**
> ya your right.
How would I do this better?

[php]
#!/usr/bin/python 
try:
    eval(raw_input("Enter: "))
except(NameError):
    print "Not valid input"
[/php]

Here is a real calculator. Run it with no arguments for a prompt, or run it with the expression you wish to evaluate as a command line argument.
[php]
#!/usr/bin/python
import sys

def main(argv=False):
    if not argv:
        inpu = raw_input("Eval: ").split()
    else:
        inpu = argv[1:]
    total = 0
    stack = []

    for i in inpu:
        if i.isdigit():
            stack.append(float(i))
        elif i in ("+","p"):
            total = stack.pop() + stack.pop()
            stack.append(total)
        elif i in ("*","t"):
            total = stack.pop() * stack.pop()
            stack.append(total)
        elif i in ("-","s"):
            total = -stack.pop() + stack.pop()
            stack.append(total)
        elif i in ("/","d"): 
            total = 1/stack.pop() / stack.pop()
            stack.append(total)
        else:
            print "Invalid input"

    print total


if __name__ == "__main__":
    if len(sys.argv) == 1:
        main()
    else:
        main(sys.argv)
[/php]

It is RPN, so you will have to use that notation. On the command line, use the letters instead of symbols if they conflict with the shell.

---

### Post by days_of_ruin on 2008-07-11
Eval is dangerous!And there is no real reason to use it in this case.
A calculator is blindingly easy to do in python so don't expect someone
else to make it for you.

---

### Post by ghostdog74 on 2008-07-11
> **days_of_ruin said:**
> Eval is dangerous!And there is no real reason to use it in this case.

eval is dangerous only when you don't know what you are doing. Its there for you to use , with proper sanitization going through the input elements one by one, raise error when they are not numbers etc .

---

### Post by pmasiar on 2008-07-11
> **days_of_ruin said:**
> Eval is dangerous!

Eval is neat sharp tool. Sharp tools are dangerous to be useful. :-) Last thing you want is dull tool.

---

### Post by LaRoza on 2008-07-12
> **days_of_ruin said:**
> Eval is dangerous!And there is no real reason to use it in this case.

It fulfilled the users request in the least amount of code (essentially just a Python prompt, which is often used as a calculator)

> 
A calculator is blindingly easy to do in python so don't expect someone
else to make it for you.
Don't expect it, although I did :-) It is just an RPN calculator (a ECMAScript I wrote for a webpage translated to Python). To make it infix is an exercise for the reader.

---

### Post by days_of_ruin on 2008-07-12
> **pmasiar said:**
> Eval is neat sharp tool. Sharp tools are dangerous to be useful. :-) Last thing you want is dull tool.
There is still no good reason to use it in this case.
Also whoever is using the calculator might expect "5 / 2" to return 2.5
but it wouldn't if you used eval.

---

### Post by LaRoza on 2008-07-12
> **days_of_ruin said:**
> There is still no good reason to use it in this case.
Considering it is no more than a Python prompt, you are right. There is no reason to use it.

> 
Also whoever is using the calculator might expect "5 / 2" to return 2.5
but it wouldn't if you used eval.

Silly "whoever"... That makes perfect sense. Integer division should yield an integer, even in scientific computing if you go by significant digits.

---

### Post by ghostdog74 on 2008-07-12
> **days_of_ruin said:**
> 
Also whoever is using the calculator might expect "5 / 2" to return 2.5
but it wouldn't if you used eval.
it is up to programmer to define that. 
```

>>> from __future__ import division
>>> eval("5/2")
2.5

```

---

