---
title: "linux dual boot with windows installation"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by persia sand on 2008-08-25
i am about to wipe my windows and restart a fresh os of windows cuz of some blackout that corrupted tons of my system files and i would like at the same time having linux as my operating system.

now i havent rebooted windows yet, and that means i have the oppertunity to do the partitions directly from the computer and not from the live cd.

what do i do? and what partitions should i make? if i partition from linux live cd would it wipe my new windows? 

thanks

Andrew , on the way linux user

---

### Post by skymera on 2008-08-25
You can create partitions in the Ubuntu LiveCD.

Have Windows as the first partition and Ubuntu as the second.

Install Windows first then install Ubuntu after on the second partition using the EXT3 filesystem.

---

### Post by persia sand on 2008-08-25
shouldnt i make a partition named swap or root? ive seen guides but i am not totally sure

---

### Post by indytim on 2008-08-25
Just do a small Windows partition (what you need plus some moderate amount of growth).  Leave the rest un-assigned for the moment.  Install Windows and get it happy.

After you've done that, get a copy of GParted and manually partition the balance of your hard drive to support Linux etc.  (recommend you create an extended partition first and then put the ext3 and swap into the extended).

Boot to the Linux LiveCD and install.  When you come to the point of the partitions, select the "manual partition" option and utilize the partitions you already created.

IndyTim

---

### Post by forger on 2008-08-25
Ok here's the simple plan, since you haven't installed linux yet
1) Boot using the windows cd, enter the installation mode
Delete the partition(s) and create partitions again - you will be asked how much space your new partitions will take, **use that** to limit your partitions size.
Then do a complete/full format.
**Note:** Keep in mind that you need at least 8GB-10GB (8192MB-10240MB) for a working Ubuntu operating system.

2) Boot using the ubuntu live CD, use the installer to install the Ubuntu operating system :)
Ubuntu's bootloader should successfully pick up your installed Windows, so you'll have both installed now
More info about installing ubuntu:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by vikramaditya on 2008-08-25
I'd go ahead and just install windows first.  Be sure your internet connection is turned off while doing so, then disable MS Messenger as soon as the desktop is up & running.  Otherwise, you'll get a flood of bogus "Your PC is at risk!" popups.  Once you've got all your windows security updates installed, then go ahead and use your ubuntu live cd.  You can set all your partitions during installation.

---

### Post by persia sand on 2008-08-25
thanks everyone

---

