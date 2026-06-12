---
title: "Booting 2 Ubuntus (64 + 32)"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Zorgoth on 2008-09-04
Hi!

I just got a new computer and dual-booted Windows Vista with 64-bit Ubuntu.  I was thinking of installing 32-bit Ubuntu as well.  I have the following partitions:

Ext3 for main Ubuntu installation
Ext3 for /home
Swap
FAT32 for different OS's to share
NTFS for Windows Vista

I was going to take out space from the FAT32 partition for the main partition of 32-bit Ubuntu.  I was wondering whether I can share /home and swap between the two Ubuntus.

Thanks!

---

### Post by wolfen69 on 2008-09-04
i know swap can be shared between any number os distros, not sure about /home. i would tend to think that you can't.

---

### Post by bodhi.zazen on 2008-09-04
> **Zorgoth said:**
> Hi!

I just got a new computer and dual-booted Windows Vista with 64-bit Ubuntu.  I was thinking of installing 32-bit Ubuntu as well.  I have the following partitions:

Ext3 for main Ubuntu installation
Ext3 for /home
Swap
FAT32 for different OS's to share
NTFS for Windows Vista

I was going to take out space from the FAT32 partition for the main partition of 32-bit Ubuntu.  I was wondering whether I can share /home and swap between the two Ubuntus.

Thanks!

Yes you can share both /home and swap.

I advise you use a unique log in name for each distro.

Also when you install the swap partition will be formatted , meaning it's uuid will change , meaning you will need to update fstab

List your partitions with :

```
sudo blkid
``` 

update the uuid in /etc/fstab in the old version of Ubuntu

---

