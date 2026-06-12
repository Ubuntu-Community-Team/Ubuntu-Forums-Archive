---
title: "[SOLVED] QGrubEditor &amp;amp; Error 13: Invalid or Unsupported Executable Format"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by andrewt522 on 2008-07-24
I have a dual boot, Windows/Ubuntu, situation on my laptop.  Last night, I edited my Windows description to say "Windows XP."  This morning, before I left for work, I tried to power up Windows and received "Error 13: Invalid or Unsupported Executable Format."  As far as I can remember, I only changed the description.  I did this late last night, and it's possible that I clicked something by accident.

Please note, my laptop is at home and I'm at work.  At this time, I'm just looking to see if there's a quick fix.

Thanks in advance.

---

### Post by PmDematagoda on 2008-07-24
Could you please post the output of:-
```
cat /boot/grub/menu.lst
```

---

### Post by andrewt522 on 2008-07-24
It is:

title Windows XP
root (hd0,5)
chainloader +1
savedefault
makeactive

title Ubuntu
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=6670870a-669d-4f86-b8ca-36d5d8530d28 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

---

### Post by andrewt522 on 2008-07-24
Bump.

---

### Post by PmDematagoda on 2008-07-24
The weird thing is that both the roots of Ubuntu and Windows are the same, so the Windows entry must be wrong in that sense. Can you post the output of:-
```
sudo fdisk -l
```

---

### Post by andrewt522 on 2008-07-24
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99ea99ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       19457   125572072+   f  W95 Ext'd (LBA)
/dev/sda5            3825       14873    88751061    7  HPFS/NTFS
/dev/sda6           15360       19457    32917153+  83  Linux
/dev/sda7           14874       15359     3903763+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by andrewt522 on 2008-07-24
Your last post tipped me off and I solved the problem.  I changed my Windows root to 0 (root (hd0,0)) and it worked.  I logged into both Windows and Ubuntu and all is good with the world, at least until the next break.:)

Regardless, thanks for the help!

---

