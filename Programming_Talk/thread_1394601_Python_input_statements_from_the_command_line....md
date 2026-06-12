---
title: "Python input statements from the command line..."
date: 2010-01-30
forum: Programming Talk
---

### Post by Stev0 on 2010-01-30
Another question from the new guy, probably something stupid I'm over looking. My python module runs perfectly from the IDE, however when I attempt to run it from the command line, all of the input is returning a syntax error unless I enclose it in ' '. 

For example, in the IDE, inputting /var/log/daemon.log works fine, from the command line, that same string will result in a syntax error unless I input it as '/var/log/daemon.log', at which point it will function as intended. Why is this, and how do I fix it? A cursory google search didn't reveal anything, so I'm at a loss here. I'm coding it as follows in python 3.0

path = input("Enter the path to the file:")

---

### Post by Axos on 2010-01-30
I cannot reproduce the problem. Here's what I tried:

```

$ python3.1 intest.py
Enter the path to the file:/var/log/daemon.log
/var/log/daemon.log
$ cat intest.py
path = input("Enter the path to the file:")
print(path)

```

Is there any chance some module you are using has replaced the built-in input function?

---

### Post by Stev0 on 2010-01-30
Suppose I should have displayed exactly what I'm doing with the string. I'm not just printing it to the screen, its being stored and used in conjunction with a Regular Expression.```


path = input("Enter the path to the file")
expr = input("Enter an expression")

r = re.compile(expr)

f = open(path, 'r')
```

Again works fine in the IDE, soon as I try to run it from the command line it spits out the syntax error. It doesnt even pause for the next input string, throws an immediate syntax error, pointing to the slash in /var/log/daemon.log

---

### Post by Axos on 2010-01-30
Still works. Someone with more experience than I have with Python will probably know what's wrong.
```

$ cat intest.py
import re

path = input("Enter the path to the file")
expr = input("Enter an expression")

r = re.compile(expr)

f = open(path, 'r')
$ python3.1 intest.py
Enter the path to the file/var/log/daemon.log
Enter an expressionpotato pancake
$ 

```

To make sure you are calling the "real" input function, try this:

```

import re
import builtins

path = builtins.input("Enter the path to the file")
expr = builtins.input("Enter an expression")

r = re.compile(expr)

f = open(path, 'r')

```

Here's an explanation: [http://docs.python.org/3.1/library/builtins.html?highlight=builtin#module-builtins](http://docs.python.org/3.1/library/builtins.html?highlight=builtin#module-builtins)

---

### Post by matja on 2010-01-31
Hi StevO,

Are you sure you're using Python 3 when you run it from the command line? If so, ignore the rest of this post. Otherwise, in Python 2.x, the input() function evaluates the string it is given as a Python expression and that would most likely result in the error you're getting (raw_input() in 2.x is the equivalent of input() in 3.x). If you're running Ubuntu, you probably have to run the "python3" executable and not just "python", i.e.,
```
$ python3 myfile.py
```
Just to make sure, you can always check the actual version of the Python interpreter by giving it a '--version' option. I get
```
$ python --version
Python 2.6.4
```

Regards,
Mattias

---

