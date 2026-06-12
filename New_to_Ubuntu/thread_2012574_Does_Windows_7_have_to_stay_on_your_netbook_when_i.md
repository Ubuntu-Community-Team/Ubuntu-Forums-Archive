---
title: "Does Windows 7 have to stay on your netbook when installing Ubuntu"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by dylanb2cm on 2012-06-29
Hello Folks,

A friend of mine partitioned my Samsung Netbook (originally with Windows 7 Starter on it).  It now has Ubuntu on it.  Since then I've become a fan of Ubuntu and don't use Windows anymore.  

Do I need to keep Windows 7 on the computer?  

Thanks everyone,

---

### Post by Dlambert on 2012-06-29
No you do not. Not at all.

---

### Post by blackbird34 on 2012-06-29
No, you don't. I didn't, although my wiping Windows was accidental :D
However I would recommend keeping it (or some form of installation media to reinstall, or have a copy of Windows on at least one computer of yours) in case you suddenly find you need Windows for some reason.

---

### Post by mike555 on 2012-06-29
before you format Windows make sure Ubuntu is in fact on a different partition.... if it is a wubi install it is inside Windows ..... also update-grub .

---

### Post by southerngeek on 2012-06-29
> **mike555 said:**
> before you format Windows make sure Ubuntu is in fact on a different partition.... if it is a wubi install it is inside Windows ..... also update-grub .

...and back your files up ;)

---

### Post by mapes12 on 2012-06-30
I'm assuming you have a dual boot configuration and can choose between win and ubu at boot up. If this is correct then what I would do is this:-

- Use a [GParted]("http://gparted.sourceforge.net/") live CD or USB to boot up the machine
- Delete the win partition and reclaim the space for ubu
-Use a [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") CD or USB to boot back into the machine and click the "Repair" button to reconfigure GRUB so that the machine starts up straight into ubu the next time you boot it without any other bootable media in it.

Back up your important stuff before you begin.

---

### Post by afz12 on 2012-06-30
I agree with blackbird34 - Windows does have its uses - for example, reading Windows docx files in Libre-Office doesn't always look that flash. Sometimes you may need to run a program that has no compatible alternative in Linux (I have many of these!) I used to have Win7 on this hP notebook (Pavilion dv6 i5 4-core 6 GB Ram etc) - for some unknown reason Win7 locked up one day and it seemed impossible (at least to me) to fix it. So I just installed Ubuntu 12.04 from a USB stick and rewrote the whole disk. Now I use Virtualbox to run XP on top of Ubuntu 12.04 - it's a bit slower than running native but anything with 4-cores 15 or 17 etc is reasonably practical. I think I'll install Ubuntu 12.10 later this year and set a separate partition aside for XP (I quite like XP)

---

