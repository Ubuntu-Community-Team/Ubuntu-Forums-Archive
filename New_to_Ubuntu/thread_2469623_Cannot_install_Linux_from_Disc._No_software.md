---
title: "Cannot install Linux from Disc. No software"
date: 2021-12-04
forum: New to Ubuntu
---

### Post by trevord734 on 2021-12-04
I place cd in player, it whirls and then nothing, except icon on Desktop, right clicking gives option to open with "autorun prompt"  This gives error report "Cannot find autorun program"         HELP

---

### Post by T6&amp;sfpER35% on 2021-12-04
how did you you create this CD ? where did you get whatever you put on CD ?
[https://www.howtogeek.com/693588/how-to-install-linux/]("https://www.howtogeek.com/693588/how-to-install-linux/")

---

### Post by trevord734 on 2021-12-04
The disk is a commercial install disk "Your Complete LINUX Starter Kit"

---

### Post by T6&amp;sfpER35% on 2021-12-04
is your BIOS set to boot from disk 1st ?

---

### Post by Frogs Hair on 2021-12-04
Can you link where the disk is from and is it a CD or DVD ?

---

### Post by oldfred on 2021-12-04
Autorun is trying to run something on DVD while booted in a system.
But to install Ubuntu, you have to boot from UEFI/BIOS not try to run a program.

[https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview](https://ubuntu.com/tutorials/install-ubuntu-desktop#1-overview)

You do need to know if system is UEFI or BIOS/CSM/Legacy.
Most systems since 2012 are UEFI with gpt partitioning as Microsoft has required vendors to install in UEFI mode since 2012 when Windows 8 was released.

---

### Post by grahammechanical on 2021-12-04
In the old, old days Windows would look for an autorun.exe file on a CD and then run it. The autorun.exe file would then load a Windows program (exe file) that was on the CD. That was how Windows would allow users to run programs from CD without installing them. Very small hard drives in those days.

Linux is not a Windows program. It cannot be run by any version of Windows. I still have a version of Linux on a floppy disc that I would use as a rescue disk. Things have moved on and now it is just a curiosity. It was command line only.

To run Linux whether from a floppy disc, a CD or a DVD we need to boot from the particular media. Such media would never have a Windows compatible autorun.exe file.

I obtained my first CDs of Linux as free gifts when I purchased a computer magazine. In the past it was not unknown for a publication to give away a CD with multiple distributions on it that we could try. We still had to boot from it.

It has been a long time since the Ubuntu distribution of Linux could fit on a CD. So, I wonder how old this CD is and what distribution of Linux it contains? We should be told the version of Windows on that machine and be given the hardware specification of the machine.

Regards

---

### Post by trevord734 on 2021-12-04
There are 2 options listed EFI Boot Devices and ubuntu (Samsung SSD 980 250GB) 
 Instructions are to use the up or down keys to select which option but I cannot get it to select the EFI Boot.
The Bios name is "insyde"  if that is of any use.

---

### Post by GhX6GZMB on 2021-12-04
The installation DVD needs to _boot_ your machine.
This means, that you first need to power up your machine and press "F10", "F2", "Esc" or whatever your brand of PC needs to get into the BIOS.
Then you select your DVD drive as first boot device.
Then you restart your PC (with the DVD in the drive) and see what happens.

---

### Post by trevord734 on 2021-12-04
Thanks for your help. I have found a workaround by downloading Linux.iso and creating an install usb. All works fine in Linux, don't know whats wrong with Ubuntu, installed it twice.after checking the hash
Thanks again

---

