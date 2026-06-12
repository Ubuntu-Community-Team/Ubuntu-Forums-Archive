---
title: "Dual boot, 2 separte HDDs"
date: 2012-10-21
forum: New to Ubuntu
---

### Post by JamesDonaldChilds on 2012-10-21
Ok, My issue is I have Windows 7 on one HD and Ubuntu 12.04 on a second HD, I installed Ubuntu 2nd yet I can not seem to find the GRUB menu allowing me to boot into Windows, In order to boot into Windows I have to load the bios and change the HD boot order.

Both the hard drives are 136GB SCSI HDs on a raid card. If that makes a difference let me know and I will get model details.

Any help appreciated =]

---

### Post by dniMretsaM on 2012-10-21
Hold the Shift key on boot up. If Windows isn't on the list you'll need to boot into Ubuntu, open a terminal window, and run:
```
sudo update-grub
```

---

### Post by oldfred on 2012-10-21
I do not really know RAID. But RAID is really one drive system. It is seen as one larger drive or as one smaller drive that is mirrored or some combination depending on the type of RAID.

You normally install grub to the MBR of a drive (IF not UEFI), but with RAID install to the root of the RAID.

[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

With Linux RAID & LVM 
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

---

