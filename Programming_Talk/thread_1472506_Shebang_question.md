---
title: "Shebang question"
date: 2010-05-04
forum: Programming Talk
---

### Post by xaegis on 2010-05-04
It appears that my IDE (Geany) will not recognize my shebang. Am I doing something wrong?

```

#!/usr/bin/env python3

foo=input("You should type some stuff!:")
print (foo)

```

It appears that the "input" command will not accept strings even though, if I recall correctly, it should: as of Python v. 3.0.

What gives?

---

### Post by doas777 on 2010-05-04
well, does the filename end in .py, and have you saved the document, or set the format in geany?

also geany itself may not be ready for py3, or you need a newer version than what is in the repos.

---

### Post by xaegis on 2010-05-04
> **doas777 said:**
> well, does the filename end in .py, and have you saved the document, or set the format in geany?

also geany itself may not be ready for py3, or you need a newer version than what is in the repos.

The Geany version in Repo is 0.18 and the latest is 0.18.1. whenever I try to invoke the script from the shell I get the same undefined error. It is as though python3 is not available even through the terminal unless I invoke it by using: "python3" first, but the shebang is not affecting the script at all.

The document is saved as a .py file.

does the input() function handle strings for anyone else?

---

### Post by Bachstelze on 2010-05-04
> **xaegis said:**
> The Geany version in Repo is 0.18 and the latest is 0.18.1. whenever I try to invoke the script from the shell I get the same undefined error. It is as though python3 is not available even through the terminal unless I invoke it by using: "python3" first, but the shebang is not affecting the script at all.

How are you running your script in the shell?

---

### Post by xaegis on 2010-05-04
> **Bachstelze said:**
> How are you running your script in the shell?

python3 foo.py

But you know now it is working from terminal.
:confused:

still no love from geany or SPE!

---

### Post by Bachstelze on 2010-05-04
> **xaegis said:**
> 
still no love from geany or SPE!

They probably don't use the shebang line at all. It is generally only used when you run the script from a shell by typing its path, like

```
./script.py
```

Look in the preferences if they let you choose the Python version, also try to see on their mailing lists if anyone asked the same question.

---

### Post by xaegis on 2010-05-04
Yeah you're right. If I set the source file execution to: "python3" it solves the problem. But it will no longer access PyQt4 modules
```
Traceback (most recent call last):
  File "TitleScreen.py", line 7, in <module>
    from PyQt4 import QtGui, QtCore
ImportError: No module named PyQt4

```

So then the question becomes how do I get python3 to use the python 2.6 modules on my system?

---

### Post by Bachstelze on 2010-05-04
> **xaegis said:**
> 
So then the question becomes how do I get python3 to use the python 2.6 modules on my system?

The answer is; you can't. Modules that were specifically built for one version of Python won't work in another. You could try to build PyQT for Python 3, but why not just use Python 2.6?

---

### Post by xaegis on 2010-05-04
The online tutorials I was using were Python3 specific. And I thought it was something I was doing wrong. But now that I know that I can just make things backward compatible i.e. input -> raw_input for strings, etc.
Thanks for clearing that up for me.
:D

---

