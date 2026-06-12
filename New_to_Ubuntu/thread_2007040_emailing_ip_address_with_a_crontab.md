---
title: "emailing ip address with a crontab"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by djyoung4 on 2012-06-20
So i'm trying to set up a crontab that will send my external ip to my email everyday or whenever it changes.  I found this script
```
#!/bin/bash

IPFILE=~/ipaddress
CURRENT_IP=$(wget -q -O - http://www.whatismyip.com/automation/n09230945.asp)
if [ -f $IPFILE ]; then
KNOWN_IP=$(cat $IPFILE)
else
KNOWN_IP=
fi

if [ "$CURRENT_IP" != "$KNOWN_IP" ]; then
echo $CURRENT_IP > $IPFILE
mutt -s "My External IP is now "$CURRENT_IP youremail@blah.com < $IPFILE
fi
```
The problem is I can't get mutt to send the email.  i'm pretty sure I have to change some configuration file in order to get it to work but I don't know which.  I have tried to find other ways to do this as well but can't seem to find any script that will find my external ip.  Any help or suggestions are greatly appreciated

---

### Post by djyoung4 on 2012-06-20
Ok I found this in one of my old conkies
```
wget -q -O - checkip.dyndns.org
|sed -e 's/.*Current IP Address: //' -e
's/<.*$//'
```
It gives an output of my ip address.  would that be enough to put in a cron entry with a sendmail at the end to send it to myself

---

### Post by HiImTye on 2012-06-20
```
my_ip=$(wget -q -O - checkip.dyndns.org | sed 's|.*Current IP Address: \(.*[0-9]\).*|\1|')
```
then just call $my_ip to use it

---

### Post by djyoung4 on 2012-06-21
Ok I got it down to having a problem with the mail client.  Anybody have any ideas.  Any help is greatly appreciated
```
home@home-desktop:~$ mail -v djyoung4@gmail.com
Subject: hello
hello
Cc: djyoung4@gmail.com
WARNING: local host name (home-desktop) is not qualified; see cf/README: WHO AM I?
djyoung4@gmail.com... Connecting to [127.0.0.1] via relay...
220 home-desktop ESMTP Sendmail 8.14.3/8.14.3/Debian-9.1ubuntu1; Thu, 21 Jun 2012 18:06:45 -0700; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
>>> EHLO home-desktop
250-home-desktop Hello localhost [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
>>> VERB
250 2.0.0 Verbose mode
>>> MAIL From:<home@home-desktop> SIZE=45 AUTH=home@home-desktop
250 2.1.0 <home@home-desktop>... Sender ok
>>> RCPT To:<djyoung4@gmail.com>
>>> DATA
250 2.1.5 <djyoung4@gmail.com>... Recipient ok
354 Enter mail, end with "." on a line by itself
>>> .
050 <djyoung4@gmail.com>... Connecting to gmail-smtp-in-v4v6.l.google.com. via esmtp...
050 <djyoung4@gmail.com>... Connecting to alt1.gmail-smtp-in.l.google.com. via esmtp...
050 <djyoung4@gmail.com>... Connecting to alt2.gmail-smtp-in.l.google.com. via esmtp...
050 <djyoung4@gmail.com>... Connecting to alt3.gmail-smtp-in.l.google.com. via esmtp...
050 <djyoung4@gmail.com>... Connecting to alt4.gmail-smtp-in.l.google.com. via esmtp...
050 <djyoung4@gmail.com>... Deferred: Connection refused by alt4.gmail-smtp-in.l.google.com.
250 2.0.0 q5M16jIk005807 Message accepted for delivery
djyoung4@gmail.com... Sent (q5M16jIk005807 Message accepted for delivery)
Closing connection to [127.0.0.1]
>>> QUIT
221 2.0.0 home-desktop closing connection

```

---

