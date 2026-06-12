---
title: "windows files"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by KnavishClout on 2008-05-28
I have Windows Server 2008 installed on a 30GB partition on my hard drive.  Then I dedicated  the remaining space to Ubuntu 64 bit.  I haven't had a reason to boot back into Windows since I did the install, but this morning when I tried to select the Windows option from grub, the computer just rebooted.  I tried several times. 

This wouldn't be an issue, except that I have some files I need to access and Ubuntu can't access the Windows partition for some reason.

If anyone knows how I can access these files or boot into windows, please let me know.

---

### Post by sayakb on 2008-05-28
What error do you get when trying to mount the Windows partitions? Did you try force mounting them?
Add this to /etc/fstab **and reboot**
```
/dev/sda1 /media/sda1 ntfs-3g defaults,force 0 0
```But first, make a directory /media/sda1:
```
sudo mkdir /media/sda1
```Also, replace sda1 with whichever applicable for your Windows partition. Also comment out (add a # at beginning)the existing line in the fstab file for the windows partition.

---

### Post by alexandremrj on 2008-05-28
Perhaps the windows directories aren't mounted

Check this

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

