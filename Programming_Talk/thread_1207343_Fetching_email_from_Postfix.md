---
title: "Fetching email from Postfix"
date: 2009-07-08
forum: Programming Talk
---

### Post by xiaomahe on 2009-07-08
Hai, i have setup a virtual mail server with virtual domain and virtual users using this tutorial [http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04]("http://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu8.04")

I can send the email, so how can i write a php code to retrieve this email and read it in the browser? I am sort of creating a webmail application for my project. and currently i am stuck in here..

I have search around, and found out phpmailer. Does phpmailer can do the things that i want? retrieve email from a current user, and then later can receive and sending email as well??

Bear in mind, that my setup is virtual setup..

---

### Post by curvedinfinity on 2009-07-08
Hey,

You can manually read through the postfix message files, but that can get ugly, and if you delete any of them, you'll have to rebuild postfix. What you want is a POP or IMAP library. With those, you can connect to Courier just like you are currently using sendmail to send mail via SMTP.

I'm not familiar with PHP, however, so perhaps someone else can chime in about the details.

By the way, next time you want to setup email on an Ubuntu Server, you can do it in one command with:

```
sudo apt-get install dovecot-postfix
```

That will use dovecot instead of courier, but it will do all of the setup automagically. It will use your unix users instead of virtual users.

---

### Post by xiaomahe on 2009-07-08
thanks for the reply.. 

i am not sure why, but i followed like what u said, installing dovecot and postfix in 1 command.. but i end up with failure because my postfix is not running, hence my mail server is not running at all.

and did anyone knows about POP before SMTP?

is it a terms for connecting to pop3 before it gets to SMTP? therefore i can download all the messages and then replied back that message and send it back using SMTP?

---

