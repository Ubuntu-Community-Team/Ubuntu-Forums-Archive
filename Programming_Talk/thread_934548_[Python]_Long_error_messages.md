---
title: "[Python] Long error messages"
date: 2008-09-30
forum: Programming Talk
---

### Post by nuclearj on 2008-09-30
I am getting these long error messages when they used to be short.

```

>>> reply = '20'
>>> reply ** 2
orig: string, modified: sgring
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for ** or pow(): 'str' and 'int'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 38, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.5/site-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.5/site-packages/apport/report.py", line 20, in <module>
    from problem_report import ProblemReport
  File "/usr/lib/python2.5/site-packages/problem_report.py", line 18, in <module>
    from email.MIMEMultipart import MIMEMultipart
  File "/usr/lib/python2.5/email/__init__.py", line 79, in __getattr__
    __import__(self.__name__)
  File "/usr/lib/python2.5/email/mime/multipart.py", line 9, in <module>
    from email.mime.base import MIMEBase
  File "/usr/lib/python2.5/email/mime/base.py", line 9, in <module>
    from email import message
  File "/usr/lib/python2.5/email/message.py", line 16, in <module>
    import email.charset
  File "/usr/lib/python2.5/email/charset.py", line 13, in <module>
    import email.quoprimime
  File "/usr/lib/python2.5/email/quoprimime.py", line 48, in <module>
    from string import hexdigits
ImportError: cannot import name hexdigits

Original exception was:
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for ** or pow(): 'str' and 'int'


```

Does anyone have an idea how to get it back to normal?

---

### Post by shadylookin on 2008-09-30
well for one thing you can't take a string to a power. 

when you put something in quotes it assumes it's a string

>>> reply = 20
>>> reply ** 2
400

---

### Post by jpeddicord on 2008-09-30
No, that's because you (or a module) is importing a bunch of other modules. When an error occurs in one of those deeper-level modules, it will print every file and call leading up to it until the error is reached. It's called a traceback, and they are very handy for pinpointing exactly where your code was when an error occurred.

**EDIT:** Though in this case, it looks like Apport is trying to run to report a bug when Python errors out. Report a bug on Launchpad after searching to see if you can't find a similar one. Choice words to search for: traceback python apport

---

### Post by nuclearj on 2008-10-10
> **jacobmp92 said:**
> No, that's because you (or a module) is importing a bunch of other modules. When an error occurs in one of those deeper-level modules, it will print every file and call leading up to it until the error is reached. It's called a traceback, and they are very handy for pinpointing exactly where your code was when an error occurred.

**EDIT:** Though in this case, it looks like Apport is trying to run to report a bug when Python errors out. Report a bug on Launchpad after searching to see if you can't find a similar one. Choice words to search for: traceback python apport


Thanks for that, I use Konsole do do my program editing and I switched the python directory for and unrelated reason, and now the error msgs are back to normal!  I guess it was something in that directory that did it...

---

