---
title: "Select a boot first device"
date: 2016-02-27
forum: New to Ubuntu
---

### Post by Norman_L_Bliss on 2016-02-27
I’m installing Ubuntu using a USB SanDisk. In Boot Menu I don’t know what boot menu to select? These are my options. LS 120, *Hard Disk, CDROM, ZIP, USB – FDD, USB – ZIP, USB – CDROM, USB – HDD and Legacy Land.

---

### Post by yetimon_64 on 2016-02-27
I don't know what make of BIOS/UEFI set up you have there but I have on occasion used the USB-HDD setting successfully with USB sticks when installing in the past. USB-HDD is worth a try first in my opinion.

---

### Post by fantab on 2016-02-27
Yep, it is usually USB-HDD. However if it doesn't work try other options until you find the right one :D

---

### Post by Norman_L_Bliss on 2016-02-27
thanks

Ubuntu screen come up but the arrow on my key board didn’t work. I found a work around and am installing Ubuntu now. Will see how it goes.

Help, Installation Failed. Error 30. Installer crashed

---

### Post by MartyBuntu on 2016-02-27
Tell us a little bit about the machine you're installing Ubuntu on.

---

### Post by Norman_L_Bliss on 2016-02-27
Motherboard: GA-770T-USB3 (rev. 1.0)
Power Supply: eXtreme Power Plus 600W
Central Processing: AMD - Phenom II X4 955 Black Edition, Socket AM3 &#8211; Deneb - Quad-Core - 3.2GHz - 4000MHz - 4 x 512KB - 6MB - 45 nm - 64 bit Support - Hyper-Transport Support - Virtualization Technology Support - 125W
RAM: CORSAIR XMS 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 2000 (PC3 16000)
Optical Drive: DVD Burner
Video Card: APCB M3 94V-0
Manufacturer: NVIDIA GeForce 310 Video Card
Model: APCB M3 94V-0
Memory Type: 512MB DDR2 64-Bit
3D API: DirectX 10.1, OpenGL 3.1
PCI Express 2.0 x16 interface
Hard Drive: Western Digital Caviar Green 1TB Internal Hard Drive, 5400RPM SATA 16 MB Cache 3.0Gb/s 3.5" WD10000CSRTL

---

### Post by X-RED_Tech on 2016-02-28
Two problems:
- Motherboard may require an additional boot parameter, IOMMU=soft
- Graphics Nvidia may require nomodeset. Not required if you have video in Try Ubuntu and during installation. May be required later, after installing and before adding the nvidia drivers.

---

### Post by Norman_L_Bliss on 2016-03-23
Thanks X-RED_Tech. This information looks like it could be the answer to my problem. 
Now my question is what do I do with this information.
Sorry haven't gotten back sooner been doing a lot of doctor stuff.

---

### Post by yetimon_64 on 2016-03-23
> **Norman_L_Bliss said:**
> Thanks X-RED_Tech. This information looks like it could be the answer to my problem. 
Now my question is what do I do with this information.
Sorry haven't gotten back sooner been doing a lot of doctor stuff.

For the boot parameter you will need to edit a system file as root. You can open a text editor as root with the file /etc/default/grub by copying and pasting the next command box in a terminal ...
```
gksudo gedit /etc/default/grub
``` enter your password and when the editor opens the file alter the line ...
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to read as ...
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash IOMMU=soft" then save the file and exit.

Next, in the terminal, issue the next command to make the change to the grub boot screen entries permanent...
```
sudo update-grub
``` and you are done. 

On the next boot of the system the new boot parameter will be used.

>   Graphics Nvidia may require nomodeset. Not required if you have video  in Try Ubuntu and during installation. May be required later, after  installing and before adding the nvidia drivers.

As per X-RED_Tech's post only use the nomodeset IF you have video problems as noted and quoted above. Same procedure as for the IOMMU parameter. IF you need to use nomodeset your GRUB_CMDLINE_LINUX_DEFAULT line would look like ...
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash IOMMU=soft nomodeset" Always remember to run the "sudo update-grub" command I showed above to make the changes permanent, even with the line altered in /etc/default/grub, without the update-grub command NO new parameter changes will occur on the next boot. 

**Note:** I am assuming those are the correct parameters; my post is only to show you how to change and permanently set such parameters on the basis of such an assumption.

Regards, yeti.

---

