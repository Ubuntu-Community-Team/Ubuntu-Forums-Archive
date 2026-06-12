---
title: "[SOLVED] Sending mail"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by gentipoo on 2008-09-24
I have Ubuntu 8.04 running. I've setup a website and it's all working except I can't get it to send mail: ie if someone sends you a message on it, it's supposed to send you an email to notify you of this... it's not sending the emails. I don't get an error on the site at all, just the emails won't go through. I have all of the DNS pointing right to the server so it can act as an email server.

I've tried sendmail, postfix and exim. I'm not sure what I'm doing wrong.

---

### Post by cmnorton on 2008-09-26
Have you installed a client?

Try installing mailutils. I had to install that, so my cron jobs could send me mail.

I am running Kubuntu 8.04.

---

### Post by gentipoo on 2008-09-29
I installed exim again and mailutils and a played with the configuration and got it working.

---

