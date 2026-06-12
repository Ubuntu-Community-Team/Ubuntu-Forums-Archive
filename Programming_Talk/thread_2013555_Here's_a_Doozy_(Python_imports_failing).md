---
title: "Here's a Doozy (Python imports failing)"
date: 2012-07-01
forum: Programming Talk
---

### Post by Dubslow on 2012-07-01
```
#! /usr/bin/python3

import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.application import MIMEApplication
from email.mime.text import MIMEText
from email.utils import formatdate
```

```
bill@Gravemind:~/bin/py&#8752;&#8706; email.py 
Traceback (most recent call last):
  File "/home/bill/bin/py/email.py", line 3, in <module>
    import smtplib
  File "/usr/lib/python3.2/smtplib.py", line 47, in <module>
    import email.utils
  File "/home/bill/bin/py/email.py", line 4, in <module>
    from email.mime.multipart import MIMEMultipart
ImportError: No module named mime.multipart
```
:-k

___________________________________________________________

[http://docs.python.org/py3k/library/email-examples.html](http://docs.python.org/py3k/library/email-examples.html)
[quote=^Link]
```
#!/usr/bin/env python3
<snip>
from email import encoders
from email.message import Message
from email.mime.audio import MIMEAudio
from email.mime.base import MIMEBase
from email.mime.image import MIMEImage
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
```[/quote]

```
bill@Gravemind:/usr/lib/python3.2/email/mime&#8752;&#8706; ls
application.py  base.py   __init__.py  multipart.py     __pycache__
audio.py        image.py  message.py   nonmultipart.py  text.py
```
So the files are definitely there... try reordering?
```
#! /usr/bin/python3
import smtplib
from email.utils import formatdate
from email.mime.application import MIMEApplication
from email.mime.multipart import MIMEMultipart
from email.mime.text import MIMEText
```
```
bill@Gravemind:/usr/lib/python3.2/email&#8752;&#8706; ls 
base64mime.py  feedparser.py  iterators.py   parser.py
charset.py     generator.py   message.py     __pycache__
encoders.py    header.py      mime           quoprimime.py
errors.py      __init__.py    _parseaddr.py  utils.py
bill@Gravemind:/usr/lib/python3.2/email&#8752;&#8706; email.py 
Traceback (most recent call last):
  File "/home/bill/bin/py/email.py", line 3, in <module>
    import smtplib
  File "/usr/lib/python3.2/smtplib.py", line 47, in <module>
    import email.utils
  File "/home/bill/bin/py/email.py", line 4, in <module>
    from email.utils import formatdate
ImportError: No module named utils
```
:-s

---

### Post by MadCow108 on 2012-07-01
rename the file email.py to something else
else it tries to import that file which obviously does not have the mime module

---

### Post by Tony Flury on 2012-07-02
Maybe a deeper dive explanation for the OP : 

Python as a default searches for imports in the local folder first, and then searches installed libraries in a specified order.

[http://docs.python.org/reference/simple_stmts.html#import](http://docs.python.org/reference/simple_stmts.html#import)

*You can change the search order if you wish, but not recommended unless you know what you are doing.*

The default search order is useful - say for instance you are developing and testing an update to a standard library - you just have to have the development copy of the library in your local directory, and any test program you write in that directory will use your development version, but it does have it's down falls - as you have seen.

In general avoid names for local files which clash with top level standard library module names - I use prefixes on my Module file names to avoid clashes where possible.

---

