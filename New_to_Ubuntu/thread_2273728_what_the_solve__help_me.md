---
title: "what the solve ?? help me"
date: 2015-04-15
forum: New to Ubuntu
---

### Post by majdi3 on 2015-04-15
[IMG]http://www14.0zz0.com/2015/04/15/12/963907017.jpg[/IMG]

---

### Post by kerry_s on 2015-04-15
you can only have 4 primary partitions.

---

### Post by coffeecat on 2015-04-15
@majdi3, welcome to the forum.

If you need help with whatever it is you are trying to do, you need to provide more information. Are you trying to install Ubuntu? Are you trying to change the partitions on a drive with Ubuntu already installed? What is the screenshot from, a live session of Ubuntu or an installed Ubuntu?

---

### Post by majdi3 on 2015-04-15
> **coffeecat said:**
> @majdi3, welcome to the forum.

If you need help with whatever it is you are trying to do, you need to provide more information. Are you trying to install Ubuntu? Are you trying to change the partitions on a drive with Ubuntu already installed? What is the screenshot from, a live session of Ubuntu or an installed Ubuntu?


iam trying install ubuntu with wibi more than one 
and this screen shot by mobile when the wibi finsh i my windows 8.1 and restart whith ubuntu .

---

### Post by Bucky Ball on 2015-04-15
Forget Wubi. It is no longer supported and hasn't been for awhile. 

You can only have four primary partitions per physical drive so you need to create free space and make sure you only have three partitions so you can install Ubuntu and its /swap partition on the fourth (which would be an extended partition in to which you'd put the Ubuntu install and /swap on logical partitions). 

Please post with any questions you have regarding doing a dual-boot with Ubuntu and Windows on separate partitions. We are not going to be of much help when it comes to Wubi. Also, make sure you go with a supported release. 12.04 LTS, 14.04 LTS, or wait for 15.04 which will be released in a week or two. The LTS releases have five years support and the interim releases (anything not LTS) has nine months.

---

### Post by coffeecat on 2015-04-15
@majdi3, wubi does not work with Windows 8 and, as Bucky Ball says, wubi is no longer supported.

Your screenshot is puzzling. Windows 8 is normally installed on a disk with a GUID partition table (GPT), in which the old four primary partition limitation doesn't apply. And that would be irrelevant to wubi anyway. Perhaps it's a spurious error message because wubi can't work in Windows 8.

Installing Ubuntu as a dual-boot with Windows 8 is more challenging because of UEFI BIOS and GPT. People here can help you though, if you post full details of your hardware and current setup. This might be better in a new thread.

---

### Post by majdi3 on 2015-04-15
ok iam not speak english very will but i try to understand by google translation :)
i have 3 parts in my hard 
c: 78 GB and 33 GB free
d: 375 GB and 210 free 
E: 12 GB recovary 
ram : 4 GB
cpu ; i5 
this is my laptop dell 5010

---

### Post by yancek on 2015-04-15
You need to have unallocated space outside any partitions.  You indicate that you have free space inside the windows partitions.  That doesn't help.  Ubuntu and any Linux uses a Linux filesystem and those partitions have windows filesystems and an Ubuntu install there simply won't work.  You should be able to shrink one of your windows partitions to create free space, probably the "D" partition if that is a data partition.  Once you create unallocated space you should be able to install.  You would also need to check to see if windows is installed using UEFI/GPT which is highly likely and install Ubuntu in the same manner.

---

### Post by bofe on 2015-04-15
Wubi hasn't been developed for 2 years and is abandoned. 

Remember you can always install Ubuntu to USB or SD card and boot the OS from  that. The installer doesn't care that you are installing to USB.

---

### Post by hakuna_matata on 2015-04-19
> **majdi3 said:**
> iam trying install ubuntu with wibi more than one 
and this screen shot by mobile when the wibi finsh i my windows 8.1 and restart whith ubuntu .
IMHO you use Wubi for Ubuntu 14.10 but you do not use Windows in UEFI mode. This is also possible for Windows 8.1. 

IMHO your issue is a [known bug]("https://bugs.launchpad.net/wubi/+bug/1385930") and a workaround [is possible]("http://ubuntuforums.org/showthread.php?t=2251986").

But in most cases it is better to follow recommendations in posts above and to avoid Wubi.

---

