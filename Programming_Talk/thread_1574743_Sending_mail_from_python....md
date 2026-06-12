---
title: "Sending mail from python..."
date: 2010-09-14
forum: Programming Talk
---

### Post by ownaginatious on 2010-09-14
Okay, so I've been trying to figure out how to send an email from python, and I can't seem to get it to work. I'm trying to use 'sendmail', but for some reason I never seem to get any mail from it...

Here is the code everyone on the internet claims to work:

```

SENDMAIL = "/usr/sbin/sendmail" # sendmail location
import os
p = os.popen("%s -t" % SENDMAIL, "w")
p.write("To: cary@ratatosk.org\\n")
p.write("Subject: test\\n")
p.write("\\n") # blank line separating headers from body
p.write("Some text\\n")
p.write("some more text\\n")
sts = p.close()
if sts != 0:
    print "Sendmail exit status", sts

```

When I replace the email address following "To:" with my email address, I never receive anything.

Any ideas on this? I'd prefer to not setup an smtp server or route through some other smtp server since this is only for sending me error messages.

This doesn't require some kind of port forwarding or something, does it?

---

### Post by Bachstelze on 2010-09-14
> **ownaginatious said:**
> 
This doesn't require some kind of port forwarding or something, does it?

No, but it requires proper configuration of your MTA and a non-blacklisted IP address. If you have a dynamic IP, you are probably blacklisted.

Also why the double-backslashes? It will certainly not work like this, you need single ones. Works for me with single backslashes.

---

### Post by ownaginatious on 2010-09-14
> **Bachstelze said:**
> No, but it requires proper configuration of your MTA and a non-blacklisted IP address. If you have a dynamic IP, you are probably blacklisted.

Oh really? I do have a dynamic IP address :(

What other options do I have at this point?

---

### Post by Bachstelze on 2010-09-14
> **ownaginatious said:**
> Oh really? I do have a dynamic IP address :(

What other options do I have at this point?

You'll have to route your mail through your ISP's SMTP server. Use ssmtp to do that simply.

But try de-doubling those backslashes first.

---

### Post by ownaginatious on 2010-09-14
> **Bachstelze said:**
> You'll have to route your mail through your ISP's SMTP server. Use ssmtp do to that simply.

But try de-doubling those backslashes first.

I actually didn't use them doubled, that's how they were in the websites example for some strange reason.

Anyway, ssmtp does exactly what I want :). Setting it up to just send from a gmail account was a lot less painful than I was expecting it to be. Thanks!

Anyway, one more question. I'm not sure if you can answer this, but do you know if ssmtp can accept the whole message as a string?

For example:

```
sudo ssmtp -m "From: guy@place.com\n To: guy@place.com\n Subject: Hi there!\n\n ...."
```

I want to be able to send the message out directly from python hopefully without having to write a file or anything.

---

### Post by Bachstelze on 2010-09-14
> **ownaginatious said:**
> 
Anyway, one more question. I'm not sure if you can answer this, but do you know if ssmtp can accept the whole message as a string?

For example:

```
sudo ssmtp -m "From: guy@place.com\n To: guy@place.com\n Subject: Hi there!\n\n ...."
```

I want to be able to send the message out directly from python hopefully without having to write a file or anything.

Not sure what you want to do. The Python script does not write a file.

---

### Post by ownaginatious on 2010-09-14
Oh well I mean, I found that I can send a message doing something like this:

```
ssmtp < message.txt
```

Where the message in the text file would follow the standard format.

```

From: ...
To: ...
Subject: ...

Message

```

So wouldn't I have to write the message to a text file first in python, and then execute that script?

I have a feeling this wouldn't work:

```
os.system("ssmtp <" + variable)
```

Where the variable would hold something like "From: ...\nTo: ...\nSubject...\n\nMessage.

---

### Post by soltanis on 2010-09-14
I am pretty sure ssmtp is no longer actively maintained, but msmtp is. They work the same: they're sendmail replacements that send mail through your ISP's mailserver.

---

### Post by ownaginatious on 2010-09-15
> **soltanis said:**
> I am pretty sure ssmtp is no longer actively maintained, but msmtp is. They work the same: they're sendmail replacements that send mail through your ISP's mailserver.

Hmm interesting. I'll look into switching the program to use that instead.

Any ideas on my problem above though? Or should I just live with outputting to a file first, and then pushing that into msmtp/ssmtp?

---

### Post by Bachstelze on 2010-09-15
You can always do

```
os.system("echo file | ssmtp")
```

but you're not really supposed to call ssmtp directly, there are some MUAs like mail or mutt that you can use to send mail from a script.

---

### Post by Pyro.699 on 2010-09-15
I wrote this a while ago, you may find it useful ^^ Instead of using your ISP's smtp server, this uses googles. All you need is a gmail account and your all set :)

[php]
import os, re, threading, smtplib, traceback 
from email.MIMEMultipart import MIMEMultipart 
from email.MIMEBase import MIMEBase 
from email.MIMEText import MIMEText 
from email.Utils import formatdate 
from email import Encoders 
 
def sendEmail(subject, text, files=[], send_to="DEFAULT_SENDTO@gmail.com"): 
    try: 
        assert type(files)==list 
         
        text = "<<My Custom Header>>\n\n"+text 
         
        send_from = 'YOUR_EMAIL@gmail.com' 
         
        msg = MIMEMultipart() 
        msg['From'] = '"%s" <%s>'%("My Script", send_from) 
        msg['To'] = send_to 
        msg['Date'] = formatdate(localtime=True) 
        msg['Subject'] = subject 
         
        msg.attach( MIMEText(text) ) 
         
        for f in files: 
            part = MIMEBase('application', "octet-stream") 
            part.set_payload( open(f,"rb").read() ) 
            Encoders.encode_base64(part) 
            part.add_header('Content-Disposition', 'attachment; filename="%s"' % os.path.basename(f)) 
            msg.attach(part) 
         
        smtp = smtplib.SMTP("smtp.gmail.com", 587) 
         
        smtp.ehlo() 
        smtp.starttls() 
        smtp.ehlo() 
         
        smtp.login('YOUR_GMAIL', 'YOUR_PASSWORD') 
        smtp.sendmail(send_from, send_to, msg.as_string()) 
        smtp.close() 
         
        return True 
    except: 
        return False
[/php]Enjoy
~Cody

EDIT:
Also, it handles file uploads xD

---

### Post by e24ohm on 2010-09-15
Hey this helps with an application I was looking into building. Question - is the password sent in plain text? I don't see the ssl port being called.

---

### Post by Pyro.699 on 2010-09-15
> **e24ohm said:**
> Hey this helps with an application I was looking into building. Question - is the password sent in plain text? I don't see the ssl port being called.


Yeah it is being called in plain text xD I was too lazy to figure out how to add ssl support... i just made a quick email account, set a 25 char password (very very random) and left it at that.

smtplib does have SSL support, if you wanted to add it... go nuts xD
[http://docs.python.org/library/smtplib.html](http://docs.python.org/library/smtplib.html)

---

