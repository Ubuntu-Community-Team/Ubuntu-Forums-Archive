---
title: "python smtplib problems"
date: 2009-03-06
forum: Programming Talk
---

### Post by blairm on 2009-03-06
Hi,

Playing with Python and trying - with no luck so far - to get smtplib working. Have tried a dozen bits of code from round the place and had no luck with any of them. 
The error messages have varied with each one I tried.
I'm able to ping the mailserver, but telnet gives me the following:

```
blairm@orpheus:~/Documents$ telnet send.xtra.co.nz 465
Trying 124.108.96.68...
Connected to smtp1.tnz.mail.vip.aue.yahoo.com.
Escape character is '^]'.
Connection closed by foreign host.
blairm@orpheus:~/Documents$ 
```

Could the problem be at the mailserver end? Or have I just found some really bad code examples?

Blair

---

### Post by ghostdog74 on 2009-03-06
is port 465 the smtp port used at the other side? its not conventional smtp port, therefore i suspect some sort of firewall blockage. i could be wrong.

---

### Post by blairm on 2009-03-06
Hi,


I'd read that 587 was common port, but got the following details from my ISP's website in the help section on setting up email clients:


Incoming Mail (POP3) Server: pop3.xtra.co.nz (Use SSL, port: 995)
Outgoing Mail (SMTP) Server: send.xtra.co.nz (Use SSL, port: 465, use authentication)
Server requires a secure connection (SSL is required)
Outgoing mail server requires authentication
Account Name/Login Name: Your Xtra username (your email address without the "@xtra.co.nz")
Email Address: Your Xtra email address (eg.*username@xtra.co.nz )
Password: Your Xtra password

The fact I've tried more than a dozen bits of code makes me think I'm either doing something really stupid (entirely possible, as I only started playing with python a few days ago) or my isp is making my life miserable!

Blair

---

### Post by Greyed on 2009-03-07
Well, first off show us what you have tried...  Remember to use code blocks or, even better, php blocks.

---

### Post by blairm on 2009-03-07
Okay, have come to the conclusion the problem lies with my ISP's mail server. Won't show all my attempts or the post will be of War and Peace proportions, but here are three most recent:

```
import smtplib
#adapted from http://bytes.com/topic/python/answers/774774-how-send-mails-using-python-smtp, inserted my name/password/isp's server
smtpserver = 'send.xtra.co.nz:465'
AUTHREQUIRED = 1 # if you need to use SMTP AUTH set to 1
smtpuser = 'my.username'  # for SMTP AUTH, set SMTP username here
smtppass = 'mypassword'  # for SMTP AUTH, set SMTP password here

RECIPIENTS = ['my.address@xtra.co.nz']
SENDER = 'my.address@xtra.co.nz'
mssg = "The Message"
  
session = smtplib.SMTP(smtpserver)
if AUTHREQUIRED:
    session.login(smtpuser, smtppass)
smtpresult = session.sendmail(SENDER, RECIPIENTS, mssg)


if smtpresult:
    errstr = ""
    for recip in smtpresult.keys():
        errstr = """Could not deliver mail to: %s
        Server said: %s %s %s""" % (recip, smtpresult[recip][0], smtpresult[recip][1], errstr)
    raise smtplib.SMTPException, errstr

```

The debugged program raised the exception unhandled error
"(104, 'Connection reset by peer')"
File: /usr/lib/python2.5/socket.py, Line: 381
Line 381 says: data = self._sock.recv(self._rbufsize)

```
import smtplib

smtpserver = 'send.xtra.co.nz'
AUTHREQUIRED = 1
smtpuser = 'my.username'
smtppass = 'mypassword'

RECIPIENTS = ['my.address@xtra.co.nz']
SENDER = 'my.address@xtra.co.nz'
mssg = "this is a test message"

session = smtplib.SMTP(smtpserver)
if AUTHREQUIRED:
    session.login(smtpuser, smtppass)
smtpresult = session.sendmail(SENDER, RECIPIENTS, mssg)

if smtpresult:
    errstr = ""
    for recip in smtpresult.keys():
        errstr = """Could not deliver mail to: %s

Server said: %s
%s

%s""" % (recip, smtpresult[recip][0], smtpresult[recip][1], errstr)
    raise smtplib.SMTPException, errstr

```




The debugged program raised the exception unhandled error
"(110, 'Connection timed out')"

File: /usr/lib/python2.5/smtplib.py, Line: 310
Line 310 says: raise socket.error, msg


But the following code using Google's mail server works:

```
import smtplib

# from http://stackoverflow.com/questions/399129/failing-to-send-email-with-the-python-example
FROMADDR = "my.address@gmail.com"
LOGIN    = FROMADDR
PASSWORD = "mypassword"
TOADDRS  = ["my.address@xtra.co.nz"]
SUBJECT  = "Test"

msg = ("From: %s\r\nTo: %s\r\nSubject: %s\r\n\r\n"
       % (FROMADDR, ", ".join(TOADDRS), SUBJECT) )
msg += "some text\r\n"

server = smtplib.SMTP('smtp.gmail.com', 587)
server.set_debuglevel(1)
server.ehlo()
server.starttls()
server.login(LOGIN, PASSWORD)
server.sendmail(FROMADDR, TOADDRS, msg)
server.quit()

```

When I altered it to use my ISP's mail server got the following (familiar looking) error:
The debugged program raised the exception unhandled error
"(104, 'Connection reset by peer')"
File: /usr/lib/python2.5/socket.py, Line: 381
Line 381 says: data = self._sock.recv(self._rbufsize)

