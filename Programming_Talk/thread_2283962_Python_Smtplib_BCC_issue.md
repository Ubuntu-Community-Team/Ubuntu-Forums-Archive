---
title: "Python Smtplib BCC issue?"
date: 2015-06-26
forum: Programming Talk
---

### Post by ericmachine on 2015-06-26
Hi everyone,

I wonder anyone can assist on this.

I have this python code which can send email.

```

import smtplib
import string
import sys
import os


fromaddr = 'first-email@gmail.com'


toaddr = 'second-email@gmail.com'
cc = []
bcc = ['third-email@gmail.com', 'forth-email@gmail.com']
subject = 'This is a test email'


msg = string.join((
        'From: %s' % fromaddr,
        'To: %s' % toaddr,
        'CC: %s' % ', '.join(cc),
        'BCC: %s' % ', '.join(bcc),
        'Subject: %s' % subject, '',
        'hello world'
    ), '\r\n')


print msg


toaddrs = [toaddr] + cc + bcc


print toaddrs


server = smtplib.SMTP('smtp.googlemail.com',587)
server.starttls()
server.login('my_gmail_account','my_gmail_password')
server.sendmail(fromaddr,toaddrs,msg)
server.quit()

```

The problem I have is for those who I bcc'ed i.e. [email]third-email@gmail.com[/email] and [email]forth-email@gmail.com[/email], they could see who's inside the bcc'd list. 

Example,
From : [email]first-email@gmail.com[/email]
To : [email]second-email@gmail.com[/email]
Bcc : [email]third-email@gmail.com,forth-email@gmail.com[/email]

This is not the right format.

I am expecting the results should be like this.

a. For [email]second-email@gmail.com[/email] user

this person should see this

From : [email]first-email@gmail.com[/email]
To : [email]second-email@gmail.com[/email]
Bcc : this is hidden

b. For [email]third-email@gmail.com[/email] user

this person should see this

From : [email]first-email@gmail.com[/email]
To : [email]second-email@gmail.com[/email]
Bcc : [email]third-email@gmail.com[/email]

c. For [email]forth-email@gmail.com[/email] user

this person should see this

From : [email]first-email@gmail.com[/email]
To : [email]second-email@gmail.com[/email]
Bcc : [email]forth-email@gmail.com[/email]

Any way to enhance my python smtplib codes to achieve the above? 

Thanks in advance.

---

