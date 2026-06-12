---
title: "Uuid vs. /dev/sda"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by streat on 2013-03-29
Im back with another question because everyone has been incredible helpful!

when editing a "/etc/xxx.conf" file i find some functions im adding specifying drives list drive location as "/dev/sda" can i simply replace these with the "UUID = xxxxx" to ensure the drive function is executed if they are moved around?

Thank you!

---

### Post by tgalati4 on 2013-03-29
Yes and no.  Each configuration file is used to set up a framework or layer that provides some function for the operating system.  Older frameworks simply used drive designation--/dev/sda or /dev/hda (for much older kernels).  Newer frameworks switched to UUID (from the *blkid* command) to account for USB external drives, and other swapable devices.  That way the framework will continue to work if the drive gets moved around.  Booting from a USB drive required UUID because everytime a USB drive got plugged in, its device designation changed depending on how many other devices were already plugged in.

So yes, you can change to UUID in a configuration file, but add a comment so you can switch back.  Some older frameworks don't support UUID, so they will break.  In /etc/fstab, you will generally find both, with one set loaded in comments, so you can see how the drives to be mounted are identified.

Let us know what breaks when you convert a configuration file to strictly UUID device naming.

---

### Post by diesch on 2013-03-29
While *UUID = xxxxx *only works in very few cases *you can use /dev/disk/by-uuid/xxxxxxxxx* in almost any config file

---

### Post by streat on 2013-03-29
Thank you for the responses! One quick question, i know that in configuration files the "#" is used to ignore a line, i have also seen a ";" used in a few, does anyone know what this is used for?

---

### Post by tgalati4 on 2013-03-29
It's a comment as well in the beginning of a line, although it is also used as a command separator in C and BASH scripting.  Look at *cat /etc/ltrace.conf*

---

