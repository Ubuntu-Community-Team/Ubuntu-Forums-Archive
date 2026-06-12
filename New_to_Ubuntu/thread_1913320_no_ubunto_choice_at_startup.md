---
title: "no ubunto choice at startup"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by traditore on 2012-01-22
I have used Ubuntu before with my previous computers, but recently one died and I bought an Asus EeePC with windows 7 installed. I tried to install Ubuntu 11.10 and the installation process showed everything OK, but it starts with windows and doesn't give me the option to choose ubuntu at the start. I have re-installed it and it has not been solved. I didn't create a swap partition for ubuntu as it said that it was only for older computers, so I guess that shouldn't be the problem. Can you give me some advice on it please?

Thanks

---

### Post by TeoBigusGeekus on 2012-01-22
It depends on where the installer installed grub.
If you installed ubuntu on a separate hard drive, chances are that grub was installed there.
If that is the case, changing the boot hd from bios could/should solve the problem.

---

### Post by kc1di on 2012-01-22
> **traditore said:**
> I have used Ubuntu before with my previous computers, but recently one died and I bought an Asus EeePC with windows 7 installed. I tried to install Ubuntu 11.10 and the installation process showed everything OK, but it starts with windows and doesn't give me the option to choose ubuntu at the start. I have re-installed it and it has not been solved. I didn't create a swap partition for ubuntu as it said that it was only for older computers, so I guess that shouldn't be the problem. Can you give me some advice on it please?

Thanks

Someone has already answered the boot problem, reinstall grub to MBR should also work. 
you still need swap partition if you want your suspend or hibernate the machine.

---

### Post by traditore on 2012-01-22
I am sorry I am not familiar with the vocabulary. How do I install grub in MBR (and what is MBR)?
I have tried the bios but it only gives me the option SATA hd, only when a USB is inserted do I get another option.

---

### Post by kc1di on 2012-01-22
> **traditore said:**
> I am sorry I am not familiar with the vocabulary. How do I install grub in MBR (and what is MBR)?
I have tried the bios but it only gives me the option SATA hd, only when a USB is inserted do I get another option.

MBR stands for Master Boot Record and it's the spot on you primary harddrive that is used by the bios to lunch what ever boot manager you have installed in it. So if you did not originally install the grub boot manager there your bios can not find it and you have to boot using another method.  IE a floppy of live cd or dvd etc. 

To install Grub to the mbr follow these instructions:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Good luck 
dave

---

