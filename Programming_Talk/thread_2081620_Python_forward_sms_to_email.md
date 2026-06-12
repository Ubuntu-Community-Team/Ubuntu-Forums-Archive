---
title: "Python forward sms to email"
date: 2012-11-07
forum: Programming Talk
---

### Post by omnicat on 2012-11-07
Hello all, 

Please i have a little problem. i wanted to know if there was a way I could get a form of help or a clue on how i can forward sms from my mobile  phone to my email address. i imported the inbox module ,but i got stuck along the line, please help.

---

### Post by hakermania on 2012-11-07
Welcome to the forums!

Please show what you have tried so far and explain better what exactly you are trying to achieve.

---

### Post by omnicat on 2012-11-08
good day,

i tried something like this, i just started.

the code goes a lil like this


---
[PHP]#!/usr/bin/python


import os
import sys
import wx
import inbox
import smtplib

app = wx.App()
frame = wx.Frame(None, -1, "SMS to Email Redirect")
frame.Show()
app.MainLoop()

[/PHP]

---

### Post by hakermania on 2012-11-08
You can use this code in order to send with python an attachment:

```

#!/usr/bin/python

#use as: python send.py "receiver@gmail.com" "My Topic" "My text" "My attachment.jpg"

import os, re, sys, smtplib, base64

from email.mime.multipart import MIMEMultipart
from email.mime.base import MIMEBase
from email.MIMEText import MIMEText
from email import encoders

SMTP_SERVER = 'smtp.gmail.com'
SMTP_PORT = 587

sender = 'myemail@gmail.com'

try:
	f1=open("email.conf", "r")
except IOError:
	password=raw_input("I don't have your password, please give it to me!\nPassword: ")
	f1=open("email.conf", "w")
	f1.write(base64.b64encode(password))
	f1.close()
else:
	password=base64.b64decode(f1.readline())
	f1.close()
recipient = sys.argv[1]
subject = ''
message = sys.argv[3]

def main():
	msg = MIMEMultipart()
	msg['Subject'] = sys.argv[2]
	msg['To'] = recipient
	msg['From'] = sender
	
	
	part = MIMEText('text', "plain")
	part.set_payload(message)
	msg.attach(part)
	
	session = smtplib.SMTP(SMTP_SERVER, SMTP_PORT)
	
	session.ehlo()
	session.starttls()
	session.ehlo
	
	session.login(sender, password)
	
	fp = open(sys.argv[4], 'rb')
	msgq = MIMEBase('audio', 'audio')
	msgq.set_payload(fp.read())
	fp.close()
	# Encode the payload using Base64
	encoders.encode_base64(msgq)
	# Set the filename parameter
	filename=sys.argv[4]
	msgq.add_header('Content-Disposition', 'attachment', filename=filename)
	msg.attach(msgq)
	# Now send or store the message
	qwertyuiop = msg.as_string()
	
	
	
	session.sendmail(sender, recipient, qwertyuiop)
	
	session.quit()
	os.system('notify-send "Email sent"')

if __name__ == '__main__':
	main()

```

Edit the [email]myemail@gmail.com[/email] in the above code to match your e-mail. The first time the script runs it will ask you for your password. It will save it at a .conf file in base64 encoding so as not to be in plain text mode available to anyone... Use as:

```

python send.py "receiver@gmail.com" "My Topic" "My text" "My attachment.jpg"

```
DO NOT give the above script the name email.py (give it any other name, like send_email.py)!

Now, you have to figure out how to save your SMS into a .txt file and send it as an attachment to a recipient of your preference...

---

