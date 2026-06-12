---
title: "problem Removing HTML tags in a file using python"
date: 2009-09-12
forum: Programming Talk
---

### Post by Suji_A on 2009-09-12
[SIZE=1]#!/usr/bin/python
import re
import os, sys, glob
from os import system
from urllib import urlopen
page = urlopen("http://dsal.uchicago.edu/cgi-bin/philologic/search3advanced?dbname=tamillex&query=%E0%AE%95&searchdomain=headwords&matchtype=start&display=utf8").read()
myfile = open('testfile.txt', 'w')
myfile.write(page)
myfile = open('testfile.txt', 'r')

#Removing all the HTML tags from the file
myfile = re.sub('<(?!(?:a\s|/a|!))[^>]*>','',page)
print myfile[/SIZE]


[SIZE=1]The above is the python program, when i run that program i got the follwing error


Traceback (most recent call last):
  File "lexicon.py", line 3, in <module>
    import os, sys, glob
  File "/usr/lib/python2.6/glob.py", line 75, in <module>
    magic_check = re.compile('[*?[]')
AttributeError: 'module' object has no attribute 'compile'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 38, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.6/subprocess.py", line 404, in <module>
    import pickle
  File "/usr/lib/python2.6/pickle.py", line 165, in <module>
    __all__.extend([x for x in dir() if re.match("[A-Z][A-Z0-9_]+$",x)])
AttributeError: 'module' object has no attribute 'match'

Original exception was:
Traceback (most recent call last):
  File "lexicon.py", line 3, in <module>
    import os, sys, glob
  File "/usr/lib/python2.6/glob.py", line 75, in <module>
    magic_check = re.compile('[*?[]')
AttributeError: 'module' object has no attribute 'compile'[/SIZE]



[SIZE=1]What this error means?:confused:how to solve this?


Thanks in advance[/SIZE]

---

### Post by G|N| on 2009-09-12
This is the function i use to remove html:
```

#!/usr/bin/python
import os, sys, glob
from os import system
from urllib import urlopen
import formatter
import htmllib
import cStringIO

page = urlopen("http://dsal.uchicago.edu/cgi-bin/philologic/search3advanced?dbname=tamillex&query=%E0%AE%95&se archdomain=headwords&matchtype=start&display=utf8" ).read()
myfile = open('testfile.txt', 'w')
myfile.write(page)
myfile = open('testfile.txt', 'r')
content = myfile.read() # You forgot this!

#Removing all the HTML tags from the file
#myfile = re.sub('<(?!(?:a\s|/a|!))[^>]*>','',page)
outstream = cStringIO.StringIO()
parser = htmllib.HTMLParser(formatter.AbstractFormatter(formatter.DumbWriter(outstream)))
parser.feed(content)
content = outstream.getvalue()
outstream.close()

print content


```

---

