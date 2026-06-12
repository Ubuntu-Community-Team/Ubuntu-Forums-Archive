---
title: "Can a Windows XP internal recovery disk still be used to restore the previos OS?"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by yocally on 2013-05-24
Hey guys, rather new to ubuntu I suppose though this isn't my first time playing around with it. I was wondering if the internal recovery disk for a windows XP computer can still be used after installing Ubuntu to revert back to what was previously installed on the computer or if that gets wiped when Ubuntu gets installed, I see no reason why it should get wiped but since it isn't my computer, I thought I'd make sure.

Thanks!

---

### Post by Hodevah on 2013-05-24
> **yocally said:**
> Hey guys, rather new to ubuntu I suppose though this isn't my first time playing around with it. I was wondering if the internal recovery disk for a windows XP computer can still be used after installing Ubuntu to revert back to what was previously installed on the computer or if that gets wiped when Ubuntu gets installed, I see no reason why it should get wiped but since it isn't my computer, I thought I'd make sure.

Thanks!

yes, it is possible to use it and it will restore your windows xp operating system to what was previously installed. Bear in mind that if you do this it will or may remove Grub and hence it wont be possible to login into Ubuntu or any other Linux distro. 

You see the problem with Windows is that it does not play nice with other operating systems. It's kind of selfish to put it another way. Linux on the other hand plays nice with other linux distros, non-linux distros such as Windows pretty much all the time. That's why Linux is a  nice little boy whom we should always pat nicely on the head and say he's a nice guy. Windows, on the other hand, is a bad guy. :D

So if you wind up in this situation where you won't be able to login to Ubuntu any longer because  you used the Windows XP disk, you can use the Ubuntu Recovery Disk which you can download and then instert to your CD drive and use the BOOT REPAIR application that comes with it. It's very easy and simple to use. I hope that this information has helped you.

---

### Post by squakie on 2013-05-25
You're saying the 'internal' recovery disk.  If by this you mean a recovery partition?  If so the answer is a little different.  Option one is that you did not tell Ubuntu to use the entire disk.  If you did, then it's likely that the recovery partition no longer exists.  Option 2 is you created or have one or more 'reset to factory defaults' disk(s) then you may be able to if they don't rely on the recovery partition.

---

### Post by Mark Phelps on 2013-05-25
It depends entirely on what's on the "recovery disk" -- no one knows for sure, we're all just guessing.

Some recovery disks only boot the PC into a restore program, which then searches the drive for the Recovery partition, and if that is intact, will then do a full restore of the original Windows setup -- removing all files and apps in the process.

Other recovery disks contain a compressed image of the Windows install -- and in these cases, will erase the drive and restore the original setup.

---

### Post by PeteJensen on 2013-05-25
Access was trashed on my dual boot IBM/Lenovo T43 during an upgrade from v8.4 to v10.4.  Access has been stable though on my Lenovo T60 inclding an upgarde to v12.04.

Remember that this restoration will take you back to the original shipping configuration of the machine so you may need supplementary disks for Service Pack 3 or advanced versions of other Windoze stuff like Media Player, the dot-net framework or any applications.

---

### Post by coldraven on 2013-05-25
This is from my hazy memory so it may not be accurate.
When I bought this laptop it had XP and a recovery partition.
I somehow got it to dual boot with Ubuntu.
One day I accidentally booted it into the restore partition, even though I clicked "Cancel" it still had overwritten the Grub boot menu.
I managed to fix that but started to use XP less and less. I was lucky enough to have a restore CD so I just deleted XP and now only run it in a virtual machine.

If you  have the facility to make a restore CD I would do that first.
This link is for HP but try Googling for your brand
[http://h10025.www1.hp.com/ewfrf/wc/document?cc=uk&lc=en&dlc=en&docname=bph08097](http://h10025.www1.hp.com/ewfrf/wc/document?cc=uk&lc=en&dlc=en&docname=bph08097)

More importantly, make a backup on an external drive of all the important data.

---

