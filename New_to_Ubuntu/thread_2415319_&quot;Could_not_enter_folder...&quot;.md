---
title: "&quot;Could not enter folder...&quot;"
date: 2019-03-24
forum: New to Ubuntu
---

### Post by deanr2 on 2019-03-24
I've got a desktop with two hard drives - one for boot, one for media etc. On a clean install of Kubuntu 18 which I wanted to try out I find I cannot access the second drive at all. Although it is listed on the left of the file manager when I try to open the folder I get the message "Could not enter folder/media/kubuntu/Seagate 500."

I seem to remember having the same problem with Ubuntu last time and tried (and then abandoned) that OS. What's more, there is no problem opening the second hard drive on installations of Mint or Manjaro. I can access all my files just like any other drive.

This leads me to ask two questions:

1. How can I use GUI to access my second hard drive?
2. Why is this a problem on Ubuntu and not Mint/Manjaro. etc.? Is there a reason for blocking simple access to drives? For new users this would be immediately off-putting and drive users back to windows or to another distro.

Music obliged for any help as I'd really like to run at least one official Ubuntu flavour and KDE seems to be a popular DE.

---

### Post by uRock on 2019-03-24
It is very odd that you're unable to access the secondary drive.  My system has multiple drives that mount without issue.

Is the drive NTFS or EXT*? Encrypted? What's the output of the following command?
```
sudo fdisk -l
```

---

### Post by deanr2 on 2019-03-24
Gnome Disks says Ext4 ( version 1.0 )

Output from sudo fdisk -l is:

[FONT=monospace][COLOR=#000000]**Disk/dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors**[/COLOR]
Units: sectors of 1 * 512 = 512 bytes 
Sectorsize (logical/physical): 512 bytes / 512 bytes 
I/O size(minimum/optimal): 512 bytes / 512 bytes 
Disklabel type: dos
Disk identifier: 0x63fa630d 

[COLOR=#000000]**Device    **[/COLOR][COLOR=#000000]**Boot   **[/COLOR][COLOR=#000000]**Start **[/COLOR][COLOR=#000000]**End       **[/COLOR][COLOR=#000000]**Sectors   **[/COLOR][COLOR=#000000]**Size   **[/COLOR][COLOR=#000000]**Id **[/COLOR][COLOR=#000000]**Type**[/COLOR]
/dev/sdb1        2048  976773167 976771120 465.8G 83 Linux[/FONT]

---

### Post by deanr2 on 2019-03-24
Hmm. As it was a clean install anyway and I was playing around I re-installed Kubuntu from scratch. No problem now. Just one of those things I guess. 

Thanks for your help anyway, uRock. If nothing else I discovered that GNOME Disks from the Discover store is a useful tool that was missing from the standard suite of apps ;)

---

