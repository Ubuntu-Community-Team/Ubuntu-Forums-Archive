---
title: "evolution going crazy"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by matteoettam on 2008-05-20
Hallo all..
I'm having a very annoying problem with evolution
I have upgraded to Hardy Heron with no problem as soon as it came out and everything ran smoothly until today...
I launched Evolution and it started doing something about "storing"..
then now I have at least half of my inbox messages where the sender does not match the text at all!!!
I have quite some data as e-mails and now I can't find them anymore since the search function is totally useless..
new incoming e-mails are fine though..

HELP!!!

---

### Post by Ux64 on 2008-05-22
Confirmed, I also have similar problem with it.

I just wrote about it to another thread.

---

### Post by sayakb on 2008-05-22
As an alternative, try Thunderbird.

---

### Post by Ux64 on 2008-05-26
> **LinuxIsInnovation said:**
> As an alternative, try Thunderbird.

I would use TB, but I tried 2.0 version. It's as slow sending email as 1.3 version was. I hate it. I handle quite a many emails daily (about 200) and I can't stand programs which are so slow when sending mail.

And as far as I know, there is no option to fix that.

---

### Post by gerard67 on 2008-05-27
Hello,
Same issue for me .. The subject summary and sender name displayed in the message list does not match the mail body anymore. My old mails are completely unusable. Many thanks Evolution !

Mathieu

---

### Post by kpappas on 2008-05-29
I am having the same problem with 4 machines and the users are going nuts. Any fixes??? anyone????

---

### Post by Golem XIV on 2008-05-29
Looks like you all ran into [this bug]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/27014") that's been around for some time.

The bug report has some workarounds, you may want to try them.

---

### Post by kpappas on 2008-05-29
It worked!!!
1. Closed Evolution.
2. Deleted ~/.evolution/mail/local/Inbox.ev-summary
3. Opened Evolution again and problem solved!

Thank you Golem XIV!!!!:guitar:

---

### Post by Ux64 on 2008-05-29
I just downloaded Evolution updates. Let's see if we FINALLY get rid of this problem. Which has been hounting me for more than 9 months. ;(

---

### Post by Ux64 on 2008-06-08
Unfortunately it seems that latest version of Evolution still got issue. ;(

---

### Post by stchman on 2008-06-08
> **matteoettam said:**
> Hallo all..
I'm having a very annoying problem with evolution
I have upgraded to Hardy Heron with no problem as soon as it came out and everything ran smoothly until today...
I launched Evolution and it started doing something about "storing"..
then now I have at least half of my inbox messages where the sender does not match the text at all!!!
I have quite some data as e-mails and now I can't find them anymore since the search function is totally useless..
new incoming e-mails are fine though..

HELP!!!
Don't do the upgrade route and do a fresh install.

---

