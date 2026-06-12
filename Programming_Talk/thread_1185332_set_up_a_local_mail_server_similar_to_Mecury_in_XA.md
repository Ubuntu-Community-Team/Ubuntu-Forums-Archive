---
title: "set up a local mail server similar to Mecury in XAMPP"
date: 2009-06-12
forum: Programming Talk
---

### Post by rvbhute on 2009-06-12
We have moved to Ubuntu development environment recently. 

Earlier, we used XAMPP in Windows. This had Mercury Mail as an email server. So we could configure an account 'rohit@localhost' and address all emails to this ID. We configured Thunderbird to read emails from this email account.

Is there a way to simulate this in Ubuntu? I do not want to set up a proper email server per se - just one that catches and stores all emails sent to 'rohit@hostname'.

Going further, whenever we had to test emails, we would manually edit the application's core email function and force the TO field to 'rohit@localhost'. Is there a way to avoid doing this by tweaking the mail server's config, to accept all incoming mails and send them to 'rohit@localhost'? 

If this is possible, then we could get the application's cron script running too - we are not enabling it right now, becuase it tends to send out a few mails on every run.

---

