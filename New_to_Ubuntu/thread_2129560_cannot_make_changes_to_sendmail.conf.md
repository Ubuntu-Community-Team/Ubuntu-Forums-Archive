---
title: "cannot make changes to sendmail.conf"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by mdc001 on 2013-03-26
Hi,

this seems a simple issue but has me stumped.
I am setting up ssmtp and it uses sendmail configuration.
I am getting email messages and would like them to stop.
I believe they are coming from a sendmail.conf setting and then promulgated through the sendmail configuration.
As I understand it, I should be able to edit sendmail.conf and then run sendmailconfig where it uses my sendmail.conf and marries it with sendmail.mc to ultimately set sendmail.cf
Unfortunately, as root, I make my change to sendmail.conf - I just comment out the CRON_MAILTO="root" but when I issue sendmailconfig, it asks if I want to use the sendmail.conf, I respond yes, but it doesn't use it. Instead, it resets it to the file I previously edited, minus the change I made.

I don't think I am understanding how sendmail.conf, sendmail.mc and sendmail.cf are all interconnected.

Any help would be greatly appreciated. 

regards
Marc

---

