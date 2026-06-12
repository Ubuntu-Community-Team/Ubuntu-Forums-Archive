---
title: "mail() function"
date: 2009-12-01
forum: Programming Talk
---

### Post by X.Cyclop on 2009-12-01
i'm trying to send an e-mail from my computer (localhost, i installed XAMPP) but it's not working.
I edited already php.ini but everything is the same.

i think smtp is the problem but i don't know which or what to install/do. could somebody help me plz??

[i'm learning PHP by the way, so i don't know a lot.:D]

---

### Post by cdenley on 2009-12-01
PHP uses the sendmail command to send e-mail. Do you have an MTA installed?
```

sudo apt-get install postfix

```
If it is a configuration problem, I can't help you unless you start using the ubuntu LAMP server. I never used XAMPP before.

---

### Post by bsharp on 2009-12-01
My ISP blocks all mail servers so your problem may be there. It took me *forever* to figure out what was going on when I was doing the same thing. Try sending to a local address and see what happens

---

### Post by X.Cyclop on 2010-09-06
[Well, i'm sorry for commenthing on this thread (i don't think i should open a new one).]

I installed **sendmail**, edited php.ini (sendmail_path = /usr/sbin/sendmail -i -t) and my script works fine.
I have the same problem again, just don't receive any e-mails. 



Ubuntu 10.4, PHP 5.3.2., Apache 2.2.14, mailto Yahoo! (i tried also Hotmail and Gmail) from localhost.

LOG /var/log/mail.log
> Sep  6 14:10:22 leo-laptop sendmail[5066]: o86BAMBS005066: to=XXXXXX@yahoo.com, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30310, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (o86BAMbi005068 Message accepted for delivery)
Sep  6 14:10:31 leo-laptop sm-mta[5070]: o86BAMbi005068: to=<XXXXXXX@yahoo.com>, ctladdr=<www-data@leo-laptop.home> (33/33), delay=00:00:09, xdelay=00:00:09, mailer=esmtp, pri=120535, relay=e.mx.mail.yahoo.com. [67.195.168.230], dsn=5.0.0, stat=Service unavailable
Sep  6 14:10:31 leo-laptop sm-mta[5070]: o86BAMbi005068: o86BAVbi005070: DSN: Service unavailable


---

