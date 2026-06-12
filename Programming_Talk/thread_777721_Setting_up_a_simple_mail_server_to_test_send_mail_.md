---
title: "Setting up a simple mail server to test send_mail from django"
date: 2008-05-01
forum: Programming Talk
---

### Post by WinterWeaver on 2008-05-01
Can anyone recommend a simple mail server setup to test if my send_mail function in django (python) is working as it should?

I've tried to set up postfix, but I think my head is going to explode O.O

On a Live environment, someone else usually takes care of the mail servers for me, so I've never actually touched it (heck, I only started playing with Apache on Monday :P ). But I need to test if my code is working.

Much appreciated,

EDIT: I should prob also mention I'm trying to send the mail via my smtp.gmail.com

WW

---

### Post by WW on 2008-05-01
This doesn't exactly answer your question, so you can file this post wherever you feel it is appropriate. :)

I use a server for a web page and for my subversion repositories.  I have my subversion repository set up so emails are sent when a repository is checked in.  Instead of setting up postfix or some other mail server, I use a program called **svnmailer**, and to actually take care of sending email, I use the Python program [smtpclient_tls.py](http://twistedmatrix.com/projects/mail/documentation/examples/smtpclient_tls.py) that is provided as part of [Twisted](http://twistedmatrix.com/trac/wiki/TwistedProject).

This following python script uses smtpclient_tls.py to act like the sendmail command, and uses smtp.gmail.com as the smtp host.  I use this because svnmailer expects a command that behaves like the sendmail command; you won't necessarily need this.

**my_sendmailer.py**
[php]
#!/usr/bin/env python

import os
import sys

# Copy stdin to the file /tmp/svnmail
msg = sys.stdin.read()
msgfile = file("/tmp/svnmail","w")
msgfile.write(msg)
msgfile.close()

# Run smtpclient_tls.py to send the email to each recipient
from_address = sys.argv[2]
to_addresses = sys.argv[3:]
base_exec_str = "python /srv/svn/smtpclient_tls.py --smtp-host smtp.gmail.com -u GMAIL_ADDRESS_HERE@gmail.com -p 'GMAIL_PASSWORD_HERE' -m /tmp/svnmail -f "+sys.argv[2]
for to_addr in to_addresses:
    exec_str = base_exec_str + " -t " + to_addr
    os.system(exec_str)
[/php]
I have a copy of smtpclient_tls.py in /srv/svn (for no particular reason that I can recall).

You'll need to install some of the twisted packages to use this method.  I can check which ones I have installed if you are interested.

---

### Post by WinterWeaver on 2008-05-01
Thanks you I'll have a poke around twisted :)

So does svnmailer take care of the "serving" part for you? or did you need to add another mailserver?

---

### Post by WW on 2008-05-01
I didn't install a separate mail server--Twisted takes care of that.  You can probably ignore the stuff about svnmailer.  I just mentioned that as background.  The main tool for sending mail is the program smtpclient_tls.py, which uses several Twisted modules to send the email.  Twisted calls this program a "demonstration", but I found it to be just what I needed. (I was also nearing the "exploding head" stage when reading about setting up an email server.)  Here are the options to smtpclient_tls.py:
```

$ python smtpclient_tls.py --help
smtpclient_tls.py [options]
Options:
  -u, --username=      The username with which to authenticate to the SMTP
                       server.
  -p, --password=      The password with which to authenticate to the SMTP
                       server.
  -f, --from-address=  The address from which to send the message.
  -t, --to-address=    The address to which to send the message.
  -m, --message=       The filename which contains the message to send.
  -h, --smtp-host=     The host through which to send the message.
      --smtp-port=     The port number on smtp-host to which to connect.
                       [default: 25]
      --version        
      --help           Display this help and exit.

Demonstrate sending mail via SMTP while employing TLS and performing
authentication.

$ 

```
My Python program given above is just a wrapper for smtpclient_tls.py, to make it behave like the sendmail program (which is what svnmailer expects).

---

### Post by WinterWeaver on 2008-05-01
Thanks for that :)

I'm busy setting up Twisted now. It seems sooo much easier. I guess I wont know till I try ^_^

---

### Post by mssever on 2008-05-01
You don't need a mail server to send via Gmail's SMTP service. You do need an smtp library, though. I use smtplib, which is part of the Python standard library. It's pretty basic.

Here's an example from one of my projects: [php]import smtplib
from sys import argv, exit
import yaml # Library: PyYAML; Ubuntu package: python-yaml

msgfile, configfile, DEBUG = argv[1:]
DEBUG = bool(DEBUG)
f = open(configfile)
config = yaml.load(f)
f.close()
if DEBUG:
    print config
fromaddr = "%s <%s>" % (config['name'], config['email_from'])
toaddrs = config['email_to']
smtpinfo = config['smtp_server'] # contains all relevant connection info

f = open(msgfile)
msg = 'From: %s\r\nTo: %s\r\n%s' % (
    fromaddr,
    ', '.join(toaddrs),
    f.read().strip(),
)
f.close()

if DEBUG:
    print smtpinfo
counter = 0
while True:
    if DEBUG:
        print 'counter =', counter
    try:
        s = smtplib.SMTP(smtpinfo['server'], smtpinfo['port'])
    except (smtplib.SMTPException,smtplib.socket.error), e:
        if DEBUG:
            print type(e)
            print e
        counter += 1
        if counter >= 10:
            print 'Unable to establish a connection to the SMTP server. Please check your network connection.'
            raise
    else:
        break
if DEBUG:
    s.set_debuglevel(1)
s.ehlo()
if smtpinfo['authentication']:
    if smtpinfo['use_tls']: # Gmail requires this
        s.starttls()
        s.ehlo()
    s.login(smtpinfo['login_name'], smtpinfo['password'])
result = s.sendmail(config['email_from'],toaddrs,msg)
s.quit()
if result: # This means that one or more destination addresses were unsuccessful
    for i in result:
        print i
    exit(4)[/php]

---

### Post by ramalho on 2010-03-23
For testing, you can use Google's SMTP server if you hava a Gmail account. Official docs here:

[http://mail.google.com/support/bin/answer.py?hl=en&answer=13287](http://mail.google.com/support/bin/answer.py?hl=en&answer=13287)

Cheers,

Luciano Ramalho

---

### Post by tree_snake on 2010-06-13
Hello, could someone explain me, where the prob is? 

All of you say: everything I need is a smtplib, which coming with Python. Django [Doc says]("http://docs.djangoproject.com/en/dev/topics/email/#module-django.core.mail") send_mail is a some kind of a "lightweight" wrapper of smtplib library. So...it seems that I have everything I need to send emails, but it doesn't! 

What I should do ? What should I read again ? =)

---

