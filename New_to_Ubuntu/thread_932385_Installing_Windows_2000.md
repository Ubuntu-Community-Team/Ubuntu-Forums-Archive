---
title: "Installing Windows 2000"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by sithpigeon on 2008-09-28
Hi,
I currently have a desktop computer with just ubuntu hardy installed and would like to install windows 2000 also. I'm worried that if I just run the windows 2000 installation it will destroy my ubuntu install. Anyone know how I should do this?

---

### Post by kansasnoob on 2008-09-28
Win 2000 is quite similar to XP. I think this should help:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by kansasnoob on 2008-09-28
Oh, I should remind you that it's always a good idea to back up any important data, photos, etc.

I've used that guide and had no problems but bad things can happen. I've had power outages during repartitioning, etc. and things can get hosed very quickly!

---

### Post by Sealbhach on 2008-09-28
cancel.
.

---

### Post by sithpigeon on 2008-09-28
Thanks, will try the tutorial.

---

### Post by sithpigeon on 2008-09-28
I just remembered(well actually saw) that I have a 8 gb slave drive installed with nothing on it and thought it would be better to install it on that. I ran the setup and when I cleared and selected the slave drive it said it still needed to write some files to the master drive(I assume these would be the boot loaders). It can't though, because my master drive uses the linux file system. Should I free up some space on the master drive or could I remove my current master drive and set the slave to the master, then install w2k. After that I could just add it again and tell grub to boot to the slave for w2k. Or, would that not work.

---

