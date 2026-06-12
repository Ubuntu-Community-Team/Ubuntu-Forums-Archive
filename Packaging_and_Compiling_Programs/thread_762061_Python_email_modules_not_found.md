---
title: "Python email modules not found"
date: 2008-04-21
forum: Packaging and Compiling Programs
---

### Post by cudjoe on 2008-04-21
Hi all,

I am facing a little problem, and I am getting mad ! Last hope is the forum !

I want to use the email.Parser, email.Utils, ... modules under Gutsy.

```
import email, email.Header, email.Message, email.Utils

ImportError: No module named Header
Error in sys.excepthook:
.....

```

I had a look in* /usr/lib/python2.5/email/*
```
base64mime.py   errors.py       header.py      message.py      parser.pyc
base64mime.pyc  errors.pyc      header.pyc     message.pyc     quoprimime.py
charset.py      feedparser.py   __init__.py    mime            quoprimime.pyc
charset.pyc     feedparser.pyc  __init__.pyc   _parseaddr.py   utils.py
encoders.py     generator.py    iterators.py   _parseaddr.pyc  utils.pyc
encoders.pyc    generator.pyc   iterators.pyc  parser.py
```

Modules and classes are here !

Any ideas ? Thanks !

---

### Post by deuce868 on 2008-04-22
Double check that your python is pointed at the 2.5 version and not the 2.4 

python --version

If it's the 2.4 then you're looking in the wrong directories.

---

### Post by cudjoe on 2008-04-23
I am sorry I did not mention that.
Of course I had this checked :)

I had something really strange, like that :

```
cudjoe@-laptop:~/Code$ diff file1.py file2.py 
cudjoe@-laptop:~/Code$ python file1.py 
ok
cudjoe@-laptop:~/Code$ python file2.py 
Traceback (most recent call last):
  File "file2.py", line 3, in <module>
    import email, email.Errors, email.Header, email.Message, email.Utils
  File "/home/cudjoe/Code/file2.py", line 4, in <module>
    import email, email.Errors, email.Header, email.Message, email.Utils
ImportError: No module named Errors
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 20, in <module>
    from problem_report import ProblemReport
  File "/var/lib/python-support/python2.5/problem_report.py", line 17, in <module>
    from email.Encoders import encode_base64
  File "/home/cudjoe/Code/file2.py", line 4, in <module>
    import email, email.Errors, email.Header, email.Message, email.Utils
ImportError: No module named Errors

Original exception was:
Traceback (most recent call last):
  File "file2.py", line 3, in <module>
    import email, email.Errors, email.Header, email.Message, email.Utils
  File "/home/cudjoe/Code/file2.py", line 4, in <module>
    import email, email.Errors, email.Header, email.Message, email.Utils
ImportError: No module named Errors

```

The two files are identical. One was working, and the other was not.

I tied up everything (rm *.pyc, renamed and moved) and it now works. I can't reproduce it.

---

### Post by deuce868 on 2008-04-23
Well, glad things are working then.

---

