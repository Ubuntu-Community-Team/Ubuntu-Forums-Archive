---
title: "Is it possible to get my mail server to auto bcc when I send emails from my phone?"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by Robert_Boutin on 2014-04-18
Hi everyone, I am hoping somebody has an answer for this.

So I built my own e-mail server using the instructions from HowtoForge's "The Perfect Server - Ubuntu 12.10 (Apache2, BIND, Dovecot, ISPConfig 3) and it is working great, seems to be very robust.  It includes Postfix and I have Squirrelmail installed on the server so I always have a way to send/receive e-mail

I do a LOT of my work through my BlackBerry Z10 (please no wisecracks about my phone, I love MOST everything about it).  I have two major gripes about BB10 OS.  First, it now automatically deletes from my phone emails that are older than two weeks.  But it also deletes them from the server.  Fortunately everything gets saved locally on my laptop via Thunderbird, but it means when I'm traveling with only my phone, I don't have access to email older than two weeks.  My second gripe is that if I don't manually cc myself, any e-mail I send from my phone is lost forever after two weeks.

So my question is this...  If I send mail from my phone, is there any way my server can add the auto bcc for me for specific email accounts (I don't want copies of my family's emails)?

Any ideas?

Thanks,

Bob

---

### Post by TechAndNews on 2014-04-18
Hi Bob: You need to setup IMAP Email, which saves Email on the Mail Server. You can also configure the Automatic-CarbonCopy in Mozilla Thunderbird Desktop Email Client; however, it may be that Emails will only Automatically CC when sent from that Desktop Client. Apple iOS Devices have an "Always BCC Myself" feature that Users can Turn-On or Off (in Settings, General, Mail). I haven't used BlackBerry since 2006, so check your Email Account Settings on the BB z10. IMAP Email is the Best, because Email is Synced Across All Your Devices! Also, "RoundCube" is an alternative to SquirrelMail. [http://RoundCube.net](http://RoundCube.net) Hope This Helps!

---

### Post by Robert_Boutin on 2014-04-18
Thanks.  So if I send an email from my phone through an IMAP server, a copy is stored in a "sent folder"?  And that is not the case with POP?

And no such luck on auto bcc.  Used to be, but the brilliant ex-leadership at BlackBerry for some reason didn't include it in BB10.

---

