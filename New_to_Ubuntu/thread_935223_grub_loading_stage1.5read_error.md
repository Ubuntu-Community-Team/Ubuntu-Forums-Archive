---
title: "grub loading stage1.5read error"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by cerealkilr on 2008-10-01
when attempting to install ubuntu everything goes smoothly until the reboot.  on restart i get "grub loading stage1.5read error."  from that point after i get an "error 18" message, unless i repeat the cycle.  the rig i built has an intel 3.2ghz cpu, 2gb of ram, and a 640gb sata hdd with an IDE conversion board.  i suppose i should note that i also have an 80gb hdd connected as a slave from which i'm trying to salvage some old information, i have no clue if it even works.  any ideas?  i've kinda been searching around and haven't really found anything that jumps out at me as a solution, mostly stuff that is an attempt to diagnose the problem or stuff that works for some but not for others.  any help would be greatly appreciated.

---

### Post by cariboo on 2008-10-01
I would suggest creating a boot partition, at the start of the hard drive. It only has to be about 200MB. Grub error 18 means:

> Selected cylinder exceeds maximum supported by BIOS. This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).
Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range). 

This may have something to do with the Sata-->Ide converter.

Jim

---

### Post by cerealkilr on 2008-10-02
i'm assuming i'll use gparted to accomplish this.  how do i find the boot partition?  do i have to create one?  also if a bios update is necessary, how do i go about installing the update?  this is my first time dealing with a linux os, but i also just kinda intuited the build process.  not really sure how to proceed.  thanks for your help, again.

---

