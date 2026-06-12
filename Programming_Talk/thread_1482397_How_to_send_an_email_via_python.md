---
title: "How to send an email via python ???"
date: 2010-05-13
forum: Programming Talk
---

### Post by hakermania on 2010-05-13
I had this script
```

#!/usr/bin/python
import smtplib

SERVER = "localhost"

FROM = "example@gmail.com"
TO = ["example@hotmail.com"] # must be a list

SUBJECT = "Hello!"

TEXT = "This message was sent with Python's smtplib."

# Prepare actual message

message = """\
From: %s
To: %s
Subject: %s

%s
""" % (FROM, ", ".join(TO), SUBJECT, TEXT)

# Send the mail

server = smtplib.SMTP(SERVER)
server.sendmail(FROM, TO, message)
server.quit()

```
And it has these errors:
[B]Traceback (most recent call last):
  File "./sntmleil.py", line 25, in <module>
    server = smtplib.SMTP(SERVER)
  File "/usr/lib/python2.6/smtplib.py", line 239, in __init__
    (code, msg) = self.connect(host, port)
  File "/usr/lib/python2.6/smtplib.py", line 295, in connect
    self.sock = self._get_socket(host, port, self.timeout)
  File "/usr/lib/python2.6/smtplib.py", line 273, in _get_socket
    return socket.create_connection((port, host), timeout)
  File "/usr/lib/python2.6/socket.py", line 514, in create_connection
    raise error, msg
socket.error: [Errno 111] Connection refused[/B]
And I find it logical because I normally have to declare a password or something for gmail. Can you actually tell me how can i make a script like this which works?

---

### Post by wmcbrine on 2010-05-13
For it to work as you've written it, you'd have to be running a mail server on your machine. I think that would be sufficient.

To use gmail is a bit more complicated, but here's a ready-made example:

[http://www.mkyong.com/python/how-do-send-email-in-python-via-smtplib/](http://www.mkyong.com/python/how-do-send-email-in-python-via-smtplib/)

---

### Post by StephenF on 2010-05-13
> **wmcbrine said:**
> For it to work as you've written it, you'd have to be running a mail server on your machine. I think that would be sufficient.
Not if the internet service provider has a policy of blocking port 25 as a spam prevention measure.

---

### Post by hakermania on 2010-05-14
Ok thank you!

---

### Post by yamex5 on 2011-10-21
> **StephenF said:**
> Not if the internet service provider has a policy of blocking port 25 as a spam prevention measure.

I have two questions please. 

First, if the port specified is 587, how does blocking port 25 affect anything? 

Second, assuming that blocking port 25 (or 587), is an issue, is there a workaround to send out gmail via python using the smtplib? 

Thanks, 

-Mike

---

