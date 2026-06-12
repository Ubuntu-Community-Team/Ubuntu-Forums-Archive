---
title: "[Python]How to attach video in a mail"
date: 2011-06-25
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-25
hey all .....i wanted to ask how do you attach a video in a email in python script...i know how to attach image and text fro MIMEImage and MIMEText but thre is nothing like MIMEVideo .... plzz help...
If u can show me with a code snippet it  wud be really helpful....
Thanks in advance.....:)

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-26
...yes i did it :) it can be done by using MIMEBase

---

### Post by juancarlospaco on 2011-06-26
1) Post the Solution Code Example
2) Mark as Solved
3) Thank you

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-26
```

#! /usr/bin/env python
import smtplib
import os,email
from email.MIMEMultipart import MIMEMultipart
from email.MIMEBase import MIMEBase
from email.MIMEText import MIMEText
#from email.Utils import COMMSPACE,formatdate
from email import Encoders

def send_mail(send_from, send_to, subject, text, file):
    
    msg = MIMEMultipart()
    msg['From'] = send_from
    msg['To'] = send_to
    msg['Date'] = " Use any date time module to insert or use email.utils formatdate"
    msg['Subject'] = subject
    
    msg.attach( MIMEText(text) )
    part = MIMEBase('application', "octet-stream")
    fo=open(files,"rb")
    part.set_payload(fo.read() )
    Encoders.encode_base64(part)
    part.add_header('Content-Disposition', 'attachment; filename="%s"' % os.path.basename(file))
    msg.attach(part)

    smtp = smtplib.SMTP("smtp.gmail.com",587) #Email id  for yahoo use smtp.mail.yahoo.com
    smtp.ehlo()
    smtp.starttls  #in yahoo use smtplib.SMTP_SSL()
    smtp.ehlo()
    smtp.login("ur id","password") #Edit
    sent=smtp.sendmail(send_from, send_to, msg.as_string())
    smtp.close()
    return sent
    

s=send_mail("Your email add","recipient email add","Mail test","Message","Path to file")  # Edit
if (s.keys()==[]):
    print "Message Sent!!!!!!!!!"
else:
    print "Error!!!!"


```

---

