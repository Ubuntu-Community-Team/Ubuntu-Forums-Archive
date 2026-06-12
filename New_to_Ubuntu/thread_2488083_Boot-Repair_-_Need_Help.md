---
title: "Boot-Repair - Need Help"
date: 2023-06-22
forum: New to Ubuntu
---

### Post by rawkeeprowing on 2023-06-22
Hello Ubuntu Fam,

I'm need some guidance with a server running ubuntu 16.04 LTS(head-less). I have physical access to the hardware(supermicro). The OS boots up to login screen, but I cannot log-in due to logon-loop. Things tried: Launch Advanced (Recovery Mode) from Advanced Options. Tried launching into systemd.unit=rescue.target environment. 

From Grub command prompt, if i run ls i get the following. (hd0) (hd0,msdos5) (hd0,msdos1). 
ls (hd0,msdos1)
error: no such partition 
ls (hd0,msdos1)/ 
lost+found/ config-4.4.0-62-generic System.map-4.4.0-62-generic abi-4.4.0-62-generic grub/ vmlinuz-4.4.0-62-generic initrd.img-4.4.0.62-generic

ls (hd0,msdos5)/ 
error: unknown filesystem 

My next step is to run the Boot-Repair Tool. Can the Boot-Repair Tool be used on a headless installation of Ubuntu? Any other recommendations/suggestions/ideas?

---

### Post by MAFoElffen on 2023-06-22
> **rawkeeprowing said:**
> Hello Ubuntu Fam,

I'm need some guidance with a server running ubuntu 16.04 LTS(head-less). I have physical access to the hardware(supermicro). The OS boots up to login screen, but I cannot log-in due to logon-loop. Things tried: Launch Advanced (Recovery Mode) from Advanced Options. Tried launching into systemd.unit=rescue.target environment. 

From Grub command prompt, if i run ls i get the following. (hd0) (hd0,msdos5) (hd0,msdos1). 
ls (hd0,msdos1)
error: no such partition 
ls (hd0,msdos1)/ 
lost+found/ config-4.4.0-62-generic System.map-4.4.0-62-generic abi-4.4.0-62-generic grub/ vmlinuz-4.4.0-62-generic initrd.img-4.4.0.62-generic

ls (hd0,msdos5)/ 
error: unknown filesystem 

My next step is to run the Boot-Repair Tool. Can the Boot-Repair Tool be used on a headless installation of Ubuntu? Any other recommendations/suggestions/ideas?

No the boot-repair script cannot be run headless. It is intertwined with GLADE so is GUI...

If you temporarily attach a display to it, to boot from a 22.04 LTS Desktop LiveCD/USB... 

Then what I would suggest, is to install the boot-repair PPA ([https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)), install boot-repair... and run it from the Live Image environment. That way we are sure you are on the latest script.

Either that or download the boot-repair disk, and boot from it...Which would also new a display.

---

### Post by grahammechanical on 2023-06-22
> (hd0,msdos1)

That is the Grub way of saying the first hard drive and the first partition. You are being told this partition does not exist.

> (hd0,msdos5)

That if the Grub way of saying the first hard drive and the fifth partition. You are being told this partition does not have a file system. Something drastically bad has happened to the hard drive in this machine. And yet you say the OS boots to the login screen. How is that possible unless you are bypassing Grub in some way. You are then hitting the same problem Grub encountered. May be.

regards

---

### Post by yancek on 2023-06-23
Has this system ever booted or is it a new install with which you are having this problem?
Have you tried using the live USB of Ubuntu to run a filesystem check on partition 5?

---

### Post by rawkeeprowing on 2023-06-24
Something drastically bad happened to the hard drive for sure. Do you know of any forensic tools I can use to investigate? Where would you look for clues?

---

### Post by rawkeeprowing on 2023-06-24
@yancek, 
 yes, the server was booting fine up until about 1 week ago. It had been running in production for more than 1 year with no issues. Its a Ubiquiti Unifi XG Server(supermicro mobo), that was hosting applications. The OS is Ubunutu 16.04 LTS (headless), and it boots all the way to the login screen. At the login screen, i get logon-loop, regardless of which tty i use.
 
 I will try to run a filesystem check on partition 5 with Live USB. Thanks

---

### Post by Rubi1200 on 2023-06-24
You could try using Testdisk from a liveUSB:
[https://www.cgsecurity.org/wiki/TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

---

