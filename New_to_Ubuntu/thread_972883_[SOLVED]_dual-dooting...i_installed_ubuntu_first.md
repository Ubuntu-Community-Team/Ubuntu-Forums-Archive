---
title: "[SOLVED] dual-dooting...i installed ubuntu first"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by sharkbite1414 on 2008-11-06
OK I installed ubuntu first (yeh i know everyone said to install windows frist) because i wanted to be rid of windows. Then i found out i can't play crysis etc. to well so i reinstalled windows. Now how do i get the grub menu back so i can dual-boot properly. Also because windows can't read/write ext3 i am running Parted Magic 2.2 from RAM.

P.S.
My OS's are
ubuntu 8.10
windows XP Pro

thanks!:guitar:

---

### Post by ponto18 on 2008-11-06
Check this out:
[http://ranacse05.wordpress.com/2008/01/12/grub-recovery-after-installing-windows-xp/](http://ranacse05.wordpress.com/2008/01/12/grub-recovery-after-installing-windows-xp/)

Hope that helps...

---

### Post by sisco311 on 2008-11-06
> **sharkbite1414 said:**
>  Also because windows can't read/write ext3 i am running Parted Magic 2.2 from RAM.

you can install the ext2/ext3 driver in windows:
[http://www.fs-driver.org/]("http://www.fs-driver.org/")

---

### Post by sharkbite1414 on 2008-11-06
> **ponto18 said:**
> Check this out:
[http://ranacse05.wordpress.com/2008/01/12/grub-recovery-after-installing-windows-xp/](http://ranacse05.wordpress.com/2008/01/12/grub-recovery-after-installing-windows-xp/)

Hope that helps...

O.K. I've got the grub menu back and i can boot into ubuntu but now there is no boot into windows option in the grub menu.:confused:

---

### Post by sisco311 on 2008-11-06
open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
sudo fdisk -l
```

---

### Post by sharkbite1414 on 2008-11-06
> **sisco311 said:**
> open a terminal (Applications -> Accessories -> Terminal)
and post the output of:
```
sudo fdisk -l
```

O.K. Now what?:confused:

---

### Post by bumanie on 2008-11-06
You need to add a windows entry to /boot/grub/menu.lst and as windows is not the first installed OS, you will probably have to add 'map' commands to that entry also. Before someone can help further you need to post the output of > sudo fdisk -lPut that code into terminal and cut and paste the output to the forum.

---

### Post by sharkbite1414 on 2008-11-06
k the output of 'sudo fdisk' -l is as follows:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008e763

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       39519   317436336   83  Linux
/dev/sda2   *       39520       60051   164923290    7  HPFS/NTFS
/dev/sda3           60052       60801     6024375    5  Extended
/dev/sda5           60052       60801     6024343+  82  Linux swap / Solaris

---

### Post by alienexplorers on 2008-11-06
Have you tried using the SuperGrub Disk.  It can be downloaded from:
[http://www.supergrubdisk.org/]("http://www.supergrubdisk.org/")

Also read this [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") if you need help running the program.

---

### Post by bumanie on 2008-11-06
+1 for reading Herman's grub page.
At the bottom of your /boot/grub/menu.lst you will need to add something like this:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows xp
root        (hd0,1)
savedefault
makeactive
chainloader    +1

To get the list up for editing > gksudo gedit /boot/grub/menu.lstCopy and paste the above to the bottom of the list, reboot and see if it has windows in the grub list - if not you may have to add map commands, but that is usually only necessary when two hard drives are involved, however I have come across situations with installations like yours, where map commands have been necessary. Try this first.

---

### Post by sisco311 on 2008-11-06
> **sharkbite1414 said:**
> k the output of 'sudo fdisk' -l is as follows:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008e763

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       39519   317436336   83  Linux
/dev/sda2   *       39520       60051   164923290    7  HPFS/NTFS
/dev/sda3           60052       60801     6024375    5  Extended
/dev/sda5           60052       60801     6024343+  82  Linux swap / Solaris

edit the menu.lst file:
```
gksu gedit /boot/grub/menu.lst
```

and add this to the buttom of the file:
> title         Windows
root          (hd0,1)
savedefault
makeactive
chainloader   +1


---

### Post by sharkbite1414 on 2008-11-06
Thanks everyone, I can boot into both OS now! Thanks again

---

