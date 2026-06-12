---
title: "Sending mail with attachement through script"
date: 2010-11-17
forum: Programming Talk
---

### Post by mecrazycoder on 2010-11-17
Hi,
  I want to know how to send mail with attachment from script. I search to entire forum(other forums too), but I cant able to relate to my requirement. Basically these are my needs,

1. Sending log files from client to my email account.
2. They are using Ubuntu 10.04.
3. They just want to invoke some script after that script should install req packages(for sending mail) and automatically start sending mail to my account. 

I want to know what are the packages required for sending mail, how to install it through packages and commands to send the mail.

---

### Post by spjackson on 2010-11-17
> **mecrazycoder said:**
> 
  I want to know how to send mail with attachment from script. I search to entire forum(other forums too), but I cant able to relate to my requirement. Basically these are my needs,

1. Sending log files from client to my email account.
2. They are using Ubuntu 10.04.
3. They just want to invoke some script after that script should install req packages(for sending mail) and automatically start sending mail to my account. 

I want to know what are the packages required for sending mail, how to install it through packages and commands to send the mail.
Here is a Python script that sends an email attachment using smtp; it was written for images, but will work with log files. It takes 2 parameters: the recipient's email address and the name of a file to attach. There are no additional packages to install. It's not wondeful but it is something I quickly put together from examples I found on the internet.
```

#!/usr/bin/env python

import sys
import smtplib
from email.mime.image import MIMEImage
from email.mime.multipart import MIMEMultipart
from email.MIMEBase import MIMEBase
from email import Encoders

def mail(serverURL=None, sender='', to='', subject='', text='', filename=''):
    """
    Usage:
    mail('somemailserver.com', 'me@example.com', 'someone@example.com', 'test', 'This is a test', 'mypic.jpg')
    """
    #
    msg = MIMEMultipart()
    msg['Subject'] = subject
    msg['From'] = sender
    msg['To'] = to
    #
    part = MIMEBase('application', "octet-stream")
    fp = open(filename, 'rb')
    part.set_payload( fp.read() )
    fp.close()
    Encoders.encode_base64(part)
    part.add_header('Content-Disposition', 'attachment; filename="%s"'
                       % filename)
    msg.attach(part)
    #
    s = smtplib.SMTP(serverURL)
    s.sendmail(sender, to, msg.as_string())
    s.quit()

mail('somemailserver.com', 'me@example.com', sys.argv[1], "Scan of " + sys.argv[2], '', sys.argv[2] )

```

---

### Post by mecrazycoder on 2010-11-18
> **spjackson said:**
> Here is a Python script that sends an email attachment using smtp; it was written for images, but will work with log files. It takes 2 parameters: the recipient's email address and the name of a file to attach. There are no additional packages to install. It's not wondeful but it is something I quickly put together from examples I found on the internet.
```

#!/usr/bin/env python

import sys
import smtplib
from email.mime.image import MIMEImage
from email.mime.multipart import MIMEMultipart
from email.MIMEBase import MIMEBase
from email import Encoders

def mail(serverURL=None, sender='', to='', subject='', text='', filename=''):
    """
    Usage:
    mail('somemailserver.com', 'me@example.com', 'someone@example.com', 'test', 'This is a test', 'mypic.jpg')
    """
    #
    msg = MIMEMultipart()
    msg['Subject'] = subject
    msg['From'] = sender
    msg['To'] = to
    #
    part = MIMEBase('application', "octet-stream")
    fp = open(filename, 'rb')
    part.set_payload( fp.read() )
    fp.close()
    Encoders.encode_base64(part)
    part.add_header('Content-Disposition', 'attachment; filename="%s"'
                       % filename)
    msg.attach(part)
    #
    s = smtplib.SMTP(serverURL)
    s.sendmail(sender, to, msg.as_string())
    s.quit()

mail('somemailserver.com', 'me@example.com', sys.argv[1], "Scan of " + sys.argv[2], '', sys.argv[2] )

```
Thanks for ur reply. But where will you specify the ur email ID password.

---

### Post by spjackson on 2010-11-18
> **mecrazycoder said:**
> Thanks for ur reply. But where will you specify the ur email ID password.
The example I provided uses smtp not esmtp, and therefore no username/password is provided.

You didn't say anything about your network configuration, so I gave you one example that works in one configuration. If you need something else, you need to say what. Are you wanting to use smtp or esmtp (and tls?) or are you running an MTA such as Postfix? Or maybe you are using Microsoft Exchange Server or something else entirely.

---

### Post by spjackson on 2010-11-18
Here's a fragment that works with esmtp and tls (specifically tested with gmail.com).
```

    s = smtplib.SMTP(serverURL)
    s.ehlo()
    s.starttls()
    s.ehlo()
    s.login('username goes here ', 'password goes here')
    s.sendmail(sender, to, msg.as_string())
    s.quit()

```
But I don't know if this is what you need or not.

---

