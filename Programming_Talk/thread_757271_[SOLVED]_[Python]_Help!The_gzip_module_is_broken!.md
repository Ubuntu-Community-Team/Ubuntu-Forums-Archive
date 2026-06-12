---
title: "[SOLVED] [Python] Help!The gzip module is broken!"
date: 2008-04-16
forum: Programming Talk
---

### Post by days_of_ruin on 2008-04-16
When I import gzip it gives me this error
```

Traceback (most recent call last):
  File "gziptest.py", line 2, in <module>
    import gzip
  File "/usr/lib/python2.5/gzip.py", line 5, in <module>
    
AttributeError: 'module' object has no attribute 'GzipFile'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 20, in <module>
    from problem_report import ProblemReport
  File "/var/lib/python-support/python2.5/problem_report.py", line 15, in <module>
    import zlib, base64, time, UserDict, sys, gzip, struct
  File "/usr/lib/python2.5/gzip.py", line 5, in <module>
    
AttributeError: 'module' object has no attribute 'GzipFile'

Original exception was:
Traceback (most recent call last):
  File "gziptest.py", line 2, in <module>
    import gzip
  File "/usr/lib/python2.5/gzip.py", line 5, in <module>
    
AttributeError: 'module' object has no attribute 'GzipFile'

shell returned 1

Press ENTER or type command to continue
```

What!? It doesn't even get to the rest of my program(which is just a test for gzip).I actually looked inside "gzip.py" and it is there.
Why in the world doesn't it work?

---

### Post by LaRoza on 2008-04-16
Open a terminal, type "python" then "import gzip"

Does that still give errors?

---

### Post by days_of_ruin on 2008-04-16
Only if its in the same directory.
But I just solved the problem.I had foolishly named a program gzip.py
and had deleted hoping to solve my problem.But I forgot to remove
the swap file.:lolflag:
It works now, thanks!

---

### Post by LaRoza on 2008-04-16
> **days_of_ruin said:**
> Only if its in the same directory.
But I just solved the problem.I had foolishly named a program gzip.py
and had deleted hoping to solve my problem.But I forgot to remove
the swap file.
It works now, thanks!

That was my second guess.

I have done it before....

---

