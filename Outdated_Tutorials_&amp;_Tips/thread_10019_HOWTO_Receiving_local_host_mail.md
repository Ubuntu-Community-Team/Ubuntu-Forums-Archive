---
title: "HOWTO: Receiving local host mail"
date: 2005-01-04
forum: Outdated Tutorials &amp; Tips
---

### Post by wallijonn on 2005-01-04
Start Evolution
Tools -> Settings -> Add
Name: username@localhost
Fullname: username
Server type: Local Delivery
Path: /var/mail/username
Sending Mail: sendmail

Replace your login user name in the fields above where it says "username".

Now you'll be able to get System Messages which could notify you of system problems.

---

### Post by HungSquirrel on 2005-01-05
It is also useful to [forward root mail to your local mail](http://www.ubuntuforums.org/showthread.php?t=7321).  :)

---

### Post by wallijonn on 2005-01-05
HS,

Your thread gave me the idea (that and I was having Evolution SMTP send mail errors, along with Postfix errors).  My problem was where you said, "First, you need a mailbox, preferably with all of root's old mail already in it." Unfortunately root didn't have any mail nor a mailbox that I could work with. 

If I try to send a mail to root@localhost, Postfix will send me a MAIL-DAEMON "Undelivered Mail Returned to Sender" to my real email account. If I send an email to root@localhost.localdomain it goes into the ether, lost forever (because I am not running Postfix). 

I guess if I enabled the root account (gave it its own password, etc.) it may create a root email postoffice box, but it's nothing I wish to try at the moment as I am already used to suid.

---

### Post by Yukonjack on 2005-01-19
You can also just open the terminal type mutt and bingo, follow the instructions, you can read the mail in /var/mail and also copy, delete, move it to you home folder ect.... Ubuntu installs a few mail transports and mail readers when you install Ubuntu.

---

### Post by barbarian on 2005-01-19
Thanx, it works great!!!

---

### Post by Cuber on 2005-05-11
Does this also works for Thunderbird?

---

### Post by wilhelm on 2005-05-11
it should work for thunderbird if it works in evolution

---

### Post by cordoval on 2010-11-09
I am using apache2 and suphp and have my local site in php
when sending the site is configured to send to my gmail email
can I just keep that and since the php sends to gmail email can I setup the mailer so that it sends mail to my gmail?

how do I set that up?

---

