---
title: "install xp"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Shqiptari on 2008-05-03
i have installed on my pc only Ubuntu 8.04 and i want to install another OS "the window$ xp" how can i do this? i have 2 HD . 1 Master with Ubuntu (250 GB) and 1 Slave (80 GB),i've checked vmware,but i want the dual boot if this is possible?!?!? thnx a lot

---

### Post by tamoneya on 2008-05-03
its possible.  You go about a xp installation the same way you did with linux.  Pop the CD in and just make sure to tell it to make its partition in the spare harddrive.  The only problem that you will run into however is that windows will not play nicely with linux and will not add it to the boot loader.  You will have to reinstall GRUB so that you can boot windows.  The easiest way to do this is with super grub.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Shqiptari on 2008-05-03
thnx a lot.now i will give a look at supergrub,however if i fail in this it doesn't matter because i have had window$ last year and i deleted it on my own...so just to proove...!!!

---

### Post by tamoneya on 2008-05-03
just remember that it is always easier to install ubuntu after windows.  So if you fail and cannot get GRUB to work using supergrub a reinstall of ubuntu into the same partition should fix everything up.

---

### Post by cartisdm on 2008-05-03
and as long as you're not worried about losing data it never hurts to just play around with stuff.  you learn the most about what things actually do when you see them for yourself (as opposed to wikis/walkthroughs)

---

### Post by drsox1899 on 2008-05-03
I reinstalled my dual boot WindowsXp partition to clear out all the crap and just use the apps I had to.

Here's what I used to get my Ubuntu 7.10 back :

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

Luck

---

