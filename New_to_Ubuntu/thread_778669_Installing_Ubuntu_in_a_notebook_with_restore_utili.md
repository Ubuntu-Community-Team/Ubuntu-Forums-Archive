---
title: "Installing Ubuntu in a notebook with restore utility"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Accinson on 2008-05-02
Hi,
i would like to install Hardy in a Dell Inspiron 1300 laptop,which has already installed windows XP in it.I have already done a backup of the important data,just in case,but i would really hate to have to reinstall all the programs and stuff,so i'm trying to do it very carefully :)

What i am concerned about is the fact that this notebook has an integrated restore utility,and i am afraid to mess with it,since i would also like to maintain this very handy capability.

I have already tried the liveCD,to see the output of fdisk -l:
> 
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa4359c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        6884    55215405    7  HPFS/NTFS
/dev/sda4            6885        7295     3301357+  db  CP/M / CTOS / ...

So i guess the sda1 is the builtin Dell restore utility and sda2 is obviously winXP.I dont really have a clue about sda4 honestly....

What i basically want to ask is:can i trust the Hardy installer or i should do something more to maintain the restore utility and winXP?

Thanks in advance and thanks for the awesome support you provide :)

---

### Post by Accinson on 2008-05-02
Anyone? :)

---

