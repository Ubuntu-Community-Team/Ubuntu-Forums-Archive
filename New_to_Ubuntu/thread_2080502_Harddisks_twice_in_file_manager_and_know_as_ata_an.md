---
title: "Harddisks twice in file manager and know as ata and scsi devices."
date: 2012-11-04
forum: New to Ubuntu
---

### Post by gabbajoe on 2012-11-04
Hi,

I update from xubuntu 10.04 to 12.10 and and most everything works flawless but I had the strange behavior that every partition of my hard drives are shown twice as Icons in Thunar and on the Desktop. So I was thinking ok maybe it has to do with the update from 10.04 to 12.10 but after a fresh installation it is still the same.
Are you can see on the pictures:
In Thunar:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=226664&stc=1&d=1352027589[/IMG]
On the Desktop:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=226665&stc=1&d=1352028206[/IMG]

I check now why this happens and I think this it is caused by this strange thing that my hard disk as know to the system as SCIS and ATA devices.
out put of list disk by id:
```

gabba@gromsh:~$ ls -l /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root  9 Nov  4 10:51 ata-HL-DT-ST_DVDRAM_GH24NS90_KQLC5CE2443 -> ../../sr0
lrwxrwxrwx 1 root root  9 Nov  4 10:51 ata-M4-CT128M4SSD1_000000001229091123FA -> ../../sda
lrwxrwxrwx 1 root root 10 Nov  4 10:51 ata-M4-CT128M4SSD1_000000001229091123FA-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov  4 10:51 ata-M4-CT128M4SSD1_000000001229091123FA-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov  4 10:51 ata-M4-CT128M4SSD1_000000001229091123FA-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Nov  4 10:51 ata-M4-CT128M4SSD1_000000001229091123FA-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Nov  4 10:51 ata-SAMSUNG_HD321KJ_S0MQJDPP610556 -> ../../sdc
lrwxrwxrwx 1 root root 10 Nov  4 10:51 ata-SAMSUNG_HD321KJ_S0MQJDPP610556-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Nov  4 10:51 ata-SAMSUNG_HD502IJ_S1PZJ1BQ502293 -> ../../sdd
lrwxrwxrwx 1 root root 10 Nov  4 10:51 ata-SAMSUNG_HD502IJ_S1PZJ1BQ502293-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Nov  4 10:51 ata-SAMSUNG_HD642JJ_S1AFJDWS401687 -> ../../sdb
lrwxrwxrwx 1 root root 10 Nov  4 10:51 ata-SAMSUNG_HD642JJ_S1AFJDWS401687-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Nov  4 10:51 ata-SAMSUNG_HD642JJ_S1AFJDWS401687-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Nov  4 10:51 ata-SAMSUNG_HD642JJ_S1AFJDWS401687-part3 -> ../../sdb3
lrwxrwxrwx 1 root root  9 Nov  4 10:51 scsi-SATA_M4-CT128M4SSD1_000000001229091123FA -> ../../sda
lrwxrwxrwx 1 root root 10 Nov  4 10:51 scsi-SATA_M4-CT128M4SSD1_000000001229091123FA-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov  4 10:51 scsi-SATA_M4-CT128M4SSD1_000000001229091123FA-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov  4 10:51 scsi-SATA_M4-CT128M4SSD1_000000001229091123FA-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Nov  4 10:51 scsi-SATA_M4-CT128M4SSD1_000000001229091123FA-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 Nov  4 10:51 scsi-SATA_SAMSUNG_HD321KJS0MQJDPP610556 -> ../../sdc
lrwxrwxrwx 1 root root 10 Nov  4 10:51 scsi-SATA_SAMSUNG_HD321KJS0MQJDPP610556-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Nov  4 10:51 scsi-SATA_SAMSUNG_HD502IJS1PZJ1BQ502293 -> ../../sdd
lrwxrwxrwx 1 root root 10 Nov  4 10:51 scsi-SATA_SAMSUNG_HD502IJS1PZJ1BQ502293-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Nov  4 10:51 scsi-SATA_SAMSUNG_HD642JJS1AFJDWS401687 -> ../../sdb
lrwxrwxrwx 1 root root 10 Nov  4 10:51 scsi-SATA_SAMSUNG_HD642JJS1AFJDWS401687-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Nov  4 10:51 scsi-SATA_SAMSUNG_HD642JJS1AFJDWS401687-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Nov  4 10:51 scsi-SATA_SAMSUNG_HD642JJS1AFJDWS401687-part3 -> ../../sdb3
lrwxrwxrwx 1 root root  9 Nov  4 10:51 wwn-0x50000f0007052239 -> ../../sdd
lrwxrwxrwx 1 root root 10 Nov  4 10:51 wwn-0x50000f0007052239-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 Nov  4 10:51 wwn-0x50000f00db610556 -> ../../sdc
lrwxrwxrwx 1 root root 10 Nov  4 10:51 wwn-0x50000f00db610556-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Nov  4 10:51 wwn-0x5001480000000000 -> ../../sr0
lrwxrwxrwx 1 root root  9 Nov  4 10:51 wwn-0x50024e900148d1ff -> ../../sdb
lrwxrwxrwx 1 root root 10 Nov  4 10:51 wwn-0x50024e900148d1ff-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Nov  4 10:51 wwn-0x50024e900148d1ff-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Nov  4 10:51 wwn-0x50024e900148d1ff-part3 -> ../../sdb3
lrwxrwxrwx 1 root root  9 Nov  4 10:51 wwn-0x500a0751091123fa -> ../../sda
lrwxrwxrwx 1 root root 10 Nov  4 10:51 wwn-0x500a0751091123fa-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov  4 10:51 wwn-0x500a0751091123fa-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Nov  4 10:51 wwn-0x500a0751091123fa-part3 -> ../../sda3
lrwxrwxrwx 1 root root 10 Nov  4 10:51 wwn-0x500a0751091123fa-part5 -> ../../sda5


```

To get ride of the duplicated icons I found this: [http://askubuntu.com/questions/207296/after-upgrade-to-xubuntu-12-10-i-have-2-mount-points-for-each-partition](http://askubuntu.com/questions/207296/after-upgrade-to-xubuntu-12-10-i-have-2-mount-points-for-each-partition) it works for me.

I also use a udev rule to hide partitions for linux that I use only with my windows as described on this page [http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/](http://www.worldofnubcraft.com/969/hide-your-disks-or-partitions-from-nautilus/)

Can I use also a udev rule to prevent my xubuntu to know my disk as ata devices, or I set something horrible wrong in my bios and this cause this issue?

The question for me is why my disk are now known as scsi and ata devices and how can I disable (x)ubuntu to identify my disk as scsi and ata devices?

Thanks for reading and maybe found a solution for me :)

Best regards,
Gabbajoe

---

### Post by verymadpip on 2012-11-04
Hi gabbajoe,
You are not alone & I think this is already being tackled somewhere up the line:
[http://ubuntuforums.org/showthread.php?t=2079661](http://ubuntuforums.org/showthread.php?t=2079661)

---

