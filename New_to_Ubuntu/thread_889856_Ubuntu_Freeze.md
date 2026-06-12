---
title: "Ubuntu Freeze"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by F.R Mostert on 2008-08-14
Hi I have ubuntu8.04 installed and freeze if I move windows around in the desktop and also found Evolution to freeze the system. The system freeze completely no keyboard or mouse movement.  I have to do a hard boot again, I have also latly learned on this forum about lt sysrq and reisub.  Is there a function like dxdiag(used in windows) to post my system specs.  I know my memory is 900 meg and processor is 233 Mhz(I think).

Regards

---

### Post by LowSky on 2008-08-14
Most likely your running into problems because of that processor



[URL="https://help.ubuntu.com/community/Installation/SystemRequirements"]
https://help.ubuntu.com/community/Installation/SystemRequirements[/URL]> Bare Minimum requirements
It should be possible to get Ubuntu running on a system with the following minimum hardware specification, although it is unlikely that the system would run well. You should use the Alternate install CD to attempt such an installation. 

300 MHz x86 processor 
64 MB of system memory (RAM) 
At least 4 GB of disk space (for full installation and swap space) 
VGA graphics card capable of 640x480 resolution 
CD-ROM drive or network card 

Recommended minimum requirements
Ubuntu should run reasonably well on a computer with the following minimum hardware specification. However, features such as visual effects may not run smoothly. 

700 MHz x86 processor 
384 MB of system memory (RAM) 
8 GB of disk space 
Graphics card capable of 1024x768 resolution 
Sound card 

A network or Internet connection 

Note: All 64-bit (x86-64) PCs should be able to run Ubuntu. Use the 64-bit installation CD for a 64-bit-optimised installation. 


Recommended for visual effects
Visual effects provide various special graphical effects for your desktop to make it look and feel more fun and easier to use. If your computer is not powerful enough to run visual effects, you can turn them off and will still have a usable Ubuntu desktop. 

Visual effects are turned on by default if you have a graphics card which is supported. For information on supported graphics cards, see DesktopEffects. 

1.2 GHz x86 processor 
384 MB of system memory (RAM) 
Supported graphics card (see DesktopEffects) 



---

### Post by LowSky on 2008-08-14
your best bet is this for a smooth running system
[http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html](http://www.binonabiso.com/en/Ubuntu-miniRAM-HOWTO.html)

---

### Post by wariskampar on 2008-08-14
In my experience, when Ubuntu freeze up (like in your case), REISUB will be useless. Matter of fact, any keyboard combi is useless. Only hard reboot will do. In my case, Ubuntu occasionally freeze when I want to watch movies.

---

### Post by LowSky on 2008-08-14
His issue is using below minimum specification processor.
A diiferent GUI or differnet Linux editoin like  Damn Small Linux would work better

---

### Post by tahina on 2008-08-14
To get info on your hardware, you can use the lshw command. 

If you open a terminal (in Applications>Accessories menu) and type... ```
sudo lshw -html > myhardware.html
```... you will get a html-document named myhardware.html in your home directory. 

To find out other usage of the lshw command, type "man lshw" (without the quote-marks) in the terminal.

---

### Post by F.R Mostert on 2008-08-14
Hi here is my hardware profile

---

### Post by tahina on 2008-08-14
The line that says "Intel(R) Celeron(R) CPU 2.40GHz" indicates that you have a cpu that should cope just fine...


This will probably not help, but to rule out that the fault is with some configuration that may have changed, you could create a new user (with "Users and groups" in the System>Administration menu) and see if you can recreate the freeze with the fresh user account...

---

### Post by F.R Mostert on 2008-08-15
Hi,  I get freezes in any application that use memmory but I have enough memory.  Maybe it can be my swap file? I do not know the size of my swap file and also not how to check it but i maybe in the attachment I posted earlier.  I have also swapped the phisical memory around with new ones so It cannot be the memory.  In windows you have vertual memory is tere an eqivalent in ubuntu?

Regards

---

### Post by tahina on 2008-08-15
The swap partition is the virtual memory.

You can install gparted to look at and play around with partitions. > sudo apt-get install gparted
It will then appear as "Partition Editor" in the System>Administration menu. They recommend also installing the package ntfsprogs... (That's probably for manipulating the ntfs partitions.)

For ntfs write-support you can install the package ntfs-3g (unless it's all ready installed by default on Hardy, I forget.)

---

