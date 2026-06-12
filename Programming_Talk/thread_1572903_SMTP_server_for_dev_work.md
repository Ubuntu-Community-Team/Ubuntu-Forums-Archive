---
title: "SMTP server for dev work"
date: 2010-09-11
forum: Programming Talk
---

### Post by ericpierce on 2010-09-11
Hi all,

I'm looking for an SMTP server for dev work under Linux.  I've searched the forums and didn't quite find the answer I was looking for.

I recently ran across a cool open source project called smtp4dev (Windows/.NET).  It is basically a dummy SMTP server 
where you can view all emails (regardless of email address domain) sent to it w/o them actually being sent on to the outside world.  It's a very cool app, and I use it at my day job (on WinXP).  However, it doesn't compile in Mono.

I wondered if there wasn't already an app like this 
for Linux.  Or maybe Sendmail or Postfix could be configured to serve this purpose (i.e., dead end SMTP server).  I have 
zero experience in either of them, so smtp4dev has a lot of appeal because of its ease of set up and use.

smtp4dev
[http://smtp4dev.codeplex.com/](http://smtp4dev.codeplex.com/)

Anyway, just looking for some ideas for doing the same under Linux.

Thanks for reading,
Eric P.

---

### Post by DanielWaterworth on 2010-09-12
try this in python:

```
import smtpd, asyncore

server = smtpd.DebuggingServer(('localhost', 8000), None)
asyncore.loop()
```

---

### Post by ericpierce on 2010-09-15
I've never used Python before.

Can you explain what that code does?

Does it possibly capture all outgoing emails and store them somewhere for inspection?

Thanks,
Eric P.

---

### Post by slavik on 2010-09-16
smtp servers STORE mail. :)

easy fake smtp server in shell (make sure netcat is installed)
```

sudo nc -l -k 25 &> /tmp/nc.log

```

---

### Post by DanielWaterworth on 2010-09-16
It should send all emails that you send to it to stdout, ie the console. If you want to log emails to a file as well, pipe the output through tee ( _[http://en.wikipedia.org/wiki/Tee_%28command%29](http://en.wikipedia.org/wiki/Tee_%28command%29)_ ). It starts the email server on port 8000, if it's more convenient to use a different one then just change the number in the source. It's also bound to localhost, which means it may not be possible to send it emails from other computers, if you'd like to send it emails from other computers then replace 'localhost' with '' in the source.

You can test that it works with this:

```
import smtplib

s = smtplib.SMTP('localhost', 8000)
s.sendmail(['test'], 'test', 'test')
```

---

### Post by ericpierce on 2010-09-17
> **DanielWaterworth said:**
> It should send all emails that you send to it to stdout, ie the console. If you want to log emails to a file as well, pipe the output through tee ( _[http://en.wikipedia.org/wiki/Tee_%28command%29](http://en.wikipedia.org/wiki/Tee_%28command%29)_ ). It starts the email server on port 8000, if it's more convenient to use a different one then just change the number in the source. It's also bound to localhost, which means it may not be possible to send it emails from other computers, if you'd like to send it emails from other computers then replace 'localhost' with '' in the source.

You can test that it works with this:

```
import smtplib

s = smtplib.SMTP('localhost', 8000)
s.sendmail(['test'], 'test', 'test')
```

Daniel,

I got the DebuggingServer working on port 25, and some Java code I wrote is able to send emails to it.  Very, very cool! =D>

The only issue I have now is some of my emails contain Japanese text, and it shows up as a jumble of unrecognizable English letters/numbers.  Is there something w/Python to show UTF-8 characters in their native character set?  I know the Japanese characters are being sent correctly because they were showing up when I was sending email to a Windows box running smtp4dev.

slavik, I didn't have any luck w/the netcat line you provided.  I'm not sure how that could work as an SMTP server since I believe a real SMTP server needs to communicate back to the client.  Anyway, it didn't work w/my code nor the Python email sender code Daniel provided.

Thanks both of you for your ideas.  I've been looking for a solution for this for months!  Just need to get the Japanese char issue sorted.

Sincerely,
Eric P.

---

### Post by endotherm on 2010-09-17
this maybe of help:
[http://evanjones.ca/python-utf8.html](http://evanjones.ca/python-utf8.html)

---

### Post by DanielWaterworth on 2010-09-17
First off, to test the system, this:

```
# encoding: utf-8
import smtplib
from email.MIMEText import MIMEText

body = u"&#12371;&#12435;&#12395;&#12385;&#12399;".encode("EUC-JP")

msg = MIMEText(body, 'plain', 'EUC-JP')

smtp = smtplib.SMTP("localhost", 25)
smtp.sendmail('test', ['test'], msg.as_string())
smtp.quit()
```should send Japanese emails to the debugging server. When I send emails using the above script, they are printed and readable (well, readable to someone who understands Japanese). I think that your problem is with the locale of the console your sending them to. Please try sending the output to a file with something like this.

```
python email_server.py > unicode_test
```If this works then try adding:

```
export LC_ALL=C
```to your .bashrc file.

Disclaimer: I'm no expert in bash or locale settings, please correct me if I'm wrong.

---

### Post by DanielWaterworth on 2010-09-19
@Eric: have you made any progress on this?

---

### Post by ericpierce on 2011-04-30
> **DanielWaterworth said:**
> @Eric: have you made any progress on this?

Hi Dan,

Just getting back to this problem.  I believe I found a workable solution.  

For starters I found a slightly more robust Python script to act as a dummy SMTP server.  It dumps the incoming email into an email file w/header, etc. in tact. 

Here's the script.
[http://www.linux-support.com/cms/component/content/article/181-dummy-smtp-server-in-python](http://www.linux-support.com/cms/component/content/article/181-dummy-smtp-server-in-python)

When emails are sent to and saved by the dummy SMTP server script, I can open them in Thunderbird and the Japanese/UTF-8 text is appearing as it should.  

I'd like to tweak the script so that the email files are created within a Thunderbird folder with the hope that the emails would just show up in that folder real time as they're created and it'd just be one click to view its content.  But I haven't been able to get that to work just yet.

Anyway, thanks for everyone's help and sorry I abandoned the thread for this long.  Hope someone else finds this info as helpful as I did!

Eric P.

---

