---
title: "Sending mail from a python script ?"
date: 2008-05-24
forum: Programming Talk
---

### Post by brijith on 2008-05-24
Hai,

Anybody know how to send a mail to a mail account such as gmail using python  script.


**[COLOR="Sienna"]Thanks[/COLOR]**

---

### Post by Steve Zenone on 2008-05-24
> **brijith said:**
> Hai,

Anybody know how to send a mail to a mail account such as gmail using python  script.


**[COLOR="Sienna"]Thanks[/COLOR]**

Here you go -- have fun...

```
#!/usr/bin/python
import smtplib

SERVER = "your.smtp.server"

FROM = "my@email.com"
TO = ["your@email.com"] 

SUBJECT = "Testing"

TEXT = "This is a test email using Python."

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

---

### Post by ghostdog74 on 2008-05-24
always look at the [docs]("http://docs.python.org/lib/SMTP-example.html").

---

### Post by brijith on 2008-05-24
Hi thanks for the reply 

In the following link it describes how to send a mail from command line using mutt. I tried it in my system but it failed. I didn't shown any error. I didn't received the mail in my Gmail account. but when I tried the same from a pc which act as proxy for our local office network it is working perfectly. I read a some thing like You need a working Mail Transfer Agent (MTA) such as sendmail or postfix. I am assuming that you have configured email server. in the following link. I think
our proxy system have all these things configured. that's why it is working in it and not in my PC. Can any one give the steps to configure sendmail or postfix.

[http://www.cyberciti.biz/tips/sending-mail-with-attachment.html]("http://www.cyberciti.biz/tips/sending-mail-with-attachment.html")


[COLOR="Sienna"]Thanks[/COLOR]

---

