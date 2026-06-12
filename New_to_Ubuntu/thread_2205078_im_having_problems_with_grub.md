---
title: "im having problems with grub"
date: 2014-02-11
forum: New to Ubuntu
---

### Post by Khizz on 2014-02-11
Hi
i have two drives a hdd and ssd . The hdd has windows 8 and ssd has windows 7. i usethe windows 7 bootloader for swithing between windows 7 and 8. then i installed elementary os on the ssd with the bootloader in ssd but when i boot it doesnt show grub only boots in to elementary...then i tried boot repair tool. nothing different...then what i did is in boot repair i set windows as default then i added elementary to the windows bootloader using easybcd but that just kept taking me back to the list without saying its having an error...i had done something similar with ubuntu when i didnt have and ssd and i had windows vista 7 and 8 and i installed all those after installing ubuntu so i added it through easy bcd. it worked out. i tried everything i could with boot-repair tool in live usb but it just didnt make a difference .... so what i want is grub to show up with elementary windoes 7 and 8.

---

### Post by oldfred on 2014-02-13
Are all systems installed in UEFI mode or all in BIOS mode?
Windows only installs boot files to partition with boot flag (active partition in Windows) and the drive set as boot in BIOS (with BIOS installs). To get grub to boot both Windows you have to repair the one without boot files to add them to that install.

 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

To understand how Windows boots with BIOS. Shows Vista, but applies to all BIOS boot.
      
 Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Khizz on 2014-02-16
turns out it was a hardware problem.....i got a new keyboard and mouse and the grub menu randomly showed up. when i try the old ones same thing happens..

---

### Post by Khizz on 2014-02-16
correction : when i try with the old ones grub doesnt show up

---

### Post by oldfred on 2014-02-17
Some BIOS have settings to turn on USB ports for keyboards & mouse. Have you checked settings in BIOS?

With my system both XP & Ubuntu would work, but grub would not with USB but would with ps/2. Both Windows and Ubuntu add drivers, but grub depends on BIOS for defaults. And when I updated BIOS it reset back to defaults which was keyboard off.

---

