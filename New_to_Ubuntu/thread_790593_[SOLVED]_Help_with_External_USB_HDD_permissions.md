---
title: "[SOLVED] Help with External USB HDD permissions"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Old_Grey_Wolf on 2008-05-11
I have an external usb hard disk that is ext3 formatted. When I boot Ubuntu 7.10, the disk icon shows on the desktop. I can open the disk by clicking the icon. When I try to copy a file to it I get the following:

"Error while copying to "/media/disk".
You do not have permissions to write to this folder."

What do I need to do to get permission to write to this disk?

---

### Post by TeoBigusGeekus on 2008-05-11
Post us the result of
```
sudo fdisk -l
```
that's -L and tell us which of the results is the external hd.

---

### Post by Old_Grey_Wolf on 2008-05-11
The /dev/sdf is the external.

Disk /dev/sda: 250.0 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         967     7310488+   c  W95 FAT32 (LBA)
/dev/sda2   *         968       23928   173585160    7  HPFS/NTFS
/dev/sda3           23929       28174    32099760   83  Linux
/dev/sda4           31954       32301     2630880    5  Extended
/dev/sda5           31954       32301     2630848+  82  Linux swap / Solaris

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008c78a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       19457   156288321   83  Linux

---

### Post by TeoBigusGeekus on 2008-05-11
Ok then... If your hd is shown as disk1 in your /media folder, then type 

```
sudo chown -R yourusername /media/disk1
```

This will make you the [COLOR="Red"]owner[/COLOR] of the volume, thus giving you write priviledges.

---

### Post by Old_Grey_Wolf on 2008-05-11
> **TeoBigusGeekus said:**
> Ok then... If your hd is shown as disk1 in your /media folder, then type 

```
sudo chown -R yourusername /media/disk1
```

This will make you the user of the volume, thus giving you write priviledges.

That resulted in the following:

"chown: changing ownership of `/media/disk/lost+found': Read-only file system
chown: changing ownership of `/media/disk': Read-only file system"

I still can't write to the disk. Get same error in original post.

---

### Post by TeoBigusGeekus on 2008-05-11
What happens if you try
```
sudo mkdir /media/disk/testfolder
```

---

### Post by Old_Grey_Wolf on 2008-05-11
> **TeoBigusGeekus said:**
> What happens if you try
```
sudo mkdir /media/disk/testfolder
```

I get the following:

"mkdir: cannot create directory `/media/disk/testfolder': Read-only file system"

---

### Post by TeoBigusGeekus on 2008-05-11
Can you write on it in window$?

---

### Post by Old_Grey_Wolf on 2008-05-11
> **TeoBigusGeekus said:**
> Can you write on it in window$?

Booted into Windows, what a PITA. Windows has been searching for a drive the last 10 minutes. I don't think it is going to find one.:lolflag:

---

### Post by TeoBigusGeekus on 2008-05-11
Just a question... Does this hd have a switch to toggle between read only/read and write mode, which you've forgotten?

---

### Post by Old_Grey_Wolf on 2008-05-11
> **TeoBigusGeekus said:**
> Just a question... Does this hd have a switch to toggle between read only/read and write mode, which you've forgotten?

No. This is the first thing I checked.

---

### Post by TeoBigusGeekus on 2008-05-11
Sorry, mate, but I can't think of anything else...
Someone else please?

---

### Post by Old_Grey_Wolf on 2008-05-11
> **TeoBigusGeekus said:**
> Sorry, mate, but I can't think of anything else...
Someone else please?

Whew, back into Linux.

Thanks for trying.

---

### Post by Old_Grey_Wolf on 2008-05-11
> **TeoBigusGeekus said:**
> Sorry, mate, but I can't think of anything else...
Someone else please?

I re-ran the "sudo chown -R yourusername /media/disk" command after rebooting and it works now. :confused:

Thanks

---

### Post by TeoBigusGeekus on 2008-05-11
It could have been a problem of inappropriate unmounting - either from window$ or Ubuntu...
Anyway, I' m glad!

---

