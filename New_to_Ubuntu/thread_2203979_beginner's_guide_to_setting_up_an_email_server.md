---
title: "beginner's guide to setting up an email server"
date: 2014-02-06
forum: New to Ubuntu
---

### Post by shad2 on 2014-02-06
how can i set up an email server to send emails on my own pc (not outside),but to myself.
i.e be able to send to myself and recieve them on my pc alone ubuntu 10.04
using Postfix,Dovecott,mysql,ssl/tls,spamassasin,clamv,amavis

---

### Post by Gaweph on 2014-02-06
> **shad2 said:**
> 
using Postfix,Dovecott,mysql,ssl/tls,spamassasin,clamv,amavis


------------
Mail server
------------
Does this mean you already have these installed? (i.e. already have the mail server ready to go?)

If you havent set these up ye,t then I can recommend iRedMail (easy to setup and use mail server)
[http://www.iredmail.org/install_iredmail_on_ubuntu.html](http://www.iredmail.org/install_iredmail_on_ubuntu.html)

------------
Send to yourself
------------
As far as sending yourself emails.  THis can be done quite simply by adding a domain into your hosts file.

For example, if you add:

127.0.0.1 shad2.local

or (if the mail server is another machine on your network)

192.168.0.123 shed2.local

Then if you send an email to [email]test@shad2.local[/email], it will resolve this name to the mail server and send it there.

-------------

Post back here if you need any clarification.

---

### Post by shad2 on 2014-02-08
I already have postfix,mysql,installed the rest are not yet installed.how can i go about the task.

---

