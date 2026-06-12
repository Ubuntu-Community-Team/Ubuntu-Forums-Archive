---
title: "Sending simple mail through terminal"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Katulobotomia on 2008-11-22
This is my first post, hi. :)

I've been looking to get an email sent through the terminal only using various programs/scripts like 'mutt','mailx' etc, and have tried to follow numerous instructions on how to set up stuff like 'postfix' or 'sendmail' but no avail.

I always seem to get some error message or if there is none, the mail simply won't get delivered.

The last try I had with mailx, and this was the result:

katulobotomia@Katul:~$ mail_script
mail: /opt/zimbra/postfix/sbin/sendmail: No such file or directory
Can't send mail: sendmail process failed with error code 1
katulobotomia@Katul:~$



Even setting up postfix (and I think I set it up correctly, but not really sure) does nothing to solve this. The script goes as follows:

#!/bin/bash
# Scriipt to send simple email
#email subject
SUBJECT="Test"
#email to ?
EMAIL="lobotomiakatu@hotmail.com"
# Email text/message
EMAILMESSAGE="/home/katulobotomia/test_mailmessage.txt"
echo "This is email message"> $EMAILMESSAGE
echo "this is email test" >>$EMAILMESSAGE
# send an email using /bin/mail
mail -s "$SUBJECT" "$EMAIL" < $EMAILMESSAGE


I have no idea what I am doing wrong here?

---

### Post by Xiong Chiamiov on 2008-11-27
I don't believe you need anything like postfix unless you're actually *sending* the mail yourself, rather than using a mail server, but I'm not very knowledgable about that.

[This]("http://mutt.blackfish.org.uk/") site looks fairly helpful for mutt, and has some useful links in it.

---

### Post by andrew.46 on 2008-11-27
Hi,

There is a guide for mutt on these forums. OK I will admit that I wrote it :-). Although it deals with Gmail mainly it could be easily modified for other servers:

[http://ubuntuforums.org/showthread.php?t=565326](http://ubuntuforums.org/showthread.php?t=565326)

  Andrew

---

### Post by hyper_ch on 2008-11-27
I see you have installed zimbra on there... if I'm not mistaken that will setup a whole bunch of demons and hence it might interfere with what you're trying to achieve.

---

### Post by Sianegad on 2010-01-02
Hi its been a long time since you posted this, i am trying to use the mail command in terminal and terminal just like you.  And just like you i ended installing all kind of mta without success.  Did you get it to work since last year?

---

