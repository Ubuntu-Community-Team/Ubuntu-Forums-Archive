---
title: "Mailman postfix Relay access denied;"
date: 2015-07-16
forum: New to Ubuntu
---

### Post by erik-priskin on 2015-07-16
Hello Everybody,


 My problem is that I have a postfix/dovecot (debian 7) mail system that is operated perfectly.
 Beside this system I install the mailman, based on this: [URL="https://help.ubuntu.com/community/Mailman"]https://help.ubuntu.com/community/Mailman

[/URL]

 I did everything step by step. The mail list set up and the  mail list send a welcome e-mail to the admin but if somebody write to  the mail list, the mail list do not send the mail to the other members,  and do not generate the html.
 What could be the problem? The members are enabled.
 
I only found this in the /var/log/mail.log:

 postfix/smtpd[7934]: NOQUEUE: reject: RCPT from  localhost[127.0.0.1]: 554 5.7.1 : Relay access denied; from= to=  proto=ESMTP helo=
 I have nearly tried everything so if anyone could help me I will be happy.
 
Thank you so much!

---

