---
title: "Ubuntu 3.10 not detecting windows 8.1"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by arne-agten-36 on 2013-10-28
Hi,

I'm running windows 8.1 on my laptop, but I want to install Ubuntu next to it, so I can dual boot. But after I plug in my usb and start ubuntu install, it displays the message that there is no operating system detected. I don't know how to partition the windows drive so I can install Ubuntu. Help is very appreciated!

Regards

---

### Post by fantab on 2013-10-28
More info on Laptop is needed, like what brand, model, RAM Graphics etc.
How did you burn the ubuntu.iso to the USB?

---

### Post by oldfred on 2013-10-28
In addition to fantab's questions.

Did you turn off the fast boot or quick boot? Is it an Ultrabook with small SSD that uses Intel SRT or RAID?

Was it pre-installed Windows so it is UEFI with gpt, or did you install yourself in the old BIOS with MBR partitioning.

---

### Post by arne-agten-36 on 2013-10-28
I use an Acer Aspire v7-481-6607, with 8GB RAM. 500GB serial ATA drive and 20GB Solid State Drive. 
[COLOR=#4D5357][FONT=Trebuchet MS]Intel® Core&#8482; i5-3337U processor (1.8GHz/2.7GHz w/ Turbo Boost). 
[/FONT][/COLOR][COLOR=#4D5357][FONT=Trebuchet MS]Intel® HD Graphics 4000 w/ 128MB dedicated system memory 
Mobile Intel® HM77 Express chipset 
I used the Universal USB installer for Ubuntu.
And windows 8 was pre-installed, updated to 8.1 last weekend.[/FONT][/COLOR]

---

### Post by oldfred on 2013-10-28
You have to turn off fast boot and Intel SRT. The Intel SRT uses RAID and you will have to remove the RAID meta-data from drives to get grub to install correctly. 
Usually best to turn off secure boot, but Ubuntu will install with secure boot on.
Does your Windows boot ok with secure boot off?

See also additional info in links in my signature. 
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


 How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)
Acer V5-571P-6815 secure boot off worked Shows Diskpart
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

### Post by newb85 on 2013-10-28
I'd imagine 3.10 wouldn't recognize much of anything, since Ubuntu want released until 2004.  ;) Might want to fix your thread title.

---

