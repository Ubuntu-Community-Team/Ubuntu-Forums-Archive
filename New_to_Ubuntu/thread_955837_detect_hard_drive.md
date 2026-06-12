---
title: "detect hard drive"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by bpgunner on 2008-10-22
How do I get Xubuntu to detect the second hard drive I plugged in after the install?

---

### Post by D3M0L1$H3® on 2008-10-22
> **bpgunner said:**
> How do I get Xubuntu to detect the second hard drive I plugged in after the install?

it should detect it automatically.
if not install Gnome Partition Editor (GPartEd) or use it on the live cd, and you will need to reformat it.
what is it right now? NTFS? or FAT?

---

### Post by Nxion on 2008-10-22
Is it a internal or external?

if it is an internal you would have to format it first and then add a line to your fstab file so everytime you boot up it mounts that harddrive. Try this:
[URL="https://help.ubuntu.com/community/DrivesAndPartitions"]
https://help.ubuntu.com/community/DrivesAndPartitions[/URL]
[URL="https://help.ubuntu.com/community/InstallingANewHardDrive"]
https://help.ubuntu.com/community/InstallingANewHardDrive[/URL]
[URL="http://ubuntuforums.org/showthread.php?&t=283131"]
http://ubuntuforums.org/showthread.php?&t=283131[/URL]

Also check this thread out. Look at post number 9: [http://ubuntuforums.org/showthread.php?t=955495](http://ubuntuforums.org/showthread.php?t=955495)

If it an external, then Ubuntu should just pick it up and mount it automatically.

Hope that helps.

---

### Post by Elfy on 2008-10-22
If it is formatted you cna add it to fstab for it to be mounted at boot, you need to 

1 - make a folder for the drive to mount to
2 - add a line to fstab with drive and folder information 

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Youy can get drive information by running 

```
sudo fdisk -l
sudo blkid
```

If you need help we will need the information from those two commands

---

### Post by bpgunner on 2008-10-22
Thanks, I'll check all the above.
It was detected, but I just removed Ubuntu and installed Xubuntu.I unplugged the second internal HD to avoid any mistakes.

---

