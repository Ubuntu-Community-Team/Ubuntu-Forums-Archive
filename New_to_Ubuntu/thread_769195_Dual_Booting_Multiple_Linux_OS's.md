---
title: "Dual Booting Multiple Linux OS's"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by N1N31NCHN41L5 on 2008-04-26
Ok so I'm still a new and a total Linux nerd now. I have a laptop ive turned into a desktop and ALL that goes on it is LINUX. Where I learn by trial and eror. Well i want to multi boot it, but not M$ and linux - i want more than one Linux distro. Currently I have Ubuntu Gutsy Gibbon running happy on primary partition, have a 512MB Linux swap (only 256RAM) and have installed WNOP on to a (logical?? partition) on the extended partition. i am at the screen where it asks about grub - i dont want to boot form usb as ubuntu has grub already and i DEFINATELY dont want to install a new grub. What do i do at this screen.????????????????

---

### Post by markharding557 on 2008-04-26
go ahead and let it reinstall grub this should detect all existing o/s the only exception i think is fedora which apparently can't see 
other linux's

---

### Post by N1N31NCHN41L5 on 2008-04-26
> **markharding557 said:**
> go ahead and let it reinstall grub this should detect all existing o/s the only exception i think is fedora which apparently can't see 
other linux's

ARE YOU SURE - when i did that yesterday with Muppy008 it tore up ubuntu grub. If you say yes - i'll go for it - but if it tears up both os's will u be here to help fix grub????

I have BOTH OS's HOOKED UP and dont want to lose my computer totally......

---

### Post by markharding557 on 2008-05-03
yes i am sure the new grub installation should detect any existing installations and if worst did happen you can reinstall grub using an ubuntu live cd

---

### Post by louieb on 2008-05-03
When I have multiple Linux OSes on a PC. I let each have its own copy of GRUB. 
Why? Its the easiest no hassle way to do it.  One Linux distro get the GRUB IPL code put in the Hard drives MBR. 
Then when I install the 2nd or 3rd Linux distribution its GRUB IPL code goes in the the boot sector of its / (root) partition. 
 
Then the 1st Linux distribution gets a configfile entry that looks something like this
 
```
 
title 2nd Linux distro
configfile (hd0,3)/boot/grub/menu.lst

```More info see the GRUB page in the **Dual Boot** link in my signature.

---

### Post by lswest on 2008-05-03
yeah, i think the new GRUB should recognized the old OS, and if not, there's a how-to in my sig (3rd line) on restoring bootloaders.

---

