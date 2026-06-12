---
title: "Installed Xp, now no GRUB menu"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by thedon_1 on 2008-10-21
I have ubuntu 8.04 installed and have installed xp on a seperate partition.

I now no longer get the option to load ubuntu at the start.

Do you need to re install grub? How do i do this?

Thanks

---

### Post by mkrahmeh on 2008-10-21
i think coz windows' boot loader is taking charge of the boot sector on your HDD..which will not recognize your linux file system..i cant tell what exactly to do but i recommend always to install linux after windows..maybe downloading grub again would solve the problem, try from a live cd or smthn

---

### Post by garyed on 2008-10-21
Try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) 

You may need to edit your menu.lst file if the you get grub back up & it doesn't boot into your preferred OS.

---

### Post by eternalnewbee on 2008-10-21
> **mkrahmeh said:**
> i think coz windows' boot loader is taking charge of the boot sector on your HDD..which will not recognize your linux file system..i cant tell what exactly to do but i recommend always to install linux after windows..maybe downloading grub again would solve the problem, try from a live cd or smthn

I agree with that.
Note: No more windows since... at least two years.
      Time flies when you're having fun!

---

### Post by binbash on 2008-10-21
Just open with a LIVE cd and re-install grub.

---

