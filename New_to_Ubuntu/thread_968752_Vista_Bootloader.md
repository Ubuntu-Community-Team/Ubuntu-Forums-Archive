---
title: "Vista Bootloader?"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Torak on 2008-11-02
I'm currently running Vista/Ubuntu 8.10 Dual Boot on an external hard drive. Im wondering if I can change back to the normal Vista bootloader over the Gnome so I dont have to have my external Hard drive plugged in when booting. Any ways to accomplish this?

---

### Post by nathansoz on 2008-11-03
Look up EasyBCD on google. Its by neosoft, and pretty self explanitory. You can rewrite the vista bootloader AND add an entry pointing to linux on your external drive.

---

### Post by Torak on 2008-11-06
Thanks but that doesnt seem to help. When I installed Ubuntu(ED) the gnome bootloader always shows up I wonder if i can get the original Vista(HD) bootloader up so that way I do not have to always have my external hard drive plugged in to boot.

---

### Post by kansasnoob on 2008-11-06
You'll need to restore Vista's mbr. If you have no disc you can get one here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You want to "fix boot" and "fix mbr"!

Afterwards you'll need to have your BIOS set to boot from USB before it boots from the internal drive to boot the external Ubuntu drive.

---

