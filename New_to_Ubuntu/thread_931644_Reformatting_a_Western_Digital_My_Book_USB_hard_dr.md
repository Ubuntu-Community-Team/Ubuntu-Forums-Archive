---
title: "Reformatting a Western Digital My Book USB hard drive"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Fakename McGrew on 2008-09-27
I wish to reformat my new WD My Book 1TB USB hard drive to NTFS. Specifically, I'd like to copy my 125 GB Windows NTFS partition onto the drive for backup purposes. However, I don't know how. I tried using GParted, but all of the formatting options for the USB drive were greyed out. Any ideas, please?

---

### Post by phidia on 2008-09-27
You need to install the ntfs-3g package. See the guide [here]("https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite").

Actually [this]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G") is a more complete howto.

---

### Post by gastly on 2008-09-27
Hi, You can format your USB drive to NTFS in the following way...

Open up a terminal and type the following:
> 
[B]sudo mkntfs /dev/<device-name>

Eg: sudo mkntfs /dev/sdb1[/B]

**NOTE:** If you don't know your device name, then in the terminal type **mount** , this will show all the devices that are mounted by Ubuntu. Search for your device, it usually is **sdb1** or something like that. [COLOR="Red"]**BUT Please DOUBLE CHECK it before using this command!**[/COLOR]

---

### Post by gastly on 2008-09-27
Oh yeah, forgot to mention you need to install the ntfs support first :mrgreen:

---

