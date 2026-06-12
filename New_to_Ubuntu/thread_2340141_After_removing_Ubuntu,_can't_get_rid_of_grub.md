---
title: "After removing Ubuntu, can't get rid of grub"
date: 2016-10-16
forum: New to Ubuntu
---

### Post by MadleSs on 2016-10-16
Hi guys, 
Yesterday I removed Ubuntu from dualboot with Win10 by formating the drive it was on, I did insert windows installation media and from command line I entered boot bootrec.exe /fixmbr, everything went well, but after rebooting I ended up in grub command line. Finally I tried running dual boot repair tool which helped me boot into windows directly, but when I open boot menu I still see these records. 

[http://imgur.com/MYuwyki](http://imgur.com/MYuwyki)

So is the grub still present in my computer? If so could you help me how to get rid of it? I will be installing the ubuntu again alongside windows 10 don't know if it will fix this by itself. 

Thank you

---

### Post by kc1di on 2016-10-16
if you reinstall ubuntu it should re-write the MBR and fix the problem.

---

### Post by MadleSs on 2016-10-16
That's what I wanted to know :) Thank you!

---

### Post by kc1di on 2016-10-16
see if it works if there is a problem, you can use Boot-repair to fix many boot problems. 
you can get it here:
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by oldfred on 2016-10-16
That looks like an UEFI boot menu?
Then you just select to boot Windows in UEFI boot menu and use it as default.

If you want to totally remove Ubuntu/grub, you need to first remove /EFI/ubuntu folder in ESP - efi system partition and the use efibootmgr to delete entries in UEFI. Do not know how to do from Windows.
[https://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](https://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)
       [http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)

---

