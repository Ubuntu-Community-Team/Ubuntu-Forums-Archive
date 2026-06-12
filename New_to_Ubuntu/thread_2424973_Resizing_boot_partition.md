---
title: "Resizing boot partition"
date: 2019-08-18
forum: New to Ubuntu
---

### Post by rubyzera on 2019-08-18
Hello guys,

So recently i wanted to install Ubuntu as a backup system for my pc and i followed an install guide that only later on i found out it was for a BIOS environment, and i have a UEFI one.
The problem is that i have a 500GB Hard drive and Partitioned the following way (following the guide)
Root: 40GB
Home: 30GB
when i clicked "install now" after partitioning these two parts, the installed warned me that i didin't configure a boot partition, and i would have problems if i didin't, so i did partition the boot disk, but didin't realise after research i would only need 512mb to that partition, and i ended up partitioning about 410GB to the boot partition, leaving me with limited space for the system (to install games and stuff).

My question is: is there a way i can resize that partition and recover all this lost space or i need to redo the installation?

Thanks in advance.

---

### Post by Dennis N on 2019-08-18
To use the correct term, it's called an EFI system partition, not a boot partition, which is something else. Where is the EFI system partition (abbreviated ESP) you made in relation to root partition and home partition?

---

### Post by rubyzera on 2019-08-18
Oh, sorry for the incorrect terms, it's the first experience with linux i'm having.

The EFI partition is in the same disk as the home and root partitions, if that's what you're asking

[https://prnt.sc/oubd20](https://prnt.sc/oubd20)

Part.1 is the Root
Part. 2 is Home
Part.3 Is the EFI.
Also i want to correct the values, that were actually 40 and 50gb respectively for the root and home.

---

### Post by rbmorse on 2019-08-18
Let's help the new guy out a bit. 

rubyzers, open a terminal and type the following command:

```
df > report.txt
```

This will create a file named report.txt in your /home/*username/ *directory.   Open the file with the text editor, select all of the content (ctrl+a) then copy the text to the clipboard (ctrl+c).  

Please use code tags at the beginning and end of the message.

---

### Post by rubyzera on 2019-08-18
```
Filesystem     1K-blocks     Used Available Use% Mounted on
udev             4039852        0   4039852   0% /dev
tmpfs             812848     1968    810880   1% /run
/dev/sda1       38183144  9684056  26529736  27% /
tmpfs            4064232   122752   3941480   4% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs            4064232        0   4064232   0% /sys/fs/cgroup
/dev/loop3          1024     1024         0 100% /snap/gnome-logs/61
/dev/loop2          4224     4224         0 100% /snap/gnome-calculator/406
/dev/loop0        154752   154752         0 100% /snap/gnome-3-28-1804/31
/dev/loop1         55040    55040         0 100% /snap/core18/941
/dev/loop4         91392    91392         0 100% /snap/core/6673
/dev/loop5         15104    15104         0 100% /snap/gnome-characters/254
/dev/loop6          3840     3840         0 100% /snap/gnome-system-monitor/77
/dev/loop7         36224    36224         0 100% /snap/gtk-common-themes/1198
/dev/sda2       47799020 35795256   9545960  79% /home
tmpfs             812844      128    812716   1% /run/user/1000
/dev/loop8         55808    55808         0 100% /snap/core18/1074
/dev/loop9         90880    90880         0 100% /snap/core/7396
/dev/loop10         3840     3840         0 100% /snap/gnome-system-monitor/100
/dev/loop11        15104    15104         0 100% /snap/gnome-characters/296
/dev/loop12        43904    43904         0 100% /snap/gtk-common-themes/1313
/dev/loop13       153600   153600         0 100% /snap/gnome-3-28-1804/71
```

---

### Post by rbmorse on 2019-08-18
I screwed up the instructions on the code block, but don't worry about that. 

Looking at your post, I don't even see a boot/efi partition listed.  Looks like Ubuntu installed in BIOS mode and it will work fine that way.  To the best of my knowledge, there is no way to convert an existing BIOS mode installation to a UEFI mode one, that would require a complete fresh install.  

You have plenty of space in your / (root or system) partition and adequate space in the /home partition.  If the computer is otherwise working, then I would not worry about it.   

Again, sorry about creating confusion about the code tags.  I edited my earlier post to remove the error, but you made your reply before I got it posted.

---

### Post by Dennis N on 2019-08-18
> **rubyzera said:**
> Oh, sorry for the incorrect terms, it's the first experience with linux i'm having.

The EFI partition is in the same disk as the home and root partitions, if that's what you're asking

[https://prnt.sc/oubd20](https://prnt.sc/oubd20)

Part.1 is the Root
Part. 2 is Home
Part.3 Is the EFI.
Also i want to correct the values, that were actually 40 and 50gb respectively for the root and home.

Not so hard. Use gparted, delete the 3rd partition. Resize 2nd partition to the size you want. Make a new ESP after it. If Ubuntu is the only OS, the ESP can be 100 mB. Then reinstall. 
Usually the ESP is first, so you could just start over and put it in that position. But it should work as 3rd partition.

---

### Post by rubyzera on 2019-08-18
Gonna take a look. Thanks

---

### Post by Dennis N on 2019-08-18
Looking at your revised figures, 40 GB is enough for a root partition. You could probably do fine with 50 GB for home as well. My whole system is set up in 25 GB of space. If you agree, you could use gparted to just resize the ESP to a reasonable value and not have to reinstall.

---

