---
title: "Partition question"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by ags40 on 2008-08-20
- If I re-format my sda1 partition will the MBR be also erased?

- If I make a backup of my sda1 partition with Partimage, will the MBR also be copied?

Thanks to you all.

---

### Post by Titan8990 on 2008-08-20
The MBR is never part of a partition. It will only be backed up by partimage if it specifically has a feature for backing up the MBR. 

To backup the MBR is completely pointless IMO. It takes less than 1min to reinstall GRUB....

---

### Post by Shippou on 2008-08-20
Hello...

If you reformat from an installation cd, I think it will modify the MBR.

I don't know about partimage though, but I think it will backup your MBR.

Just backup your data files though. :)

---

### Post by bobnutfield on 2008-08-20
If you only format the partition the MBR should remain intact.  But you should back it up first if you need to keep it.  Here is a link with instructions on how to backup your MBR:

> [http://www.backuphowto.info/backup-mbr-linux](http://www.backuphowto.info/backup-mbr-linux)

---

### Post by Titan8990 on 2008-08-20
What is the point of doing all that to backup something that is VERY widely available on many different types of media, does not store personal or preference information, and can be reinstalled in no time???

---

### Post by bobnutfield on 2008-08-20
> **Titan8990 said:**
> What is the point of doing all that to backup something that is VERY widely available on many different types of media, does not store personal or preference information, and can be reinstalled in no time???

According to the site I directed the OP to:

> Since the MBR records some information about your hard disk partitions and it loads the operating system, it is very important for a computer. Some virus can damage the MBR. They can modify the MBR so that they can start before the operating system. Or it makes your computer not to be able to run. Reinstall the operating system can solve this problem but it takes too long time. In fact, if you backup the MBR, the solution is very easy: just restore it.

I do not have Windows on my machine and have not booted into a Windows machine in a loooong time, but the OP did not specify whether he was booting from grub or a windows MBR.  I know from experiences years back that having a backup of your MBR is important on a Windows machine.

---

### Post by Titan8990 on 2008-08-20
But as of recent (release of Vista) Windows has tools for reinstalling their bootloader in the MBR just like you can reinstall GRUB. I assume that the OP is using GRUB if he is using kubuntu. 

Either way even if you don't have linux and you only have Windows, GRUB will still boot it.

For a user that has no idea what a MBR is or how to install a bootloader there then I could see a reason to back it up but I don't believe this is the case with the OP.

---

