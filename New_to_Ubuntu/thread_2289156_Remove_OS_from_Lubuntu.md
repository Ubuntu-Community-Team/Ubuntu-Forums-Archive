---
title: "Remove OS from Lubuntu"
date: 2015-08-01
forum: New to Ubuntu
---

### Post by guny on 2015-08-01
I want to remove my Windows OS
I have this


Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0655eeae


Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *           63 235575905 235575843 112.3G  7 HPFS/NTFS/exFAT
/dev/sda2       293025600 312576704  19551105   9.3G 12 Compaq diagnostics
/dev/sda3       235577342 293023743  57446402  27.4G  5 Extended
/dev/sda5       235577344 290949119  55371776  26.4G 83 Linux
/dev/sda6       290951168 293023743   2072576  1012M 82 Linux swap / Solaris


Partition table entries are not in disk order.

---

### Post by yancek on 2015-08-01
If you are sure you want to do this, the standard method is to simply format the partition or partitions using a Linux filesystem such as ext4.  You can use GParted for this which should be on the Lubuntu installation medium or it can be download and put on a CD or flash drive and booted that way.

---

### Post by NathanRodriguez on 2015-08-01
NTFS partitions are usable under Ubuntu Linux, you don't even have to reformat it as you may have some stuff stored there.

---

### Post by sandyd on 2015-08-02
Try running
```

sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub
```
to hide Windows.

You can then use the Windows partition for whatever you want.

Otherwise, copy needed files off Windows partition, unmount it and reformat using Gparted.

If your using LVM, you can add the space back by creating a physical volume and adding it to your volume group.

---

