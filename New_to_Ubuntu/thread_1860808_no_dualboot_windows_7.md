---
title: "no dualboot windows 7"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by Il_Dude on 2011-10-15
Yesterday I 've installed ubuntu 11.10 on an other partition as windows 7.
Normally in the start up process I should get an bootmenu but it seems that my computer starts up windows 7 directly.
I would like to have a bootmenu, the first choice should be windows 7 (sorry about that) and the second ubuntu.
Does anybody knows how to do it?
Thank you very much!
Il_dude

---

### Post by garvinrick4 on 2011-10-15
Put a Live Cd in (install cd using Try Ubuntu) and open a terminal (ctrl/alt/t)
and copu and paste this.
```
sudo fdisk -l
``` (lower case L)
and post results here.

---

### Post by Owenoen on 2011-10-15
Hi Dude, I think EasyBCD would help to get the Ubuntu to the second bootmenu, after Windows 7.

---

### Post by Owenoen on 2011-10-15
Oh, forgot telling that EasyBCD should be run in Windows.

---

### Post by Il_Dude on 2011-10-15
Thanks for the quick response.
This is what I get in the terminal

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe556e556

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   105354269    52677103+   7  HPFS/NTFS/exFAT
/dev/sda2       105355262   312560639   103602689    f  W95 Ext'd (LBA)
/dev/sda5       105355264   136605263    15625000   83  Linux
/dev/sda6       143348058   204780554    30716248+   7  HPFS/NTFS/exFAT
/dev/sda7       204780618   312560639    53890011    7  HPFS/NTFS/exFAT
/dev/sda8       136605696   143347711     3371008   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by garvinrick4 on 2011-10-15
### Below is for partition install and not a WUBI install for any new users reading post. If you have WUBI install start a Thread with WUBI in Title line.
@Il_Dude
This will put grub2 into play in mbr (master boot record) so as to boot both Ubuntu and Windows as menu entries.
As long as you have a file system installed in sda5, that is your linux partition. Do not know why grub (boot loader) was not installed in installation process. But below is code to do so.
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
``````
sudo reboot
```This below is a GUI app as to customize grub to your wishes.
[HOWTO: Grub Customizer - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183")

---

### Post by garvinrick4 on 2011-10-15
@Il_Dude
If any further problems need to see the RESULTS.txt file of this script below, gives
you instructions on how to run, if any trouble with just ask. Will make a file called RESULTS.txt
[Boot Info Script | Download Boot Info Script software for free at SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by Il_Dude on 2011-10-17
Thanks for the information&help.
I 've got everything worked out now!
Now starting to explore ubuntu ;-)
Il_dude

---

### Post by garvinrick4 on 2011-10-17
Good and Welcome to the Ubuntu Forums Il_Dude, enjoy your Ubuntu.

---

