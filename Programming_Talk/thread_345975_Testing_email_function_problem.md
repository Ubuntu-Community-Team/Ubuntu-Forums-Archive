---
title: "Testing email function problem"
date: 2007-01-25
forum: Programming Talk
---

### Post by moonhk on 2007-01-25
I want to testing email function, but I need below problem

where email module at below location
/usr/lib/python2.4/email


# Import smtplib for the actual sending function
import smtplib

# Import the email modules we'll need
from email import MIMEText

textfile='/home/moonhk/hello.txt'
# Open a plain text file for reading.  For this example, assume that
# the text file contains only ASCII characters.

fp = open(textfile, 'rb')
# Create a text/plain message
msg = MIMEText(fp.read())
fp.close()

**Result:**
/usr/bin/python -u  "/home/moonhk/python/sendmail.py"
Traceback (most recent call last):
  File "/home/moonhk/python/sendmail.py", line 13, in ?
    msg = MIMEText(fp.read())
TypeError: 'module' object is not callable

I just base on below example

7.1.13 Examples

Here are a few examples of how to use the email package to read, write, and send simple email messages, as well as more complex MIME messages.

First, let's see how to create and send a simple text message: 

# Import smtplib for the actual sending function
import smtplib

# Import the email modules we'll need
from email.mime.text import MIMEText

# Open a plain text file for reading.  For this example, assume that
# the text file contains only ASCII characters.
fp = open(textfile, 'rb')
# Create a text/plain message
msg = MIMEText(fp.read())
fp.close()

# me == the sender's email address
# you == the recipient's email address
msg['Subject'] = 'The contents of %s' % textfile
msg['From'] = me
msg['To'] = you

# Send the message via our own SMTP server, but don't include the
# envelope header.
s = smtplib.SMTP()
s.connect()
s.sendmail(me, [you], msg.as_string())
s.close()

---

