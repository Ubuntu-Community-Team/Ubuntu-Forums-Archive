---
title: "Boot menu disappeared"
date: 2013-09-20
forum: New to Ubuntu
---

### Post by semion2 on 2013-09-20
hi!

before installing ubuntu on my desktop i had windows xp sp3 installed. in boot menu i could choose either to boot windows or ubuntu. now i've reinstalled windows, and boot menu disappeared, windows starts automatically. how can i revert the boot menu?

thanks!

---

### Post by GwL3eNC on 2013-09-20
Hi,

boot from the ubuntu dvd and choose try ubuntu. Make internet availeable and install grub customizer 

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

Start grub customizer as sudo and use the install grub to mbr option
Also you can do it without this tool using the terminal. I think it's the
grub-install command but im not shure. take a look at man grub-install.

---

### Post by deadflowr on 2013-09-20
[Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by Elfy on 2013-09-20
*Thread moved to **Absolute Beginners Section**.*

---

### Post by grahammechanical on 2013-09-20
I have never done this from a live session terminal but the correct command is

```
sudo grub-install /dev/sda
```

That is if there is only one hard disk (sda) in the machine.

Regards.

---

### Post by Jonathan Precise on 2013-09-20
Please know which drive it is. If it is the only HDD in the PC, ignore this warning.

Try:

```
sudo grub-install /dev/sda
```

where sda is your drive. Check in GParted first (the drive that contains Win XP). Make sure not to do anything other than check, or YOUR INFORMATION MIGHT BE LOST!!!!

---

### Post by semion2 on 2013-09-22
Thanks! Problem is solved!
> **deadflowr said:**
> [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

