---
title: "Does 11.10 automatically save Evolution email during upgrade?"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by bwallum on 2011-10-17
Many like me may have upgraded without noticing that Evolution was no longer the default mailer. As a consequence if you didn't manually back up Evolution data you have lost all earlier emails.....or not? Does the upgrade automatically backup Evolution data?

---

### Post by kolinab on 2011-10-17
It depends . . . on: (this list is not exhaustive)

1 - your upgrade method - did you do a dist-upgrade or an 'upgrade' like others do - that is - a clean install?

2 - did you leave your /home data intact, either by leaving it on it's own partition, or by doing a dist-upgrade, which would have left your data alone

or

3 - did you do a clean install and format of your drive?

Do you still have your other data? If so, you will likely find it in /home/USERNAME/.evolution

I believe if it is there you should be able to import it into Thunderbird if you choose - or if you prefer you can install evolution (I think) in 11.10.

Does that help? Post back and tell us how it goes.

K

---

### Post by ajgreeny on 2011-10-17
If you upgrade, as opposed to clean install, all your emails and configuration for evolution will still be in your home folder/partition in a hidden folder called **~/.evolution**, I think.  All you need to do is install evolution in 11.10 and you should be good to go.

All this assumes that evolution has not changed so that it no longer recognises your mail.

I don't, and never have used evolution, so can't help on that question.

---

### Post by bwallum on 2011-10-17
...well you would have thought it might be in .evolution but what I have, following a dist-upgrade is a sub folder called tasks, with a sub folder called tasks, then a sub folder called views (home/me/.evolution>tasks>tasks>views) completely empty from .evolution down. I don't recall setting that up, so assume the upgrade wiped it. All other data remains intact as far as I can tell. My home folder sits on a separate drive.

---

### Post by bwallum on 2011-11-16
Found them in the end.

E.g. My old Inbox emails were here:-

home/yourusername/.local/share/evolution/mail/local_mbox/ inbox

I guess yours might be different depending upon your folder structure. It seems you have to import each file separately, which is a pain if you have sub folders like me.

How to attached, note caveat that your file structure may differ.

---

### Post by kolinab on 2011-11-16
I should have thought of that. Some other stuff has moved from . to ./local/share -- I had trouble trouble finding my Tomboy notes one time and eventually found them in ./local/share. Tomboy is polite enough to leave you a note in /.tomboy telling you where to look.

---

### Post by WRCKID on 2011-11-16
Is there any issues with the Evolution client when sending email after the upgrade? I can retrieve my email, however I can't send email at all. Do you have to reconfigure the client to connect to the servers? Sorry, I don't mean to hijack this thread, but I figured this might be on topic with the thread. 

Thank you,

---

### Post by bwallum on 2011-11-17
Recovery of 'lost' email folders has no effect on the use of Evolution on my system. I.e. it works ok. However the email I recovered had the same attributes as my existing email. same pop server, same smtp server, same username and password. If you have different attributes could you tell us what they might be?

---

