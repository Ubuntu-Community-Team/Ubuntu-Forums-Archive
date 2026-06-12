---
title: "[ Python ] Need help with print - invalid syntax."
date: 2010-01-29
forum: Programming Talk
---

### Post by The Men on 2010-01-29
Python 3.1.1 - everytime I try to use print, I get an invalid syntax error. Am I missing something here ?

```
#!/usr/bin/env python

def showMessage(msg):
    print "Message:", msg
    
showMessage("Testing Python ..")

```

```
  File "sample.py", line 4
    print "Message:", msg
                   ^
SyntaxError: invalid syntax
```

---

### Post by unknownPoster on 2010-01-29
I believe in Python 3, print is now a function.

You should try:
```

print("Message:", msg)

```

---

### Post by The Men on 2010-01-29
Why would they do that ? Anyway, thank you for the answer - worked :)

---

### Post by steeleyuk on 2010-01-29
[Python 3 Print() Function]("http://docs.python.org/dev/3.0/whatsnew/3.0.html#print-is-a-function")

You can also use the brackets in 2.x without any problems, which is good for forward-compatibility in that respect.

---

### Post by Can+~ on 2010-01-29
> **The Men said:**
> Why would they do that ? Anyway, thank you for the answer - worked :)

Because now, print can be passed as a reference to other functions, or list comprehensions. For example, in python 2.6:

[PHP]>>> [print i for i in xrange(0, 10)][/PHP]

Although it makes sense to print each element inside this list, the statement nature of print screws up the syntax. On the other hand (Python 3):

[PHP]>>> [print(i) for i in range(0, 10)][/PHP]

Becomes valid syntax. This is my personal reason why I prefer it as a function, here's the real reason:

[PEP 3105: Make print a function]("http://www.python.org/dev/peps/pep-3105/")

*edit: Also, I just tried this out:
[PHP]>>> print(*range(0, 10), sep='|')[/PHP]

I think there's no easy way to achieve that with old print statement.

---

### Post by The Men on 2010-01-30
Thank you - explained it pretty well :) The only culprit I found is that you can easily redefine the print function and there are no alternatives to it .. Aren't there a way to protect it somehow ( static, classes .. ) ?

---

### Post by Can+~ on 2010-01-30
Python doesn't have static methods as a keyword like "static void foo(int bar)", but it does it with decorators

[PHP]class Foo(object):

    @staticmethod
    def foo():
        # ...[/PHP]

---

