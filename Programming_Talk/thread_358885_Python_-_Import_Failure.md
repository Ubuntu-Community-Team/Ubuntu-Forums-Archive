---
title: "Python - Import Failure"
date: 2007-02-11
forum: Programming Talk
---

### Post by ngms27 on 2007-02-11
Hi,

Trying to use pythons email functionality and am getting this error:

Traceback (most recent call last):
  File "email.py", line 4, in ?
    from email.MIMEMultipart import MIMEMultipart
  File "/home/ngms27/Desktop/email.py", line 4, in ?
    from email.MIMEMultipart import MIMEMultipart
ImportError: No module named MIMEMultipart

The file should import as its in /usr/lib/python2.4/email

Any ideas?

---

### Post by po0f on 2007-02-11
ngms27,

You don't happen to have python2.5 installed, do you?

---

### Post by ngms27 on 2007-02-12
No, Python 2.5 isn't installed

---

### Post by ngms27 on 2007-02-12
Fixed it. I called my test program email.py so python found that instead of searching in the lib directories!!!

JonnyT

---

