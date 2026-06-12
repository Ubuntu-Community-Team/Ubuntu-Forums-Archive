---
title: "Booting off a usb hard disk"
date: 2014-01-21
forum: New to Ubuntu
---

### Post by danny_peck on 2014-01-21
okay so i have an old laptop im trying to refurbish, and the hard drive failed (well, the hard drive broke the SATA connector, so i can neither use the old hard drive or install a new one) so im trying to boot off a usb HDD. when i try and install it on my old laptop however, i get to the "installation type" screen with "device, type, mount point.." ect. but my hard drive isnt there, even though its clearly plugged in and booting. any help? :)
btw, love the layout, if i can get this working my old laptop may become my main laptop, its so purrrty

---

### Post by ibjsb4 on 2014-01-21
Is this what your trying?

[https://help.ubuntu.com/community/Grub2/ISOBoot#Booting_the_ISO](https://help.ubuntu.com/community/Grub2/ISOBoot#Booting_the_ISO)

Or do you have a cd/dvd burned?

---

### Post by danny_peck on 2014-01-22
yes i believe so, im trying to boot it off the same HDD as i want to install it to

---

### Post by mastablasta on 2014-01-22
use a USB stick to installl from (or DVD)

---

### Post by danny_peck on 2014-01-22
ah ok. out of curiosity, is it not reconising the hard drive so that it cannot accidently overwrite itself during install? and thanks!:D

---

### Post by mörgæs on 2014-01-22
Please use a more informative thread title. 
Changed.

---

### Post by mastablasta on 2014-01-22
> **danny_peck said:**
> ah ok. out of curiosity, is it not reconising the hard drive so that it cannot accidently overwrite itself during install? and thanks!:D

i don't know if that is possible. it may be.

one of the problems is you will need to write bootloader on the MBR of hard disk durign install. perhaps if you tried to partition and format the disk before doing it he install it might work. also linux uses EXT or other filesystems, while to boot the image of a HDD you are probably are using fat32 or more likely NTFS file system.

---

### Post by sudodus on 2014-01-22
Ubuntu flavours (standard Ubuntu, Kubuntu, Lubuntu, Xubuntu ...) are portable, so that it is possible to install a system, when a HDD is connected to one computer, and it will work, when you connect it to another computer. This includes USB hard disk drives and pendrives and hard disk drives that you connect temporarily via a 'USB to IDE and eSATA cable' adapter. But avoid installing any proprietary drivers until you have connected the device to where it is going to be permanently.

I think it might work, but it is risky to try to install Ubuntu to the same drive, that you are installing from. Different installers might work in different ways. The [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") will not allow installing into the same drive in basic mode, and not into the same partition in advanced mode. I'm not sure how the desktop and alternate installers work.

---

