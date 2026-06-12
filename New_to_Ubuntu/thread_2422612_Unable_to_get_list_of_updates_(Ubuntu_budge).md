---
title: "Unable to get list of updates (Ubuntu budge)"
date: 2019-07-10
forum: New to Ubuntu
---

### Post by ubantunovice2 on 2019-07-10
Ubuntu budge running in Oracle vm in Windows 10.
I am connected to the internet.

When I try to update I get an error popup which says
[INDENT][I]"Unable to get list of updates.
E: Could not get lock /var/lib/dpkg/lock-frontend - open
(11: resource temporarily unavailable)[/I]
[/INDENT]

But it is not temporary. It keeps happening.
Why can it not get lock on .......?

Thank you.

---

### Post by ubantunovice2 on 2019-07-10
After searching for an answer I tried fsck and got a warning that because the filesystem is mounted this would damage the file system. So I aborted. I don't have a live cd. How do I solve this?
Thanks.

---

### Post by ubantunovice2 on 2019-07-11
Google is your best friend (if you know the right question to ask.....)

I forced fsck on reboot by opening the terminal and issuing
# shutdown -rF now

This rebooted Ubuntu, did a fdsk on restart and now updates are OK,

In case this helps someone else.

---

### Post by ubantunovice2 on 2019-07-11
Oops, spoke too soon.
Worked once and updated. But the next time I checked updates I again got
[I]"Unable to get list of updates.
E: Could not get lock /var/lib/dpkg/lock-frontend - open
(11: resource temporarily unavailable)

[/I]Help from some expert?

---

### Post by overdrank on 2019-07-11
Hi and after a quick search this [_link _]("https://askubuntu.com/questions/346143/e-could-not-get-lock-var-lib-dpkg-lock-open-11-resource-temporarily-unavai")may help with your issue.  Good luck

---

