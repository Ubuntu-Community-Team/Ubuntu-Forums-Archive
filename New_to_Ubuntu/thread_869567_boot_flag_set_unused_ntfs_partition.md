---
title: "boot flag set unused ntfs partition"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by dave.com on 2008-07-24
Thread title pretty much explains it. Windows is installed in ide drive /dev/sda1 (ntfs fs). Sata drive #1 is /dev/sdb and splits an ntfs partition with a fat32. Ubuntu is on Sata drive #2 with a root, boot, home partition and a swap. I uncheck the Sata #1 ntfs boot flag and boot up. 

Windows complains NTLDR is missing and fails to boot. 

My ubuntu partition manager finds a boot flag in the Sata #1 ntfs partition which has no OS (it does have archival stuff) and I unmount the partition, unset the flag and quit.

Launch again and same thing happens, so I ctl+alt+del and go into ubuntu and ya know, the frikkn boot flag has been set again in the 2nd ntfs partition. Windows doesn't even load yet it's setting a boot flag in the wrong partition. 

/boot/grub/menu.lst hasn't changed. Before downloading 'gnash' a flash plugin is the last launch before discovering this. Before that I updated to kernel 2.6.24-20-generic and all seemed well. I got back into Ubuntu, right? Now I am stumped. Anyone know how this is happening and how to correct it?

---

### Post by kansasnoob on 2008-07-24
And you're doing this in Gparted, aka Partition Editor, and you're clicking "apply" and waiting until it's applied?

I'll tell you partitioning is touchy! Even changing "boot" flags.

You can't "apply" changes in a "mounted" partition and have them actually "apply" so maybe you just need to use a Live CD:confused:

---

### Post by logos34 on 2008-07-24
Sounds like your windows stanza in menu.lst is pointing to the ntfs data partition on sdb, and the 'makeactive' option is setting the boot flag each time. 

gksudo gedit /boot/grub/menu.lst
 
If sda is the Bios boot disk, your windows root line should be (hd**0**,0).  If sdb is the boot disk, then (hd**1**,0) + map lines.

---

### Post by dave.com on 2008-07-25
k thank youse guys, I'm on it. brb with the latest headlines ;p

---

### Post by dave.com on 2008-07-25
I went into root user and did a quick update-grub from there. The indications were that, even taking into account the observations you guys have rightly made, that the system settings were okay and I probably did the update-grub incorrectly (from the wrong account).

The update-grub seems to have taken well, a last look inside the partition table showed no flag in /dev/sdb afterward and I quickly looked at bios nothing changed in there.

I soulmarked Logos for a x1 thanks, the info clarified a hazy area for me. Grats ;p

---

