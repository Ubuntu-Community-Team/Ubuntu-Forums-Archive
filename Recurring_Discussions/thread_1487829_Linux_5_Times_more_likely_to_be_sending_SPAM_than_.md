---
title: "Linux 5 Times more likely to be sending SPAM than Windows...."
date: 2010-05-19
forum: Recurring Discussions
---

### Post by neu5eeCh on 2010-05-19
Interesting article at PCWorld:

[http://www.pcworld.com/businesscenter/article/195890/symantec_study_mischaracterizes_linux_spam.html](http://www.pcworld.com/businesscenter/article/195890/symantec_study_mischaracterizes_linux_spam.html)

---

### Post by Linuxforall on 2010-05-19
WOW! Symantec's assessment of Linux.

---

### Post by Roasted on 2010-05-19
It's from Symantec. Clearly it's legit.

---

### Post by Grenage on 2010-05-19
Valid points, but an awful lot of talk about nothing.

---

### Post by Chronon on 2010-05-19
I agree.  Much ado about nothing.

---

### Post by Viva on 2010-05-19
Could it be because most spam is from automated scripts that run on linux servers?

---

### Post by Lightstar on 2010-05-19
If I was owner of a spam company.  I'd surely use Linux.  It's much faster and reliable than windows machines.  I would be certain that all my spam gets delivered very quickly without problems.

---

### Post by juancarlospaco on 2010-05-19
*Because of Windows Mail Servers just Freeze...*

---

### Post by mickie.kext on 2010-05-19
Symantec is a company that cashes in on Windows security flaws. They are scared that Linux might render them obsolete, hence the FUD.

---

### Post by cariboo on 2010-05-19
It wouldn't surprise me at all, an email server is pretty easy to install. There are even apps that install a mail server when you really don't need one (rkhunter for one). if you don't know what you are doing it could be setup so that it is easily compromised.

I'm quite sure there are many systems out there with an email server running, where the owner isn't even aware of it.

---

### Post by lancest on 2010-05-19
Poor administration. 
They feel they can drop in Linux boxes without proper security configs. 
"If you are a Linux administrator, make sure your systems do not have open mail relays available to be exploited by botnets to distribute spam e-mail messages." 
BTW The article states that it's likely the Linux mail servers are not directly infected.

---

### Post by jerenept on 2010-05-19
This is probably bcuz Symantec wants the poor fools using Windows Server to drop money on their product rather than pay $FREE.99 for Linux.

---

### Post by lisati on 2010-05-19
There are a couple of scenarios I can think of when a Linux-based email server could be mistaken for a system sending spam. The first is from misdirected autoresponses (often from an autoresponder blindly sending out its messages to forged "from" or "reply-to" addresses), and the second from misdirected bounces (usually from a similar problem caused by accepting an email before deciding to bounce it). These problems, along with a couple of others, are described here: [http://www.spamcop.net/fom-serve/cache/329.html](http://www.spamcop.net/fom-serve/cache/329.html)

---

### Post by the yawner on 2010-05-19
> 
As it turns out, Symantec also provides a more detailed investigation into the Linux spam issue. Symantec elaborates to say it "found that in most cases it came from a machine running an open source mail transfer agent (MTA) such as Postfix or SendMail, that had been left open. This suggests that one reason there is so much spam from Linux could be that many companies that have implemented their own mail servers, and are using open source software to keep down costs, have not realized that leaving port 25 open to the internet also leaves them open to abuse."


Wait. Leaving port 25 open is equal to setting mail server as an open relay? I guess I better block port 25 on my firewall.

---

### Post by dmizer on 2010-05-19
Also from the article:
> So--the **true source** of the spam messages is still most likely a compromised Windows PC--probably part of a massive botnet.

Linux represents a huge percentage of mail servers, so the fact that spam is being sent through them should not be much of a surprise. Also, even if you have port 25 blocked on your firewall an infected Windows machine located on your LAN can still exploit a local Linux SMTP server. This is why many ISPs block port 25 completely.

---

