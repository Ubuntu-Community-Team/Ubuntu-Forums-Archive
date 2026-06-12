---
title: "Reformating"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by gsankar on 2013-03-19
I am running Ubuntu 12.10 on Lenovo X61 Laptop. I have a Seagate HDD running on a USB port which also has Ubuntu 12.10. I want to 
delete the files on the USB drive and re-partition it. While Lenovo recognizes the USB HDD, while reformating with FAT file system (recommended) 
an error message comes as follows:

     " Error creating file system: helper exited with exit code 1: helper failed with unit:: non DOS media. mlabel: cannot initialize drive. " 

Waht do I do? Any help would be appreciated.

---

### Post by Bashing-om on 2013-03-19
gsankar; Hi !

Did you attempt that operation while the drive was in a mounted state ?
I would suggest that you (re)format the drive from a liveCD (thus the drive is not mounted) and use the GParted utility to reformat the drive.

 Is there a particular reason to format to FAT as that filesystem now-a-days does have some limitations.
[INDENT=2]
just my opinion
[/INDENT]

---

### Post by gsankar on 2013-03-20
Thanks for the reply. Will try what is suggested. FAT was the only option avilable. I would have prefered NTFS. 

GS

---

### Post by Bashing-om on 2013-03-20
gsankar; Good luck !

GParted has a ton of filesystems to format to. Did you do the initial format of the usb drive with Windows, maybe formatted in GPT ?
Look at the drive with terminal code:
```
sudo fdisk -lu
``` to see what ubuntu sees.[INDENT=3]
try'n to help

[/INDENT]

---

