---
title: "Python problem"
date: 2007-04-28
forum: Programming Talk
---

### Post by underworld288 on 2007-04-28
I am currently still at a beginners level of python programming and I am try to type a program to just have a conversation with people. Well, the problem is I am try to type a question in so it doesn't take the input and use it somewhere else. I was thinking something like this...

```
raw_input("How are you? ")
```

The only problem is when you type the answer in in replies back with what you typed in, I don't want that. Can someone give me some advice or something that would make this work?

thanks 
andrew

---

### Post by pmasiar on 2007-04-28
you want not the value user entered, but something else? like what?

---

### Post by seamless on 2007-04-28
> **pmasiar said:**
> you want not the value user entered, but something else? like what?
He wants nothing echoed back like in the case of entering a password.

You will need to manipulate the terminal itself using termios. For example
```
import fcntl, os, sys, termios

def main():
    fd = sys.stdin.fileno()
    oldterm = termios.tcgetattr(fd)
    newattr = termios.tcgetattr(fd)
    newattr[3] = newattr[3] & ~termios.ICANON & ~termios.ECHO
    termios.tcsetattr(fd, termios.TCSANOW, newattr)

    oldflags = fcntl.fcntl(fd, fcntl.F_GETFL)
    fcntl.fcntl(fd, fcntl.F_SETFL, oldflags | os.O_NONBLOCK)

    result = raw_input("How are you? ")

    if result == "yes":
        do_something()

    termios.tcsetattr(fd, termios.TCSAFLUSH, oldterm)
    fcntl.fcntl(fd, fcntl.F_SETFL, oldflags)

```

---

### Post by underworld288 on 2007-04-28
whoa, I am only a beginner programmer. what does all of the do? I put it in a .py file and tried to run it but got nothing back. 

andrew

---

### Post by raja on 2007-04-28
Perhaps as a beginner you should not be so fussy about not having input echoed. Just accept that it is not straightforward to do.

---

### Post by WW on 2007-04-28
If, in fact, you don't want the input echoed on the screen *as it is typed*, you can use [getpass]("http://docs.python.org/lib/module-getpass.html").  For example,
```

from getpass import getpass

s = getpass("What is your password? ")
print "Your password is:", s

```

But it is not clear that that is what you actually want.  Could you provide some more details about what you want to do?

---

### Post by WW on 2007-04-28
Or, are you trying something like this, working interactively with python:
```

~$ python
Python 2.4.3 (#2, Oct  6 2006, 07:52:30)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> raw_input("How old are you? ")
How old are you? 99
'99'
>>>

```
In this case, it is normal for python to print the result of the call to raw_input, because it has not been assigned to a variable.  Try this instead:
```

>>> s = raw_input("How are you? ")
How are you? fine
>>> print s
fine
>>>

```

---

### Post by underworld288 on 2007-04-29
Thanks WW your secong example helped me, I could just give the input a variable then just never use that variable. 

Thanks

---

