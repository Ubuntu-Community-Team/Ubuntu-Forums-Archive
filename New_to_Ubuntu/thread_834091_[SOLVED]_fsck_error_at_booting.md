---
title: "[SOLVED] fsck error at booting"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by webofunni on 2008-06-19
Hello,

  Recently i had installed fedora 4 on one of the ext3 partitions and after that i am getting FSCK error when Ubuntu boots, i need to press the "ctrl + D" to resume the booting process. The log file shows the error : 

> root@host:/var/log/fsck# cat checkfs
Log of fsck -C3 -R -A -a 
Thu Jun 19 13:59:04 2008

fsck 1.40.8 (13-Mar-2008)
/dev/sda6: clean, 33683/794624 files, 2743561/3172829 blocks
Lfs: clean, 102/244800 files, 76829/975940 blocks
Music: clean, 965/1224000 files, 1245302/4883752 blocks
fsck.ext3: Unable to resolve 'UUID=a3e1dbca-60ee-4aa4-bf79-60cf6d96075d'
Video: clean, 128/1622016 files, 4474478/6478203 blocks
fsck died with exit status 8

Thu Jun 19 13:59:05 2008
----------------


  I have executed the fsck after login but the error persists on booting. Please help 

Regards,
Unni

---

### Post by Nepherte on 2008-06-19
Looks like a problem with the UUIDs of your disks. It seems one is not correct. Can't think of a solution though.

---

### Post by bumanie on 2008-06-19
If you input > sudo blkid into terminal, it should give you a list of all your hard drive UUID's - print them. You can then look at > cat /boot/grub/menu.lst and see if there is a discrepency with one of the UUID's. If so > gksudo gedit /boot/grub/menu.lst and edit the incorrect UUID to the correct letters/numbers.

---

### Post by philinux on 2008-06-19
Check the uuids in fstab and menu.lst

---

### Post by webofunni on 2008-06-19
Hi All,

  Thanks for the suggestions. I will check and let you know :-) 

  But one question. That was working before installing Fedora. Is there any chance that Fedora installation changed the UUID of that partition ? 

Regards,
Unni

---

### Post by philinux on 2008-06-19
My guess is the discrepancy will be in fstab. Caused by the fedora removal.

---

### Post by webofunni on 2008-06-19
Actaully Fedora replaced the Ubuntu Grub installation with Fedora Grub. So currently system uses the Grub menu.lst from Fedora. Is that a problem

---

### Post by philinux on 2008-06-19
> **webofunni said:**
> Actaully Fedora replaced the Ubuntu Grub installation with Fedora Grub. So currently system uses the Grub menu.lst from Fedora. Is that a problem

Well you could reinstall grub with supergrub or the livecd.

---

### Post by webofunni on 2008-06-24
Hi All,

  Thanks for the suggestions. 

  The issue was with the "UUID" in "/etc/fstab". Replaced the "UUID" in "/etc/fstab" with the UUID got from blkid. 

========================================================
root@host:~# blkid | grep /dev/sda7
/dev/sda7: UUID="9758e919-a56d-44cc-8c7e-a6ab9ff03151" SEC_TYPE="ext2" TYPE="ext3" LABEL="Olinux" 
=========================================================
root@host:~# grep -A 1 /dev/sda7 /etc/fstab 
# /dev/sda7
UUID=9758e919-a56d-44cc-8c7e-a6ab9ff03151 /media/olinux   ext3    relatime        0       2
==========================================================

  It seems that the fedora installation changed the "UUID" of the partition, that caused the issue. 

  Again thanks for all. 

Regards,
Unni

---

