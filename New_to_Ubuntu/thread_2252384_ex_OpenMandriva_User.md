---
title: "ex OpenMandriva User"
date: 2014-11-11
forum: New to Ubuntu
---

### Post by Francisco_Gallardo on 2014-11-11
I'm new in Linux, I became a paranoid user 'cos I got on Mandriva some message "***lnusertemp failed {temporary directories full?}. Check your installation ?  ***", and then I can't, login, so I Moved to Ubuntu. Is it possible that this occurs on Ubuntu? :confused:, Well by now Ubuntu seems more stable than openMandriva, and the other think

is I got, 

Partition 1 : 498 Gb Ext4 /dev/sda1 Type: Linux (booteable)
Partition 2 : 2 Gb Extended  /dev/sda2
Partition 5 : 2 Gb Linux swap version 2 /dev/sda5 

and then on /dev/sda 1.1 mb free space not allocated.

what is what? help me too understand.

---

### Post by oldos2er on 2014-11-12
I'm not quite sure what you're asking. Do you just have the one hard disk? Is Ubuntu the only OS currently installed?

From the information you posted it looks like you have a 498GB primary partition with Ubuntu (?) or some type of Linux installed on it, and a 2GB extended logical swap partition.

---

### Post by coffeecat on 2014-11-12
It's quite common to have 1mb unallocated space between partitions. Don't worry about it.

---

### Post by grahammechanical on 2014-11-12
Temporary directories should be variable in size. Perhaps the partition was getting full. I have never seen a message like that in the 7 years I have been using Ubuntu. I have seen warnings that memory (partition space) was getting limited. Ubuntu will install in 6 - 7 GB partition but even 10 GB can get full when certain large applications are installed.

With Ubuntu we have a recovery mode. We find it under the Advanced Options for Ubuntu sub-menu of the Grub boot menu. The recovery menu gives us the option of Clean, which will try to make free space in the partition. That should get us to a working desktop where we can take other steps to clean house.

Regards.

---

### Post by Francisco_Gallardo on 2014-11-13
Thank you all!!! I'll let you know if something happends, this sunday is the date to test if ubuntu passes my paranoid!!

---

