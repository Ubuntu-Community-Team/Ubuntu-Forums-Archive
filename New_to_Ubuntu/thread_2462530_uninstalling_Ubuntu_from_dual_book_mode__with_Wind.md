---
title: "uninstalling Ubuntu from dual book mode  with Windows 10"
date: 2021-05-22
forum: New to Ubuntu
---

### Post by markb60000 on 2021-05-22
Ubuntu Forum

I have Windows 10 and Ubuntu in dual boot mode.  I want to uninstall Ubuntu (in preparation to reinstalling it).


I have created a USB drive for Windows in case there are any problems.
[ATTACH=CONFIG]288528[/ATTACH]
Now I am at the point where I am at the Disk Management window for Windows 10, and will uninstall Ubuntu (please see attachment).  

Reason for this post is that I want to be sure that I do the right thing.  I plan to delete the three entries for Disk 0 – partitions 1, 4 and 6).  Is that correct?  

Thanks,
Mark

---

### Post by oldfred on 2021-05-22
Is Windows UEFI or BIOS? If UEFI, then you have Windows boot loader in first partition.
There is no reason to delete any partitions.
Just use Something Else and choose the same partitions for / & /home or if partition is swap it will auto find it. 
And if Windows is UEFI, you need to reinstall Ubuntu in UEFI mode & it will auto find the ESP.

Post this from Ubuntu live installer's terminal:
sudo parted -l

---

### Post by markb60000 on 2021-05-23
Thanks for your response.  I do not know anything about how matters relating to systems, so, unfortuantely, can only do things following step-by-step instructions. 

 I am using instructions from [https://itsfoss.com/uninstall-ubuntu-linux-windows-dual-boot/](https://itsfoss.com/uninstall-ubuntu-linux-windows-dual-boot/)   So the reason for my post was to simply confirm that deletion of the three Disk 0 entries shown in the attachment.

If deleting these 3 entries is not advisable, maybe I need to find another step-by-step guide for deleting (or overwriting) Ubuntu.

What do you suggest?

Thanks,
Mark

---

### Post by oldfred on 2021-05-23
Typical Something Else.
Just choose the existing partitions, not create new.
[https://www.tecmint.com/ubuntu-19-04-installation-on-uefi-firmware/](https://www.tecmint.com/ubuntu-19-04-installation-on-uefi-firmware/)

Post this if you want to review of existing partitions. either existing install or live installer in live mode.
sudo parted -l
If you booted into existing install.
lsblk -o name,mountpoint,label,size,fstype,fsused,uuid | egrep -v "^loop"

---

### Post by Impavidus on 2021-05-24
That screenshot in your first post doesn't really tell us what those partitions are. Windows doesn't really tell us anything about those partitions, other than their size. That's why oldfred suggested a few commands to get that information from Ubuntu.

And indeed, there's no need to remove the old operating system before reinstalling it. You can simply overwrite, if you want to keep the same partitions. If you want to change partitions, deleting the current partitions using the live session, then creating new partitions will do. The live session can tell you what they are.

BTW, is this an UEFI or a legacy system? Windows 10 is usually UEFI, but none of the partitions are labelled as EFI. If legacy, there can only be 3 primary partition + 1 extended partition with logical partitions, but they aren't clearly labelled. The suggested commands to run in Ubuntu should clear it up.

---

