---
title: "Sendmail problems"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by infosys on 2008-05-09
Okay, I'm running out of things to try through stumbling around, so I've decided to ask you all for some real help. The basic problem is that my Ubuntu server box will not send mail. I'm recreating a helpdesk that is alredy in production, but it's set up using Slackware and I'm using Ubuntu. The Slackware one will send e-mail, but for the life of me I can't get the Ubuntu one to send e-mail. 

Originaly I was getting errors saying "unable to qualify my own domain name" but I was able to fix that in the hosts file.

Now I got one single error saying "perldesk sendmail[6244]: NOQUEUE: SYSERR(infosys): can not chdir(/var/spool/mqueue/) Permission denied" So, I changed the owner of the /var/spool/mqueue/ folder to root, and I've not getting any more errors, but no e-mails have been showing up in my inbox yet. Maybe changing owners was the wrong thing to do, I'm not sure. Don't really know what else to try at this point.

Any help would be greatly appreciated, thank you.

---

### Post by Darkade on 2008-05-09
I experienced same problem with sendmail but now I'm using postfix, it's really easy to setup and reliable. here's a how to, that you'll probably find useful if you go for postfix
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by infosys on 2008-05-09
From my understanding, the third party helpdesk softare that I'm running, it requires sendmail; So I don't really have a choice in the matter. This could be wrong though. Is postfix 100% interchangable with sendmail? 

Maybe some of my termanology is incorrect here too. I'm not acctualy trying to set up a full blown e-mail server. The helpdesk software that I'm using sends out an e-mail when a user submits a new request. All I'm trying to do is get get it too work, and it seems to be dependent on sendmail specificaly.

---

