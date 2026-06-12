---
title: "Completely Remove Ubuntu"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by sijoco on 2011-09-22
Hi All,
I put Ubuntu 11.04 on the GF's laptop about 6 months ago (it was a complete overwrite of XP) and she's now decided she want's XP back :confused:

I have the original XP disk and a bootable USB stick but each time l select the Windows USB/Disk from the list in Grub (1.99) - Windows NT/2000/XP (loader) (on /dev/sdb1) it says:

Error No such Device: 5385-467c
Error Device Format "dev/sbd,msdos1" invalid: must be (f|h)dN, with 0 <= N < 128
Error No Such Disk

I end up going round in circles ](*,)

I still have Ubuntu on my pc so l'm not letting the side down but l'm not savvy enough to switch the GF's laptop back without help.

Thanks in Advance

---

### Post by TeoBigusGeekus on 2011-09-22
The grub entry must be a remnant of the time when your gf had still windows on her pc.
You have to go into bios, find the boot order selection, select cd as the first boot device and then boot from the winxp cd.

---

### Post by sijoco on 2011-09-22
Thanks for the quick reply Teo.

FIXED - I ran it from the Flash Drive selecting Run from USB Hard Drive on the Startup. It's now formating the partition.

---

### Post by TeoBigusGeekus on 2011-09-22
Good to know; don't forget to mark the thread as solved.

---

