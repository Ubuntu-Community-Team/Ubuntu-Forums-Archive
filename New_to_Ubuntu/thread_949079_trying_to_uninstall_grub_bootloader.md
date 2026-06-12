---
title: "trying to uninstall grub bootloader"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by walmz on 2008-10-15
so im trying to uninstall the grub boot loader because its on my moms computer and she needs that and doesn't wont ubuntu. so im wondering how do i go about doing this and go back to windows xp bootloader im a noob, and i don't have the live cd for windows xp, and the unbuntu file is on my external hard drive, ive already tried to unistall it but the grub bootloader is still there. HELP

---

### Post by maddog39 on 2008-10-15
Theres really no reason why you could keep grub there and just select windows every time you booted up the machine. However, you have two choices, reinstall windows, or launch the windows install CD and get to the repair prompt. Enter the commands fixboot and fixmbr (as far as I know) and that will restore the windows bootloader.

---

### Post by louieb on 2008-10-15
Some of us (like me) have to learn the hard way you don't uninstall GRUB you replace it.  The easiest way is with the XP install CD. But there are other disks on the net  that can make the computer boot windows.
[IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by eagle416 on 2009-01-05
your files are safe as long as you don't do a format or restore.  all you're doing is rewriting the MBR.

Instructions here:

[http://www.techzonez.com/forums/archive/index.php/t-3975.html]("http://www.techzonez.com/forums/archive/index.php/t-3975.html")

---

