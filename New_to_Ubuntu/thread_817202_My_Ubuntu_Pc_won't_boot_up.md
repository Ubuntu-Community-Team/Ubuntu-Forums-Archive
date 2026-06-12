---
title: "My Ubuntu Pc won't boot up"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by jjblackfox on 2008-06-03
I keep getting this error: kernel panic - not syncing: Attempted to kill the idle task!

I had Ubuntu installed, but it kept crashing and rebooting and I began to get this message. I tried to re-install Ubuntu, but I got this error message when I tried to install Ubuntu from the disk. I thought that it might have been a problem with the disk so I burned another copy twice and it still didn't work. 

Does anyone know why this is happening?

---

### Post by ibuclaw on 2008-06-03
What type of Hard-Drive do you have? (SATA, PATA, RAID)

Regards
Iain

---

### Post by jjblackfox on 2008-06-03
> **tinivole said:**
> What type of Hard-Drive do you have? (SATA, PATA, RAID)

Regards
Iain
I think it is a PATA

---

### Post by Duck2006 on 2008-06-03
Format the linux partitions with the live cd of gparted or parted magic and then reinstall ubuntu.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by jjblackfox on 2008-06-03
> **Duck2006 said:**
> Format the linux partitions with the live cd of gparted or parted magic and then reinstall ubuntu.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

I used gparted and deleted all my partitions and I tried to install Ubuntu again and it gave me the same error message.

---

### Post by jjblackfox on 2008-06-03
When I try to install Ubuntu, it asks me what language I want to use and I say English, then I hit enter to install Ubuntu. A screen pops up and says "Loading Linux Kernel" Then when it gets to 100%, it gives me the error.

---

### Post by spiderbatdad on 2008-06-03
Did you recently have windows force quit. You need a clean shut down. Also defrag windows (sometimes twice) regardless of whether the system tells you the volume does not need defragging.

Also try using acpi=off from the boot options screen of the live cd: Press f6 then delete the end of the kernel line: --quiet splash, replace with acpi=off

If that works you will need to edit the kernel line in /boot/grub/menu.lst after installation, to make the change permanent.

---

### Post by jjblackfox on 2008-06-03
> **spiderbatdad said:**
> Did you recently have windows force quit. You need a clean shut down. Also defrag windows (sometimes twice) regardless of whether the system tells you the volume does not need defragging.

Also try using acpi=off from the boot options screen of the live cd: Press f6 then delete the end of the kernel line: --quiet splash, replace with acpi=off

If that works you will need to edit the kernel line in /boot/grub/menu.lst after installation, to make the change permanent.

I'm using a text-based installer, not a live cd, and I don't have windows, only ubuntu.

---

### Post by stchman on 2008-06-03
> **jjblackfox said:**
> I keep getting this error: kernel panic - not syncing: Attempted to kill the idle task!

I had Ubuntu installed, but it kept crashing and rebooting and I began to get this message. I tried to re-install Ubuntu, but I got this error message when I tried to install Ubuntu from the disk. I thought that it might have been a problem with the disk so I burned another copy twice and it still didn't work. 

Does anyone know why this is happening?

Sounds like you have a bad hard disk.

---

### Post by jjblackfox on 2008-06-03
> **stchman said:**
> Sounds like you have a bad hard disk.

That isn't what I wanted to hear :(

---

### Post by sTpny on 2008-08-06
I think it's your memory, not your hard drive. Some people have had luck swapping sticks around, or messing with the boot options as suggested in a previous post. Try new memory if you can. A weak power supply can also cause problems.

---

