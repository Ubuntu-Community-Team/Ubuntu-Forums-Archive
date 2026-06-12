---
title: "[SOLVED] How do I change the bootloader if it was installed by PCLOS and I can't acce"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by EAL on 2008-10-12
Actually, I can get in PCLOS, but only to the command prompt. 

The computer originally just had Ubuntu installed, then I wanted to try PCLoS.  Long story short I screwed up the display settings so bad I can't even get into gui which I don't care about, I want to use Ubuntu.

The problem is, the default is PCLOS when I reboot and I want to change that to Ubuntu but can't figure out exactly how from Ubuntu or by command line.

Any help would be greatly appreciated. Thanks.

---

### Post by RealG187 on 2008-10-12
Try [this]("http://ubuntuforums.org/showthread.php?p=5856196#post5856196"), except replace Windows with Ubuntu.

Unless it's not a grub thing...

---

### Post by EAL on 2008-10-12
> **RealG187 said:**
> Try [this]("http://ubuntuforums.org/showthread.php?p=5856196#post5856196"), except replace Windows with Ubuntu.

Unless it's not a grub thing...

That would help if grub was running on my Ubuntu install, but it is running on my PCLOS distro, and I can't see it from Ubuntu for some reason.

Thanks for the answer tho.  Once I can get to the file, I'll know what to do.

---

### Post by WWSmith36 on 2008-10-13
If grub is running at all you are in luck.  Grub is a great bootloader and it comes with some nice tools.  Let me know if you can get to any grub menu, if you can we can fix you machine quiet easily.

---

### Post by EAL on 2008-10-13
> **WWSmith36 said:**
> If grub is running at all you are in luck.  Grub is a great bootloader and it comes with some nice tools.  Let me know if you can get to any grub menu, if you can we can fix you machine quiet easily.

I"ll be honest, I can't remember if it is grub or another bootloader. I can get to it only when I reboot the machine, I see it then, but there don't seem to be any configurable options there.

---

### Post by EAL on 2008-10-13
I figured it out. Why do I always miss the obvious?

I just logged in on the command line and 

`nano /boot/grub/menu.lst`

and changed default to the correct number.

Hmpfff...

Thanks for the replies, sorry for the dumb questions.

---

