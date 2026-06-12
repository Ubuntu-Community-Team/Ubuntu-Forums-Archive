---
title: "Corrupted partition"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by theswarmy on 2011-10-22
As the title suggest i have a corrupted/damaged partition(well i believe this to be the case) i was dual booting Windows7/Ubuntu until about 4 hours ago, i didn't have much space left on Ubuntu and decided to use gparted to divide the windows partition more and add more space to the Ubuntu one, but during the process for some strange reason my computer decided to crash, and restart. to my surprise when i came back onto Ubuntu that my whole windows drive was gone, panicing i decided to look up what i could do to fix it, it seems there was a program called "testdisk" that could help me with this, so i decided to give it a try and analyze the partitions as the tutorials said, but now im faced with the following none of them say "NTFS" as they should for the windows partition they say "Linux , Linux "HPFS/NTFS"(but this is the recovery drive) " i have provided screenshots so you could see what it says and probably better sort me to what i could do to fix this problem


thank you for your help
--Swarmy

[http://i.imgur.com/nqz9O.png](http://i.imgur.com/nqz9O.png)

---

### Post by rsvancara on 2011-10-22
What does the following produce?

```
sudo parted -l
```

--Randall
[http://www.knowyourlinux.com](http://www.knowyourlinux.com)

---

### Post by theswarmy on 2011-10-22
> **rsvancara said:**
> What does the following produce?

```
sudo parted -l
```

--Randall
[http://www.knowyourlinux.com](http://www.knowyourlinux.com)


this:

my bad i read that as 1 not l it shows this


Model: ATA WDC WD3200BEVT-6 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  266GB  266GB   primary   ntfs         boot
 2      266GB   306GB  39.9GB  extended
 5      266GB   304GB  38.2GB  logical   ext3
 6      304GB   306GB  1684MB  logical
 3      306GB   320GB  13.9GB  primary   ntfs


incase this helps at all
[http://i.imgur.com/sdKKN.png](http://i.imgur.com/sdKKN.png) <-- (what gparted shows)

edit: and this
[http://i.imgur.com/1f3X9.png](http://i.imgur.com/1f3X9.png)

---

### Post by rsvancara on 2011-10-22
Which version of Ubuntu are you using right now?  Are you also running windows XP or Windows 7?

---

### Post by theswarmy on 2011-10-22
Windows 7,

also
Ubuntu
Release 11.10(oneiric)
Kernel Linux 3.0.0-12-generic
Gnome 3.2.0

what testdisk shows before the search([http://i.imgur.com/YiEB8.png](http://i.imgur.com/YiEB8.png))

---

### Post by theswarmy on 2011-10-22
should i try booting into windows?

i want to atleast be  able to boot into windows using nautilus to get my files.

---

