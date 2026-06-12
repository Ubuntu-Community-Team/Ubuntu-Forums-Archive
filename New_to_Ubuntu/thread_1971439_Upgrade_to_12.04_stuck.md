---
title: "Upgrade to 12.04 stuck"
date: 2012-05-02
forum: New to Ubuntu
---

### Post by Phil16v on 2012-05-02
I just clicked on the Upgrade button to get 12.04 (I was using 11.04 with no real problems), and after downloading all the packages, it's stuck installing the upgrades saying "preparing to configure libc-bin". When I expand the Terminal, I get a message telling me that rsync, cups, cron, and atd need to be restarted, but I have no idea what they are or how to restart them. Give me a Z80 assembler and I'm happy - I don't know enough about what goes on under the bonnet of Unix or Windows!

---

### Post by Frogs Hair on 2012-05-02
Normally upgrades go in order, so if you were using 11.04 the upgrade would be to 11.10. You should not have to restart any process during the course of an upgrade until you are asked to restart the computer at the end of the upgrade. 

You may have to wait until someone familiar upgrades and that particular problem sees your thread.

---

### Post by DuckZoro on 2012-05-13
was having the exact same problem, except that I'm installing from 11.10.

in the end, it turns out there is a button at the bottom of the dialog, called "terminal". clicking that, I got the chance to press "enter", and the install continued.

---

### Post by luotinen on 2012-09-14
Same here. Stuck at "Preparing libc-bin".

Pressing enter at the Terminal does not solve the issue.

I'm upgrading from 10.04.

---

### Post by Epodx64 on 2012-09-14
Separate /home partitions and clean installs is really a better way to upgrade.

---

### Post by luotinen on 2012-09-16
> **Epodx64 said:**
> Separate /home partitions and clean installs is really a better way to upgrade.

Fortunately I do have separate /home partition. I'm just now doing a clean install.

They should add a warning under that update button for us mundanes:
"**It's not recommended to try to update via the Update Manager. Updating will brick your computer.**"

I'm also thinking about migrating to Windows for a more relaxed computer using experience.. :P

---

