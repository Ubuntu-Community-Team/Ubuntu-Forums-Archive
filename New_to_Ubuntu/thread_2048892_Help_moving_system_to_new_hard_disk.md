---
title: "Help moving system to new hard disk"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by Deniz343 on 2012-08-27
Hi,

I'm moving my system to another internal HDD with following steps in this URL: [https://help.ubuntu.com/community/MovingLinuxPartition](https://help.ubuntu.com/community/MovingLinuxPartition)
Everything was going perfectly. When I came this step> Update new ubuntu partition as bootable

gnome> System -> Administration -> Disk Utility
Find and Click on new Ubuntu partition to highlight the partition
Click on "Edit Partition"
Check "Bootable" check-box
And clock "Apply" button
Reboot you machine again
On booting, make sure new partition's grub menu is displayed as.

I go to the disk utility page, selected new HDD, clicked edit partition, Checked bootable box. Then few minutes later a window appeared;
> Sorry, the program "udisks-daemon" closed unexpectedly 
Another thing I saw on this error report is > message did not recive a reply

---

### Post by Bashing-om on 2012-08-27
Hi deniz ;

 New one on me ,.. what pops into my mind is the boot flag. Only one boot flag is required, that will be the partition that grub installs to. Perhaps the disk utility closed when unexpected flag was encountered ?

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by Deniz343 on 2012-08-27
My English is bad. But error is saying to me > Your memory isn't enough to solve the problem.

---

