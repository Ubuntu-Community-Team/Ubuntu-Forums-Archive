---
title: "Sending email from Python scripting -- using Gmail"
date: 2011-02-20
forum: Programming Talk
---

### Post by garfonzo on 2011-02-20
Ok, I want to send emails from within a Python script. I know how to do this by using Gmail's SMTP server to handle the delivery of the email. The problem is, I have to insert my email account password in plain text within the script. Here's what I have:

```


#!/usr/bin/python
import smtplib
import getpass

SMTP_SERVER = 'smtp.gmail.com'
SMTP_PORT = 587

sender = 'something_here@gmail.com'

#HERE'S THE PASSWORD, IN PLAIN TEXT
**password = 'secret_password'**
recipient = 'blah_blah@gmail.com'
subject = 'test email'
body = 'blah blah blah'

"Sends an e-mail to the specified recipient."

body = "" + body + ""

headers = ["From: " + sender,
           "Subject: " + subject,
           "To: " + recipient,
           "MIME-Version: 1.0",
           "Content-Type: text/html"]
headers = "\r\n".join(headers)

session = smtplib.SMTP(SMTP_SERVER, SMTP_PORT)

session.ehlo()
session.starttls()
session.ehlo

#THIS IS WHERE THE PASSWORD IS USED
**session.login(sender, password)**

session.sendmail(sender, recipient, headers + "\r\n\r\n" + body)
session.quit()

```

In order to use Gmail, I have to insert my password. I don't like this situation since I am planning on making CGI scripts to email stuff (ie: security risk I think) 

I have two questions: 
1) Is there a way to *not* have my password in plain text?
2) Is it worth installing/setting up something like Postfix to handle this kind of thing if I only want to send email, never receive?

(this server is running Ubuntu 10.04 and is in my home)

Thoughts?

---

### Post by ve4cib on 2011-02-20
In regards to question #1, probably not.  Typically the password is send as the raw string over an encrypted "tube" (since the internet is a series of tubes), and hashed on the other side.  So if you want the password in your .py script you'll need to leave it "in the clear."

You might be able to store the password in an encrypted file or password manager (seahorse comes to mind).  Your python script would then need to access that file/manager, authenticate itself, and extract the password at runtime.  This will slow your script down and make it a little more complicated, but it will make it more secure in that your password is not sitting there in the script.

---

