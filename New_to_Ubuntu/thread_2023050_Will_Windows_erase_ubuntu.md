---
title: "Will Windows erase ubuntu"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-07-11
if I dual-boot...hold on.

I have windows 8 RP installed as my OS. If I dual boot with Win 8 and Ubuntu when I upgrade to the final released of windows 8 will it wipe out my ubuntu paRTITON?

---

### Post by Shadius on 2012-07-11
I'd assume it would depend on what the upgrade options are. I don't know what the upgrade process consists of on Windows, but when upgrading from one version of Ubuntu to another it doesn't erase Windows. Hopefully, it works the same way for Windows.

---

### Post by critin on 2012-07-11
If you download the iso to burn to DVD or USB flash and install to a partition, it shouldn't wipe out another partition.  Back up though, just in case.

---

### Post by GreatDanton on 2012-07-11
No. Windows can't even read Linux format system (ext4). When I was installing windows on my computer, I have few problems, because my hard disk drive was formatted in ext4, and the Windows did not recognize it. As you was advised before, make sure you have backups.

---

### Post by Redblade20XX on 2012-07-11
Probably will just kill your grub! :lolflag:

- Red

---

### Post by Shadius on 2012-07-11
> **GreatDanton said:**
> No. Windows can't even read Linux format system (ext4). When I was installing windows on my computer, I have few problems, because my hard disk drive was formatted in ext4.

I was thinking this as well. I doubt that Windows will even detect that there's another OS on the HDD.

---

### Post by afixane on 2012-07-11
> **Redblade20XX said:**
> Probably will just kill your grub! :lolflag:

- Red

Yes :lolflag:
And it's easy to recover grub, just boot Ubuntu LiveCD and install Boot-Repair :D

---

### Post by Shadius on 2012-07-11
> **afixane said:**
> Yes :lolflag:
And it's easy to recover grub, just boot Ubuntu LiveCD and install Boot-Repair :D

Definitely will kill your GRUB. You can use Boot-Repair or just boot up from the Ubuntu LiveCD and use...
```
sudo update-grub
```
Either method should work. Boot-Repair is the easiest way!

---

### Post by lolpenguin on 2012-07-12
> **GreatDanton said:**
> No. Windows can't even read Linux format system (ext4). When I was installing windows on my computer, I have few problems, because my hard disk drive was formatted in ext4, and the Windows did not recognize it. As you was advised before, make sure you have backups.

It depends on how you upgrade Windows.
Windows doesn't have the drivers to read ext, but if you do a clean install of Windows, you can accidentally wipe your Ubuntu partition.
Windows _will_ overwrite the MBR and kill GRUB, so when dual booting, as a general rule, install Windows first if possible.

---

### Post by TheMTtakeover on 2012-07-12
Gotcha thank guys

---

