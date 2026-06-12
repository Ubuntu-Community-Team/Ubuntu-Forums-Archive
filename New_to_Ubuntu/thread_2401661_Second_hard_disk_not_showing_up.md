---
title: "Second hard disk not showing up"
date: 2018-09-20
forum: New to Ubuntu
---

### Post by dragonchaser2 on 2018-09-20
Installed Ubuntu. All went well. Added a 2nd HD in my PC. Seems to show up in BIOS (it has an ID, no name, no size) but not in Ubuntu. I see an sda but no sdb. This was a Windows disk if I remember correctly. Is this the reason I can’t see it? Do I have to format it first? But how if I can’t see it?

---

### Post by Autodave on 2018-09-20
gparted should be able to help you. PLEASE make sure that you select the correct disk!!!!!!

---

### Post by yancek on 2018-09-20
Generally, a usb drive or any external drive will show under the /media/username directory.  Have you checked there?  It will usually show by UUID.

---

### Post by oldfred on 2018-09-20
If it was used with Windows 8 or 10, it still may be hibernated and then you can only manually mount in read/only mode.
Newer Windows uses fast start up which is just hibernation and Linux NTFS driver will not mount read/write to prevent damage.

Best not to use NTFS unless you have Windows as it will need chkdsk or defrag periodically and you cannot do that from Linux.

---

### Post by dragonchaser2 on 2018-09-21
I installed GParted. The only thing I can see is sda1. So that must mean my HD must be Linux formatted, right? But... how if Ubuntu doesn’t see it?

---

### Post by yancek on 2018-09-21
So if you only have Ubuntu installed and that is on sda1, did you click the down arrow in the upper right corner of the GParted window to show additional drives?

While booted to Ubuntu, run the command below to see if your additional drive/partition(s) show:

```
sudo parted -l
```  Lower Case Letter L in the command.

---

### Post by reginald3 on 2018-10-06
Guys, I'm really struggling with this:

@Autodave : I have installed Gparted; disk won't show up

@yancek : its not a usb drive or any external drive; it's an internal hard disk

@oldfred I have tried with a Windows 10 disk, it may indeed still be hibernated but I cannot / don't know how to manually mount in read/only mode. I know newer Windows uses fast start but I can't even see the disks in Ubuntu. Als tried with a Linux disk (Centos) but no show.


@yancek : when I do sudo parted -l only one disk show up, the SSD root disk

Any ideas?

---

### Post by reginald3 on 2018-10-06
Solved. Very stupid of me: in the bios I had activated SATA-0 and SATA-1.

I was under the impression this related to disk 0 and disk 1 but it doesn't.

SATA-1 relates to the CD/DVD.

Enabled SATA-2. Problem solved.

Thank you for your help and sorry for the inconvenience.

---

