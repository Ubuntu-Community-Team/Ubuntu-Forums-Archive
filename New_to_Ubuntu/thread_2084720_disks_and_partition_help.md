---
title: "disks and partition help"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by jamesleeadf on 2012-11-16
:) hi all, im new to ubuntu, i used windows for the past so i learning the concept in linux

before  i install ubuntu, i having C:\ as winXP and d:\ as a storage. i couldn't find my d:\ after install and i guess ubuntu cleared off every partition in my hardisk.

if it does, how can I interpret the DISKS? is it i having 3 partition now?160GB, 160GB and 255MB drive? i can see the 255MB drive on my HOME but not the others.

or please link me to a partition creation tutorial page?
i attached my printscreen here, please teach me how to understand the DISK.

Thanks

---

### Post by ALinuxWindowsBalance on 2012-11-16
DOS, or Windows, label and mount partitions differently than Linux does. So different, that it takes a while to understand just how different they are. First difference is the label. Windows gives the A: through Z: label for partitions and disks. Linux uses /dev/sd(x)

Confusing, huh? **The partitions are actually mounted in a folder you can get to, not just My Computer.** So your first partition/disk will be ```
 /dev/sd**a** 
```
while your second is ```
/dev/sd**b**
```. Do you see a pattern?
this goes all the way through A to Z, kinda like Windows. Now, I think in Windows 7 you can mount partitions/disks in a NTFS folder. This is the **same concept**. If your partitions can't be mounted, It's probably because they are formatted with the NT filesystem(NT FS)
That is a strict Windows-only FS, and is the most frustrating from your point of view.

There might be a package in the Ubuntu Software Center that gives support for NTFS in Nautilus, your Home Folder icon.
I personally don't know, because I've been using Linux for so long, that I've actually needed to re-learn windows.

---

### Post by Mr_JMM on 2012-11-16
Paste the results of the following terminal commands:

```
sudo fdisk-l
```
```
sudo blkid
```

These commands show you (us) how your hard drive(s) are partitioned. We can then go through the results for you and try to explain how it's now laid out and what you need to do.

---

