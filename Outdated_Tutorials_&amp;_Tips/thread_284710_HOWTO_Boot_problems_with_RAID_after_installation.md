---
title: "HOWTO: Boot problems with RAID after installation"
date: 2006-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by mk1970 on 2006-10-26
I installed Ubuntu 6.06.1 and later also 6.10 on a PC with two large SATA disks. I followed [my own instructions](http://www.iki.fi/kuparine/comp/ubuntu/raid.html) with the only difference being that both disks have a small area for Windows and normal ext3 filesystem in the beginning of the disks.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+   7  HPFS/NTFS
/dev/sda2   *        1217        2432     9767520   fd  Linux raid autodetect
/dev/sda3            2433        2554      979965   fd  Linux raid autodetect
/dev/sda4            2555       30515   224596732+  fd  Linux raid autodetect

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+  83  Linux
/dev/sdb2   *        1217        2432     9767520   fd  Linux raid autodetect
/dev/sdb3            2433        2554      979965   fd  Linux raid autodetect
/dev/sdb4            2555       30515   224596732+  fd  Linux raid autodetect
```

There are 3 RAID1 devices (md0 = sda2+sdb2, md1=sda3+sdb3 ja md2=sda4+sdb4) which contain / (md0), swap (md1) and /home (md2).

[COLOR="Red"]The Problem[/COLOR]

When starting the PC for the first time I saw this error message.

```

Error 15: File not found

Press any key to continue...

```

This bug exists at least in Ubuntu 6.06.1 and 6.10 (see this [problem report](https://launchpad.net/distros/ubuntu/+source/grub/+bug/46223)) and it appears to exist whenever the /dev/mdN containing the / filesystem does not use the first physical partition (this assumption is my own).

_The Problem is caused by an invalid "root (hd0,0)" line in /boot/grub/menu.lst_ as seen in the following example. hd0 refers to the first harddrive and it is correct. The zero after comma refers to the first partition but since the first partition type is NTFS (because it contains Windows), the boot loader will not find the files needed to boot Ubuntu.

```
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/md0 ro quiet splash locale=fi_FI
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot
```

[COLOR="Red"]The Solution[/COLOR]
[LIST]
[*]When booting the PC for the first time after the installation, go with the arrow keys to the boot menu entry which you want to start. Usually this is the top-most line.
[*]_Do NOT press Enter!_ Press e to edit the entry.
[*]Go to the line which says **root (hd0,0)** and press e to edit it.
[*]Change the second 0 to the correct number (in the example above the correct number is 1 because the /dev/md0 which contains the / filesystem uses the 2nd physical partition).
[*]Press Enter to access your changes and press b to boot. Your PC should now boot normally.
[*]Open a Terminal (Applications > Accessories > Terminal).
[*]Lauch an editor with **sudo gedit /boot/grub/menu.lst**
[*]Replace all invalid "root (hd0,0)" entries with "root (hd0,1)".
[*]Save the file and reboot. If the changes were made correctly your PC should start now normally.
[/LIST]

Finally it's a good idea to install the boot loader also on the second harddrive so the the PC is able to start even if the first harddrive fails.

```
# sudo grub
grub> device (hd0) /dev/sdb
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
(My original HOWTO about this problem in Finnish is found [here](http://forum.ubuntu-fi.org/index.php?topic=6237.0))

---

