---
title: "Need help"
date: 2005-05-24
forum: Programming Talk
---

### Post by nightshift on 2005-05-24
Hello, iv just started using ubuntu(and linux) and trying to learn python, I'm new to both with no previous experience and need some help. I started reading the Dive Into Python tutorial and am following the 1st program example, but cant get it to run, not sure where i'v went wrong, the instruction from the tutorial is that you can run a program from the command line: python odbchelper.py
The program looks like this, which i wrote using the normal terminal,(applications>system tools>terminal) any help would be appreiciated:

python
Python 2.4.1 (#2, Mar 30 2005, 21:51:10)
[GCC 3.3.5 (Debian 1:3.3.5-8ubuntu2)] on Linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> def buildConnectionString(params):
...     """Build a connection string from a dictionary of parameters.
...
...     Returns string."""
...     return ";".join(["%s=%s" % (k, v) for k, v in params.items()])
...
>>> if __name__ == "__main__":
...     myParams = {"server":"mpilgrim", \
...                 "database":"master", \
...                 "uid":"sa", \
...                 "pwd":"secret" \
...                 }
...     print buildConnectionString(myParams)
... python odbchelper.py
  File "<stdin>", line 8
    python odbchelper.py
         ^
SyntaxError: invalid syntax

---

### Post by Swab on 2005-05-24
You should be typing the program into a text editor, saving it as odbchelper.py , then run it by typing "python odbchelper.py"

Also remember that you need to indent each code block, so type it exactly the way it's shown in the book.

---

