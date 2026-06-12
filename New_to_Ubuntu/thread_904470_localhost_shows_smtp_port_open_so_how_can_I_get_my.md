---
title: "localhost shows smtp port open: so how can I get my box to send out mail?"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by t0p on 2008-08-29
In an effort to get the **fetchyahoo** command-line utility working on my computer, I installed **procmail**, **exim** and **mailx**.  Now, if I do a portscan (**nmap**) on localhost, I get a result that partially reads:

> PORT     STATE SERVICE
25/tcp   open  smtp


But if I use the command-line **mail** command to send an email to, for instance, [email]myemail@gmail.com[/email], it doesn't get sent.  And if I then check the contents of /var/mail/t0p (again, with the mail command), I find a message that reads:

> Message 3:
From MAILER-DAEMON Fri Aug 29 15:28:55 2008
Envelope-to: t0p@ubunty
Delivery-date: Fri, 29 Aug 2008 15:28:55 +0100
X-Failed-Recipients: [email]myemail@gmail.com[/email]
Auto-Submitted: auto-replied
From: Mail Delivery System <Mailer-Daemon@ubunty>
To: t0p@ubunty
Subject: Mail delivery failed: returning message to sender
Date: Fri, 29 Aug 2008 15:28:54 +0100

This message was created automatically by mail delivery software.

A message that you sent could not be delivered to one or more of its
recipients. This is a permanent error. The following address(es) failed:

  [email]myemail@gmail.com[/email]
    Mailing to remote domains not supported


Is it possible for me to configure smtp so my computer will become a mail server that *will* send to remote domains?  And if so, how?

---

### Post by brian_p on 2008-08-29
> **t0p said:**
> 

Is it possible for me to configure smtp so my computer will become a mail server that *will* send to remote domains?  And if so, how?

```
sudo dpkg-reconfigure exim4-config
```

---

### Post by Dr Small on 2008-08-29
> **brian_p said:**
> ```
sudo dpkg-reconfigure exim4-config
```
Also, once you get that setup, you'll probably find that mailing to gmail will be bothersome because of their strict rules. Your mail will most likely get bounced back, becaues you need a Fully Qualifing Domain.

---

### Post by brian_p on 2008-08-29
> **Dr Small said:**
> Also, once you get that setup, you'll probably find that mailing to gmail will be bothersome because of their strict rules. Your mail will most likely get bounced back, becaues you need a Fully Qualifing Domain.

The OP can choose to send mail directly or through his ISP's smarthost, using the latter if there are problems. As it happens I send directly to gmail from laptop.mydomain.co.uk, which does not resolve, without any difficulty.

---

