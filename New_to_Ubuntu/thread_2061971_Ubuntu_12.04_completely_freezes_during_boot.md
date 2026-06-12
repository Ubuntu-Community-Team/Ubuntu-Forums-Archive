---
title: "Ubuntu 12.04 completely freezes during boot"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by tbrann on 2012-09-23
I recently got a laptop with Windows 7 (64 bit) on it . I installed Ubuntu 12.04 (64 bit) on another partition (180 GB partition on a total 300 GB hard drive) It hangs during boot up. It is a complete freeze with an immovable cursor on either a black screen or a purple screen with no icons on it. The computer will not respond to mouse or keyboard, and a hard restart is necessary.  I did install the proprietary drivers, but it didn’t help.
   However, if I boot Windows 7, then restart the computer, Ubuntu will boot up successfully. So evidently there is something left over from the Windows launch that tells Ubuntu how to boot up.
  How can I find out what is going wrong when Ubuntu hangs during boot up, and how do I fix it?


  TOSHIBA Satellite C655D
  Processors:  AMD E-300 APU with Radeon(tm) HD Graphics, 1300 Mhz, 2 Core(s), 2 Logical
  Display:                  AMD Radeon HD 6310 Graphics
  RAM:  2.00 GB
  64-bit Operating System

---

### Post by kabukiM0n0 on 2012-09-23
I don't think I know enough about Linux to answer how it could be fixed. But if you press ```
Control + Alt + F1/6
``` (F7 is the screen you'd log on too' might save you from hard rebooting. log in, then ```
sudo reboot
``` - then I don't know if it will appear as it seems as it fully crashes, but it's worth a shot.

---

### Post by daslinkard on 2012-09-23
> **tbrann said:**
> I recently got a laptop with Windows 7 (64 bit) on it . I installed Ubuntu 12.04 (64 bit) on another partition (180 GB partition on a total 300 GB hard drive) It hangs during boot up. It is a complete freeze with an immovable cursor on either a black screen or a purple screen with no icons on it. The computer will not respond to mouse or keyboard, and a hard restart is necessary.  I did install the proprietary drivers, but it didn’t help.
   However, if I boot Windows 7, then restart the computer, Ubuntu will boot up successfully. So evidently there is something left over from the Windows launch that tells Ubuntu how to boot up.
  How can I find out what is going wrong when Ubuntu hangs during boot up, and how do I fix it?


  TOSHIBA Satellite C655D
  Processors:  AMD E-300 APU with Radeon(tm) HD Graphics, 1300 Mhz, 2 Core(s), 2 Logical
  Display:                  AMD Radeon HD 6310 Graphics
  RAM:  2.00 GB
  64-bit Operating System

This link [here]("http://www.av8n.com/computer/htm/grub-reinstall.htm") may provide you with some insight on how to repair the grub with the master boot record (MBR)....good luck!

---

### Post by Julian Lewis on 2012-09-30
I have installed Ubuntu 12.04 on a Toshiba C655. The alt1c driver freezes when Ubuntu is booted with no wired Ethernet cable in place. This is what I did to fix the problem.
Install Ubuntu AMD64 bit version keeping the Ethernet plugged in, if not the install will freeze. Once up go to
[http://www.linuxfoundation/collabora...networking/alx](http://www.linuxfoundation/collabora...networking/alx)
and download the compat-wireless-2012-05-10-p.tar.bz2 tarball and svave it in your home directory, I put it in a folder named alx. Go there and extact it. Follow the instructions on the website ...
./scripts/driver-select-alx then make and sudo make install.
Then you reboot. When the reboot is over you still see the alt1c driver so we need to get rid of it. Do
sudo rmmod alt1c, then
sudo depmod alx after that your wired connection comes back up, last do a
sudo depmod -a and last but not least
sudo update-initramfs -u

Reboot and it works a treat... It took me a while to figure this out, I hope it will help.

---

### Post by paolachatnoir on 2012-10-01
I have a similar problem with ubuntu, my problem is that installing ubuntu work perfectly but when the ethernet cable is disconnected is ubuntu freezes and i have to shut down and restart, my laptop is a 
TOSHIBA Satellite C645D
Processors: AMD E-300 APU with Radeon(tm) HD Graphics, 1.30 GHz,  Dual-Core
RAM: 2.00 GB
32-bit Operating System

---

### Post by NikTh on 2012-10-01
> **paolachatnoir said:**
>  but when the ethernet cable is disconnected is ubuntu freezes and i have to shut down and restart

Try to boot in to BIOS config page and change the device boot order. Place first the Network. 

Thanks

---

### Post by Joph on 2012-10-06
> **NikTh said:**
> Try to boot in to BIOS config page and change the device boot order. Place first the Network. 

Thanks



Thanks NikTh!! this fixed my boot/ethernet issue...

---

