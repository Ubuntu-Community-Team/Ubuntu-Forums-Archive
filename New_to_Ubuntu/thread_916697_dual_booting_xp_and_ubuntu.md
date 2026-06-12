---
title: "dual booting xp and ubuntu"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by antgul338 on 2008-09-11
my pc has ubuntu installed already.....is there a way to resize partitions and install windows after??? or do i have to install xp then ubuntu again??? thx

---

### Post by Nepherte on 2008-09-11
You could try to resize it with gparted. You can find it in the repositories. You will have to unmount the disk first though, so if you'd like to resize / you will need a gparted live cd.

---

### Post by Mr-Imacdaddy on 2008-09-11
yup windows xp does not like to share! so you have install windows first than ubuntu. i started out with laptop 5 days ago. now its every where in my house. my laoptop, both my imac's 20" flat panel and 24" flat panel. workes great on windows laptop and imac's.not bad for just 5 days into this. now making a linux box, thats why im here.. but good luck they also make a program called Parallels Desktop 3.0 for Mac. Parallels Desktop 3.0 allows you to run Mac OS X, Windows, OS/2, Solaris and any version of Linux simultaneously on your Intel-powered Mac without rebooting. they also make Parallels Workstation 2.2 for Windows & Linux. Use Windows? Like Linux? Have it all on a single PC.
Parallels Workstation is an easy-to-use, easy-on-the-pocket solution that lets you run Windows, Linux and more side-by-side on a single PC without rebooting.

good luck with either way you choose ....

---

### Post by muteXe on 2008-09-11
Windows will overwrite your grub though with its own mbr, so you need to "reinstall" that maybe with the supergrub disk.

Do you have lots of data on your ubuntu?  I'd be tempted to install xp on the whole of the disk, then re-install ubuntu, partitioning as part of the ubuntu installation process.

---

### Post by antgul338 on 2008-09-11
no i have all my data on a seagate 500gb usb but all the settings and programs ive installed and unistalled.....so much work!

---

### Post by kansasnoob on 2008-09-11
You can do it:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

I followed that guide to do my first dual boot and it worked fine.

It is easier to install Linux after Windows because you don't have to do the fiddling with GRUB, but it's not that hard to do.

---

### Post by talking Llama on 2008-09-11
I dual booted windows XP and Ubuntu but my Windows partition was too small for what I needed so I re-sized it with the Live CD and now Windows won't boot, it just brings me to the Windows XP screen, can anyone help?

---

