---
title: "Can't upgrade from 11.10 to 12.04"
date: 2012-11-21
forum: New to Ubuntu
---

### Post by han4dguy on 2012-11-21
I'm currently running Ubuntu 11.10 and have tried to upgrade to 12.04.  When I do i get the following message:
&#65279;"Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
The package 'ubuntu-desktop-boulder' is marked for removal but it is in the removal blacklist.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug update-manager' in a terminal."

As far as I know none of the causes applies, except perhaps the third (I have VirtualBox installed).  How do I resolve this??

---

### Post by LuisGMarine on 2012-11-21
Did you make sure to remove all 3rd party software sources before trying to update?

---

### Post by deadflowr on 2012-11-22
Are you running the business remix?

Here's the bug report for that:

[https://bugs.launchpad.net/ubuntu-business-remix/+bug/992013]("https://bugs.launchpad.net/ubuntu-business-remix/+bug/992013")

---

### Post by han4dguy on 2012-11-22
LuisGMarine: No.  I'm not actually sure how to tell which are 3rd party sources.

deadFlower: Yes, when I "upgraded from 8.0 I installed the business remix.  I'll check out the link you provided and see if that fixes the problem.

---

### Post by monkeybrain2012 on 2012-11-22
Just save your data and do a clean install. I see no point in trouble shooting upgrades.

---

### Post by han4dguy on 2012-11-22
Monkeybrain2012: I was hoping to avoid that, since the Ubuntu OS is one of two on a dual-boot PC.

---

### Post by monkeybrain2012 on 2012-11-22
> **han4dguy said:**
> Monkeybrain2012: I was hoping to avoid that, since the Ubuntu OS is one of two on a dual-boot PC.

I do clean install with a system that has 4 OSes. Not an issue as long as you do the install in the same partition where 11.10 is (so in the installer choose "something else" and choose the appropriate partition to be /, if you have a separate /home leave it as is and your data and settings would be saved)

---

