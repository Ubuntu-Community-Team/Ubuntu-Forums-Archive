---
title: "[SOLVED] External HDD Problems"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by shoot2kill on 2008-09-15
OK, i have an external HDD which i was backing up some files to my ubuntu install.

i had to force mount the drive for it to work properly, and i was in the process of backing up the data when i had a power cut, 

after restarting my computer i tried to mount the drive again, and cannot see it anywhere, the drive is spinning, but i cannot see it in "Computer" or "fstab"

the output of fdisk -l is:
> 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaffa47ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         912     7325608+  12  Compaq diagnostics
/dev/sda2   *         913        5776    39070080    7  HPFS/NTFS
/dev/sda3            5777        9729    31752472+   f  W95 Ext'd (LBA)
/dev/sda5            5777        9598    30700183+  83  Linux
/dev/sda6            9599        9729     1052226   82  Linux swap / Solaris


now i do have a dualboot XP and ubuntu, but i am unsure on what all of these partitions are, and i am hoping that one of them is the external as i NEED the data off of it, and hope it is not corrupt in anyway..

BTW, it was NTFS partition..

and i dont have a compaq as shown in the fdisk result.

thanks in advance for any help recieved..

---

### Post by Lord DarkPat on 2008-09-15
You have one recovery partition, 2 Linux Partitions, 1 Windows Partition, and one which looks like your ExHDD. I suggest plug it into the devil(windows) and back everything up, then format it, it should mount on Ubuntu. When that happens, you can format it to any FS you want from Ubuntu.
P.S. I had the EXACT same problem. ^^ worked

---

### Post by Dill on 2008-09-15
The external hard drive should show up as another device (/dev/sdb , for instance), not as a partition under /dev/sda . So I'm not sure that Ubuntu is recognizing the hard drive, but you can certainly see if Windows XP recognizes it.

Also, can you plug in your external HD, open a Terminal, and type 

```
ls /dev/sd*
```

---

### Post by shoot2kill on 2008-09-15
no at the ubuntu machine now, will try the command later on, but windows is not an option, for some reason neither xp or vista will recognise any drive atatched to my IDE to USB adapter, and finding a fix for windows is just WAAAY to much hastle.. i would rather get it working with ubuntu.. :P

---

### Post by shoot2kill on 2008-09-15
Dont know what the problem was, but after turning the laptop back on, it worked first time, (although i tried a reboot earlier).

thanks for your time..

Solved!

---

