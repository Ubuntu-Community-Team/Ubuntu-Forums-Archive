---
title: "Dual Boot?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by Enigma52809 on 2008-09-27
Okay, I just installed Ubuntu onto a seperate partition of my hard drive. I had a fun time going around on it and setting up a couple things (so the OS DID work, at least to some extent). Now, I restarted my computer to see if I could still get into Windows. I can get into Windows fine, but there is no option for me to go back into Ubuntu when I start up my computer. How can I access Ubuntu again?

---

### Post by bumanie on 2008-09-27
Boot with ubuntu live cd and post the terminal ouput of > sudo fdisk - lu

---

### Post by Elfy on 2008-09-27
```
sudo fdisk -lu
```

---

### Post by Enigma52809 on 2008-09-27
Here is the readout. I'm pretty sure I installed correctly, but not much harm if I need to reinstall it, I guess.

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00063a9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    19535039     9767488+  83  Linux
/dev/sda2   *    19535040   197551304    89008132+   7  HPFS/NTFS
/dev/sda3       306712980   312576704     2931862+  82  Linux swap / Solaris
/dev/sda4       197551305   306712979    54580837+   5  Extended
/dev/sda5       197551368   302166584    52307608+  83  Linux
/dev/sda6       302166648   306712979     2273166   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 400.0 GB, 400088456704 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422767 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x167e35b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   781417664   390708801    7  HPFS/NTFS

```

---

### Post by bumanie on 2008-09-27
You haven't installed ubuntu onto a separate hard drive - ubuntu has ended up on your first/primary hard drive and looks as though it has been installed twice. Windows is still there as you know, but you have two main ext3 partitions and two swap partitions. You don't really need two installations that are the same. Which version of windows do you have?

---

### Post by WWSmith36 on 2008-09-27
From this output I see you have 2 hard drives.  First hard drive have you windows on the second partition.  There are also two linux partitions and two linux swap partitions.  I am curious as to where you installed ubuntu.

Please copy and paste the output below the line
## ## End Default Options ##
of

```
cat /boot/grub/menu.lst
```

---

### Post by Enigma52809 on 2008-09-27
It says that there is no such file or directory. 
I think the other linux install is from a previous attempt at dual booting. I think I'll just wait a bit until I have more time and then just wipe the entire hard drive and install windows then reinstall a fresh copy of ubuntu.
Thanks for the help!

---

