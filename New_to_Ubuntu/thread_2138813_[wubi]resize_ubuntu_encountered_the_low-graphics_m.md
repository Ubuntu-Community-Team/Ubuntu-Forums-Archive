---
title: "[wubi]resize ubuntu encountered the low-graphics mode"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by AnnabellChan on 2013-04-25
I am a new starter in Linux. I installed Ubuntu 12.04.2 LTS under Windows 7(using Wubi). 
When I used ```
sudo apt-get update
``` encountering an error that "No space left on device". Then I used ```
df -h
``` to check and the result was
[LIST]
[*]Filesystem Size Used Avail Use% Mounted on
[*]/dev/loop0 4.5G 4.2G 354M 93% /
[*]udev 1.5G 4.0K 1.5G 1% /dev
[*]tmpfs 582M 908K 581M 1% /run
[*]none 5.0M 0 5.0M 0% /run/lock
[*]/dev/sda7 96G 16G 80G 17% /host
[/LIST]

The partition table was
[LIST]
[*]Deive Boot Start End Blocks Id System
[*]/dev/sda1 * 7 HPFS/NTFS/exFAT
[*]/dev/sda2 7 HPFS/NTFS/exFAT
[*]/dev/sda3 7 HPFS/NTFS/exFAT
[*]/dev/sda4 7 Extended
[*]/dev/sda5 7 HPFS/NTFS/exFAT
[*]/dev/sda6 7 HPFS/NTFS/exFAT
[*]/dev/sda7 7 HPFS/NTFS/exFAT
[/LIST]
I googled it and resized my ubuntu following the steps in the "Automated resize" section of the official Wubi guide [https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk) to increase the size of partition to 10G. But after I rebooting ubuntu, an error message showed that **"The system is running in low graphics mode"** and *Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself".* Then I pressed Ctrl + Alt + F1 into the terminal and used ```
df -h
``` the result was

[LIST]
[*]Filesystem Size Used Avail Use% Mounted on
[*]/dev/loop0 9.2G 8.8G 0 100% /
[*]udev 1.5G 4.0K 1.5G 1% /dev
[*]tmpfs 582M 904K 581M 1% /run
[*]none 5.0M 0 5.0M 0% /run/lock
[*]none 1.5G 0 1.5G 0% /run.shm
[*]/dev/sda7 96G 16G 80G 17% /host
[*]overflow 1.0M 4.0K 1020K 1% /tmp
[/LIST]
So my question is why the use% of /dev/loop0 is even higher since I have resized the ubuntu and how to fix this problem? I will be very appreciated for your help~

---

### Post by bcbc on 2013-04-25
If you added 5GB and it's already filled then I'd guess there is some out of control log file. Something has filled up that space. Try:
```
sudo du -sh /var/log
```

It seems unlikely though. Mine is only 16MB.
```
bcbc@06:34:37:~$ sudo du -sh /var/log16M    /var/log
```


Was this on the very first reboot following the resize? Do you have any custom mount points?

---

### Post by AnnabellChan on 2013-04-25
yep, it is the very first reboot and the result of ```
sudo du -sh /var/log
``` is 53M. What does the "custom mount points" mean? Could u give me more detailed explaination? coz I'm a green hand~thx~

---

### Post by bcbc on 2013-04-25
Custom mount points - something in /etc/fstab where you're mounting another partition, and not under /media. The resize script is written to ignore different file systems so this shouldn't make a difference, but just trying to get some background info to figure out what might have happened. (I've never heard of this happening before)

---

