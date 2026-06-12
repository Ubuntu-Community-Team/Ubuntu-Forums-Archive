---
title: "warning: SASL: Connect to private/auth failed: No such file or directory"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by anichin on 2013-06-22
I am trying to set up a mail server following this guide:

[https://help.ubuntu.com/13.04/serverguide/postfix.html](https://help.ubuntu.com/13.04/serverguide/postfix.html)

I have Postfix 2.10 and Dovecot 2.2.3. I got this in the mail.err log file:

```
Jun 22 10:22:25 ubuntu01 postfix/smtpd[9286]: fatal: no SASL authentication mechanisms
```

and this in the mail.log:

```
Jun 22 10:26:47 ubuntu01 postfix/smtpd[9419]: warning: SASL: Connect to private/auth failed: No such file or directory
Jun 22 10:26:47 ubuntu01 postfix/smtpd[9419]: fatal: no SASL authentication mechanisms

```

I checked and I am missing /var/spool/postfix/private/auth socket - it is just not there.

I am attaching some of the configuration files I changed with reverting back the domain specific settings to their general values. 

Please, can anyone help me and point me in the right direction. I suspect the documentation refers to an older version of postfix/dovecot with different configuration files.

Thank you!

Configuration files: 


[ATTACH]244032[/ATTACH]

---

### Post by priyans on 2013-06-25
Please paste the output for postconf -a and postconf -A . Also, check if dovecot was installed correctly and working well, for that, create a user and try to authenticate using pop or imap.

---