Thanks for your help - no doubt I'll be calling on it again in the next day or so!

Blair

---

### Post by Greyed on 2009-03-07
Hm, that does look to be the case if you can get it to work with Google's SMTP implementation.  I was worried about the encryption layer but you have starttls in there, so that ruled out my primary suspicion.  BTW, is that your real uname/password?  If so, might want to edit that portion out.  ;)

---

### Post by blairm on 2009-03-07
Thanks Greyed,

Yes, they were my details... thanks for the heads up on that. Have removed them now.
Now I know I can use the elements I need for my little script I just have to glue them all together - why do I have a feeling that won't be a trivial exercise?
Good thing I'm enjoying myself.:)

Blair

---

### Post by the_unforgiven on 2009-03-07
Check how the SMTP object is initialized -
from your code: ```
smtpserver = 'send.xtra.co.nz:465'
[...]
session = smtplib.SMTP(smtpserver)

```
which fails. Versus, the gmail example: ```
server = smtplib.SMTP('smtp.gmail.com', 587)

```
Check this documentation of smtplib:
[http://docs.python.org/library/smtplib.html](http://docs.python.org/library/smtplib.html)

Looks like 465 is the default SMTP-over-SSL port and there is already a class to handle that - smtplib.SMTP_SSL() :)
However, that looks like it's been added sometime after 2.5.2 - which is the version I'm using and it doesn't have SMTP_SSL().
So, if you want your code to be portable, just use the smtplib.SMTP(host, port) syntax and then call starttls().

---

### Post by blairm on 2009-03-07
Thanks Unforgiven,

I did read something about smtplib.SMTP_SSL() but like you I'm using 2.5.2

Thanks to some annoying policies our IT department has the script I'm writing will only be run on my computer anyway.
The script will (hopefully!)  check rss feeds every 30 min and send an email to a work address with any new stories.

Out IT dept has blocked the rss functions in thunderbird and firefox - and given we run a news website rss feeds with notification of new stories are pretty much a necessity.

Plan to run this from my home computer as it appears to be the only solution.
Besides, been considering python for a while now and this seemed a good project to keep me motivated while learning.

Blair

---

### Post by lavinog on 2009-05-06
Any luck with this. I am having the same issues
the smtp server I am trying to connect to is hosted by yahoo.
The setup instructions for a email client say:
> 
User Name:
[email]username@mydomain.biz[/email]

Outgoing Mail (SMTP)
smtp.bizmail.yahoo.com
Use SSL, port: 465; authentication required

and there are various notes for outlook users to:
> Note: Please make sure that "Log on using Secure Password Authentication" is not checked.

```
import smtplib

SERVER = 'smtp.bizmail.yahoo.com'
PORT=465
FROM = "test@mydomain.biz"
TO = ["me@mydomain.biz"]
message='testing'
smtpuser='test@mydomain.biz'
smtppass='passwurd'

print 'opening session'
session = smtplib.SMTP(SERVER,PORT)

session.set_debuglevel(1)
session.starttls()

print 'checking login'
session.login(smtpuser,smtppass)
session.sendmail(FROM, TO, message)

session.quit()

```
this results in a connection reset by per error:
```
opening session
Traceback (most recent call last):
  File "test2.py", line 12, in <module>
    session = smtplib.SMTP(SERVER,PORT)
  File "/usr/lib/python2.6/smtplib.py", line 239, in __init__
    (code, msg) = self.connect(host, port)
  File "/usr/lib/python2.6/smtplib.py", line 296, in connect
    (code, msg) = self.getreply()
  File "/usr/lib/python2.6/smtplib.py", line 337, in getreply
    line = self.file.readline()
  File "/usr/lib/python2.6/socket.py", line 404, in readline
    data = self._sock.recv(self._rbufsize)
socket.error: [Errno 104] Connection reset by peer

```

---

### Post by lavinog on 2009-05-06
if i change the script to:
```

print 'opening session'
session = smtplib.SMTP_SSL(SERVER,PORT)

session.set_debuglevel(1)

print 'checking login'
session.login(smtpuser,smtppass)
session.sendmail(FROM, TO, message)

session.quit()

```
i get:
```

checking login
send: 'ehlo myserver.###########.####.#######.net\r\n'
Traceback (most recent call last):
  File "test2.py", line 18, in <module>
    session.login(smtpuser,smtppass)
  File "/usr/lib/python2.6/smtplib.py", line 549, in login
    self.ehlo_or_helo_if_needed()
  File "/usr/lib/python2.6/smtplib.py", line 509, in ehlo_or_helo_if_needed
    if not (200 <= self.ehlo()[0] <= 299):
  File "/usr/lib/python2.6/smtplib.py", line 382, in ehlo
    self.putcmd(self.ehlo_msg, name or self.local_hostname)
  File "/usr/lib/python2.6/smtplib.py", line 318, in putcmd
    self.send(str)
  File "/usr/lib/python2.6/smtplib.py", line 310, in send
    raise SMTPServerDisconnected('please run connect() first')
smtplib.SMTPServerDisconnected: please run connect() first

```

---

### Post by lavinog on 2009-05-06
ok i got it to work:
```

session = smtplib.SMTP(SERVER)
session.set_debuglevel(1)
session.starttls
session.login(smtpuser,smtppass)

```
I had to remove the port=465 and use the default port for standard connections.

---

