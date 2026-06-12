---
title: "Problem starting Ubuntu"
date: 2015-01-24
forum: New to Ubuntu
---

### Post by Brian_Pritchard on 2015-01-24
I have Ubuntu 14 installed within Windows XP.  When I try to boot through Grub I get the error 'Serious errors were found while checking the disk drive for /.'  If I type S for skip it says 'the disk drive for /tmp is not ready yet or not present'.  When I go to Advanced options I have half a dozen version available, the top one is 3.13.0.44 from today's update.  If I go to the oldest version I am able to boot the system.
I would like to correct these problems and also remove all the old versions shown in the menu.
Thanks
Brian

---

### Post by yancek on 2015-01-24
> I have Ubuntu 14 installed within Windows XP.

That would be a wubi install and it is no longer supported although people still get it to work at times.  My understanding is that a wubi install creates an entry in the windows boot menu and then goes to Grub.  Are you getting the Grub menu on boot?  Did you actually do a wubi install?

---

### Post by Brian_Pritchard on 2015-01-24
> **yancek said:**
> That would be a wubi install and it is no longer supported although people still get it to work at times.  My understanding is that a wubi install creates an entry in the windows boot menu and then goes to Grub.  Are you getting the Grub menu on boot?  Did you actually do a wubi install?
I am getting a grub menu on boot.  I am afraid I don't know what a wubi install is.
Brian

---

### Post by hakuna_matata on 2015-01-24
> **Brian_Pritchard said:**
> If I go to the oldest version I am able to boot the system.

What version number has the oldest version ? Something like 3.11 (Ubuntu 13.10) or 3.2 (Ubuntu 12.04) ?

There is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437") and are [solutions]("http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted")

edit:
 > I am afraid I don't know what a wubi install is.
Wubi install = Ubuntu within Windows files (mainly **ubuntu/disks/root.disk**) on a Windows drive (partition)

---

### Post by JeQhdMD on 2015-01-24
Yikes, . . . . I cringe eveytime I read that someone has Ubuntu installed "inside" Windows (especially  . . XP).   It's not likely an install like yours will remain stable or usable over time (like now).

**_If you want a better, permanent solution, replacing XP with Ubuntu (or a lighter cousin of it like Xubuntu) MAY be an option_** . . . . depending on what your hardware specs are, and how you use the PC (gaming, business, science/engineering, or just general use (email, media consumption, text/number processing, etc.).

By the way, a WUBI install means Ubuntu is installed inside Windows by using a Windows executable program . . . that is installed and uninstalled using the standard Windows tools (control center, etc.)   It was discontinued after intro of Windows 8.

---

### Post by Brian_Pritchard on 2015-01-24
> **hakuna_matata said:**
> What version number has the oldest version ? Something like 3.11 (Ubuntu 13.10) or 3.2 (Ubuntu 12.04) ?

There is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1317437") and are [solutions]("http://askubuntu.com/questions/453411/ubuntu-14-04-not-booting-after-error-message-tmp-could-not-be-mounted")

edit:
 
Wubi install = Ubuntu within Windows file **ubuntu/disks/root.disk** on a Windows drive

I can boot to 3.0.2-67.  I would be happy to go back to an earlier version and delete all the others if possible.

---

### Post by Brian_Pritchard on 2015-01-24
> **JeQhdMD said:**
> Yikes, . . . . I cringe eveytime I read that someone Ubuntu installed "inside" Windows (especially  . . XP).   It's not likely an install like yours will remain stable or usable over time (like now).

**_If you want a better, permanent solution, replacing XP with Ubuntu (or a lighter cousin of it like Xubuntu) MAY be an option_** . . . . depending on what your hardware specs are, and how you use the PC (gaming, business, science/engineering, or just general use (email, media consumption, text/number processing, etc.).

By the way, a WUBI install means Ubuntu is installed inside Windows by using a Windows executable program . . . that is installed and uninstalled using the standard Windows tools (control center, etc.)   It was discontinued after intro of Windows 8.

Thanks for the comments.  I need to keep Windows XP; I have another PC running Ubuntu 12.
Brian

---

### Post by hakuna_matata on 2015-01-24
> **Brian_Pritchard said:**
> I can boot to 3.0.2-67.  I would be happy to go back to an earlier version and delete all the others if possible.
Was the lastest kernel update part of an upgrade from 12.04 to 14.04? It is not a good idea to use kernel 3.0 (part of Ubuntu 11.10) with 14.04.

Does only the oldest kernel work?

---

### Post by Bucky Ball on 2015-01-24
Wubi install is not recommended. As mentioned previously on the thread, no longer supported officially here or by Canonical. If you have Ubuntu installed INSIDE Windows, and not to a partition of its own ALONGSIDE Windows, then you have a Wubi install. 

Suggest you go for a dual-boot (Windows and Ubuntu on separate partitions) as support for Wubi on these forums is scarce and what you might find here and elsewhere will be dated and possibly redundant. 

Good luck. ;)

---

