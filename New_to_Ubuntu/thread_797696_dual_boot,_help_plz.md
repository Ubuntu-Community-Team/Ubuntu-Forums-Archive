---
title: "dual boot, help plz"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by akkad on 2008-05-17
i have ubuntu 8.04 installed, i installed WinXP as dual boot so i lost the ubuntu boot loader, is there away to reinstall ubuntu boot loader again ??

---

### Post by meierfra. on 2008-05-17
Click on FixGrub in my signature.

---

### Post by akkad on 2008-05-17
fast response, thnx, i applied the commands and now am rebooting, thnx to live cd :) ...

---

### Post by akkad on 2008-05-17
rebooted, i got back grub boot list but the windows xp is not listed??

reason for installing winxp: cuz i command and conquer generals is not working at all in ubuntu :(

---

### Post by akkad on 2008-05-17
rebooted, i got back grub boot list but the windows xp is not listed??

reason for installing winxp: cuz i command and conquer generals is not working at all in ubuntu :(

---

### Post by meierfra. on 2008-05-17
You need to add windows  to the file /boot/grub/menu.lst.  Post the output of 

```
sudo fdisk -l
```
(l is a lowercase L)

and I can tell you exactly what to do.

---

### Post by akkad on 2008-05-17
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x472bfe58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         867     6958080   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             867       16803   128005920   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3   *       16803       18716    15361920    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           18716       19457     5957280    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/sda5           18716       19457     5957248+  82  Linux swap / Solaris

---

### Post by tompickles on 2008-05-17
it wont work in ubuntu as its not made for linux - you could try installign wine to get it to run.... not sure how successful it would be though.

---

### Post by meierfra. on 2008-05-17
Boot into ubuntu. Open "menu.lst" via

```
gksudo gedit /boot/grub/menu.lst
```

Add this to the very end of the file:


title Windows XP
root (hd0,2)
chainloader +1


You might also want to  change

"timeout 3" to "timeout 10"

and

change "hiddenmenu" to "#hiddenmenu"


Save the file and reboot.

---

### Post by akkad on 2008-05-17
meierfra thnx 4 the follow up, my problem solved, thnx ...

---

