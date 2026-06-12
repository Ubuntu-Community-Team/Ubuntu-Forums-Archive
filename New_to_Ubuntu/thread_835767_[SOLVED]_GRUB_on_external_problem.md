---
title: "[SOLVED] GRUB on external problem"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by scasplte2 on 2008-06-20
Alright, I know there is a way to do this and I have tried searching these forums and google for an answer but nothing seems to have worked. 

My problem is that I installed Ubuntu 8.04 64bit on an external drive and cannot boot my computer without the external drive being plugged in. The external drive is a 40GB IDE hard drive and I have a 160GB internal SATA drive with Windows Vista SP1. My BIOS does have the ability to boot from USB devices boot there is no option to set either drive as slave as suggested in some forums. I have tried rewriting the windows MBR with Super Grub Disk but this resulted in me being unable to boot Ubuntu until I restored GRUB with SGD. I simply cannot figure out how to get GRUB onto my internal drive so that I can boot without the external drive plugged in.

Every other forum has asked for the result of:
```
sudo fdsik -l
```

so here it is
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
129 heads, 4 sectors/track, 605778 cylinders
Units = cylinders of 516 * 512 = 264192 bytes
Disk identifier: 0xb21d0910

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               4       27787     7168000    c  W95 FAT32 (LBA)
/dev/sda2   *       27787      330673    78144512    7  HPFS/NTFS
/dev/sda3          330673      605772    70975488    f  W95 Ext'd (LBA)
/dev/sda5          330677      605772    70974464    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000128de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4659    37423386   83  Linux
/dev/sdb2            4660        4864     1646662+   5  Extended
/dev/sdb5            4660        4864     1646631   82  Linux swap / Solaris
```


/dev/sda2 is my main Vista partition and 
/dev/sdb1 is my main Ubuntu partition.

Also GRUB says that the 160GB drive is (HD1,0)
and the 40GB drive is (HD0,1)

If anyone can help, point in the direction of another post with a solution, or needs more information I would greatly appreciate it.

---

### Post by logos34 on 2008-06-20
> **scasplte2 said:**
> My BIOS does have the ability to boot from USB devices boot there is no option to set either drive as slave as suggested in some forums. 

you need to set the usb drive first in the hard disk boot order (not to be confused with the device boot order), ahead of the internal sata disk.

Restore windows bootoader to the internal disk MBR.

[Write grub to the external drive's mbr]("http://ubuntuforums.org/showthread.php?t=224351").  The only diff is that the find command may output root as '(hd1,?)', so you'd do 'setup (hd1)'

Mount root and make sure **/boot/grub/menu.lst** has '(hd**0**,?)' for the 'root' and 'groot' lines.  (The reason: as soon as you change the Bios order to boot ubuntu, the external becomes (hd0)

---

### Post by scasplte2 on 2008-06-22
Thank you very much. Your suggestion worked beautifully

---

### Post by logos34 on 2008-06-22
glad I could help

---

