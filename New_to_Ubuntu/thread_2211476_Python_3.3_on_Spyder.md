---
title: "Python 3.3 on Spyder"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by miguelmalheiro17 on 2014-03-16
Hi, Ubuntu is packed with python 2.7 and 3.3. I installed Spyder from the Software center, and it's running Python 2.7.
I want python 3.3, so in preferences->console->advanced settings I changed /usr/bin/python to /usr/bin/python3.3 and pythonstartup to default.

But I'm getting an error when the console starts:
Error in sitecustomize; set PYTHONVERBOSE for traceback:
SyntaxError: invalid syntax (sitecustomize.py, line 430)

And I can't run a file:
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'runfile' is not defined

Any help how to get Spyder to run python 3.3?
Thanks in advance

---

### Post by dniMretsaM on 2014-03-16
Check out this link for more info: [http://spyder-ide.blogspot.com/2013/01/spyder-v2114-supports-python-3.html](http://spyder-ide.blogspot.com/2013/01/spyder-v2114-supports-python-3.html)
There is also a beta of 2.3 out, currently, I believe. You could use that as well.

---

