---
title: "Rename External Hard Drive"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by ElliottMarlow on 2008-05-05
Hi. I recently bought a Western Digital 250 GB external hard drive. When mounted, the name appears as "My Passport," but I want to rename it, mostly to get rid of the space between "My" and "Passport."

Right-click, rename doesn't work, nor does highlight, F2. 
Is there a terminal command?

Thanks

---

### Post by mlentink on 2008-05-05
Hmmm...
afaik you can only rename partitions when unmounted. So what I would try is to unmount the drive, fire up GParted and rename the partition.
But you could also connect it to a windows box and do it from there. But then you would need a windows box, and not everyone has that readily available... ;-)

---

### Post by forestpixie on 2008-05-05
[This]("https://help.ubuntu.com/community/RenameUSBDrive") worked for me renaming ext3

---

### Post by Rocket2DMn on 2008-05-05
You can install the metapackage ntfsprogs then use ntfslabel to give a better label to the drive (say it's sdb1).  Unmount it, then run
```
sudo apt-get install ntfsprogs
sudo ntfslabel /dev/sdb1 usbdisk
``` where usbdisk is the new label for the hard drive (don't use a name with spaces)

---

### Post by ElliottMarlow on 2008-05-06
I tried mounting in Windows, still no luck. It told me I didn't have permission. I'll give Gparted a shot though. Thanks

---

### Post by lemonoid on 2013-03-10
i know this is old but I need to frankenstein it. i have the exact same issue i got a 1tb  WD tonight named My Passport. I need no spaces, as the op said. I tried the suggestion to install ntfsprogs, unmount the device, and then ntfsprogs /dev/sdb1 usbdisk (or whatever you wanna name it too) but it said ```
 The device /dev/sdb1 doesn't exist
 
``` 
so then i tried to mount the external and try it and i got this
```
 Cannot make changes to a mounted device 
```
has anoyne ever figured out how to change the name of an external such as this? or maybe anything i'm doing anything wrong in this situation

---

### Post by fantab on 2013-03-10
I don't think you can change the Device name that easily. It is written in the firmware. However you can label and change labels of the partition. If your Disk has only one partition then **unmount the disk** and run:

```
$ sudo dosfslabel /dev/sdb1 drivelabel
(or whatever) if the drive is FAT

$ sudo e2label /dev/sdb1 drivelabel
if the drive is ext4.
```

**Next time start your own thread, no need to dig up the dead.**

---

### Post by vanadium on 2013-03-10
It is all there in stock Ubuntu nowadays, with the "Disks" utility. Select the drive in the left pane, unmount with a button in the right pane, then click the gear button to select the command "Edit filesystem label".

---

