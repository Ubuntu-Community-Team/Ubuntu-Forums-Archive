---
title: "host pc reboots on trying to install virtual machine"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by bruce247 on 2012-09-01
I'm trying to install windows xp pro (32bit) on a virtual machine using Virtual Box with Ubuntu 12.04 as host. It seems to be working initially as XP goes through its setup procedure, but then my laptop computer reboots. I think my BIOS is up to date to within a few months, so wouldn't haver thought that would be the problem. 

Does anyone know how to get around this?

---

### Post by gordintoronto on 2012-09-01
There's at least one reboot during the installation of XP. Is that when your computer reboots?

Obviously, it should just reboot the virtual machine, but perhaps XP finds a way to reach the hardware.

---

### Post by bruce247 on 2012-09-01
> **gordintoronto said:**
> There's at least one reboot during the installation of XP. Is that when your computer reboots?

Obviously, it should just reboot the virtual machine, but perhaps XP finds a way to reach the hardware.

No, it generally reboots when it states "Windows is starting" just before it allows you to choose file system and partitioning. I've gotten it to go a little further but it keeps restarting the system.

---

### Post by bruce247 on 2012-09-04
Well it seems to be working now. I altered a few setting in VirtualBox but I think what did it was enabling virtualisation support within the BIOS; make sure this is also enabled within the virtual machine settings.:p

---

