---
title: "External disk mounting error on Ubuntu 24.04.1 LTS"
date: 2024-09-01
forum: New to Ubuntu
---

### Post by temesa on 2024-09-01
Failed to mount “Iomega_Ext_Drive”
Error mounting/dev/sda1 at /media/xxxx/Iomega_Ext_Drive: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error.

---

### Post by yancek on 2024-09-01
Is this a partition on an external hard drive?
What type filesystem is on the drive?
Is this something new?  Have you been able to access this drive previously without problems?  If so, what changes if any were made just prior to the problem occurring?
Was the drive properly removed/unmounted?

---

### Post by temesa on 2024-09-02
Yes, I've already tried it on another PC with Ubuntu 22.04 without any problems.

Disklabel type: dos
Partition: /dev/sda1 with type HPFS/NTFS/exFAT and size 1.8T.

---

### Post by yancek on 2024-09-02
>  Yes, I've already tried it on another PC with Ubuntu 22.04 without any problems.


Does that mean you have mounted and accessed this drive from 22.04 after you had the problem with 24.04?  You have a windows filesystem on that partition so you need to use windows to repair it.  Are you sharing this drive with windows users?  If not, why use a windows filesystem?

---

### Post by temesa on 2024-09-02
Hi

Thanks for the answer.

The issue is as follows: 
This external drive has files from a computer with Windows. 
On the computer with Ubuntu 22.04, there has never been, and there isn't, any problem opening the drive. 
On the computer with Ubuntu 24.04, it doesn't open. 
The computer with Ubuntu 22.04 opens it without any problem even after trying it on Ubuntu 24.04. 
On Ubuntu 24.04, the same error message I mentioned earlier always appears, so I conclude that the problem is with Ubuntu 24.04.

---

### Post by yancek on 2024-09-02
Do you select to safely remove or unmount from 22.04 before attaching the disk to the 24.04 computer?  I expect that ntfs-3g is installed on both but you could check that.  Don't have any other suggestions and don't use 24.04 so can't check anything.

---

### Post by Morbius1 on 2024-09-04
If this partition is ntfs the issue is with ntfs3.

Ubuntu 22.04 will mount an ntfs partition not defined in fstab using ntfs-3g driver.

Ubuntu 24.04 will mount an ntfs partition not defined in fstab using the ntfs3 driver.

A workaround is to "blacklist" the ntfs3 driver from running:
```
echo 'blacklist ntfs3' | sudo tee /etc/modprobe.d/disable-ntfs3.conf
```
Then reboot the box.

This will force the file manager to use the ntfs-3g driver which does not have this issue.

---

### Post by temesa on 2024-09-12
**Thank you so much for your help!**
Your solution worked perfectly. I had been struggling with this issue for days, and blacklisting the ntfs3 driver resolved everything. I really appreciate you taking the time to explain the difference between ntfs-3g and ntfs3, and why the issue was happening in Ubuntu 24.04. Now my external drive mounts without any problems. Thanks again for your support and for sharing your knowledge!

---

