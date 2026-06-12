---
title: "Python - Import Failure"
date: 2007-02-11
forum: Programming Talk
---

### Post by ngms27 on 2007-02-11
Hi,

I'm trying to send a HTML email following this example: [http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/473810](http://aspn.activestate.com/ASPN/Cookbook/Python/Recipe/473810) and I'm getting a 

Traceback (most recent call last):
  File "email.py", line 4, in ?
    from email.MIMEMultipart import MIMEMultipart
  File "/home/ngms27/Desktop/email.py", line 4, in ?
    from email.MIMEMultipart import MIMEMultipart
ImportError: No module named MIMEMultipart

The module is installed on my system under /usr/lib/python2.4/email/MIMEMultipart.py

Any ideas why the import is failing?

---

### Post by prensing on 2007-02-19
I suspect your problem is a name conflict between "email.py" in your Desktop directory and the standard email package. Python appears to be loading your "email.py". Then when it goes to look for MIMEMultipart, it can't find it inside "email" because "email" is your file, not the standard package.

Try renaming your file to something else like "myemail.py".

---

### Post by po0f on 2007-02-19
prensing,

I remember this one.  ngms27 figured it out.  It was a case of double posting and one post getting an answer and the other one getting left out in the cold, un-updated.  :)

---

