---
title: "Triple boot?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by jpeery on 2008-11-21
Hey all, I have a dual boot system, Windows (sadly) and Ubuntu, was wondering how difficult it would be to put a third distro (CentOS) on there?  Can grub handle it?  Anyone can point me to some how-to's?
Thanks,
Jason

---

### Post by indytim on 2008-11-21
No problem (I'm using 4 different Linux versions/distro's + Win2k).  My suggestion is to create your new partition(s) for the new distro **before** installing.  Remember to use a common /swap.  Identify the new partition(s) when you build your new ops.  

Depending upon which distro you select to install, you may have to do some tuning on the bootloader.  I try to stay with a GRUB boot loader across everything that I use.

IndyTim

---

### Post by Miljet on 2008-11-21
This can be easily done. I've found it helpful to make a copy of your existing /boot/grub/menu.lst file before beginning. Anytime you install another distro, it will install its own GRUB. I keep my GRUB on a bootable floppy. Then I can modify the menu.lst to add the new distro.

The best how-to on GRUB that I have found is here:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by jpeery on 2008-11-21
Yeah, I just learned that by mistake, now I can't get back to my main OS (Ubuntu).  Looks like I've got some fooling to do

---

### Post by bodhi.zazen on 2008-11-21
This thread has a number of community suggestions :

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by jpeery on 2008-11-21
> **bodhi.zazen said:**
> This thread has a number of community suggestions :

[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

Ah, that's just what I was looking for, thanks!
JP

---

### Post by bodhi.zazen on 2008-11-21
> **jpeery said:**
> Ah, that's just what I was looking for, thanks!
JP

You are most welcome. Several community members contributed to that thread.

---

