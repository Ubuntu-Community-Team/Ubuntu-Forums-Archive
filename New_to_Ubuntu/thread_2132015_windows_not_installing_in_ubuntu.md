---
title: "windows not installing in ubuntu"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by 123u on 2013-04-03
hello this is my first post ,here, i have a lenovo desktop with ubuntu 12.10 in it but i want to install windows 8 pro in it and install ubuntu as dual boot in my laptop with windows 7 
so, i was able to dual boot it in my laptop but whenever i put windows 8 install disc in my desktop it simply displays a blank screen with a arrow bot i cant write anything,
i have seen bios and tried installing it from usb but dosent work,please help i am facing quiet a problem with it and i have to use it in home urgently .please help!.

---

### Post by oldfred on 2013-04-03
Windows only boots from primary partitions (sda1 thru sda4) formatted NTFS with the boot flag. If a second install of Windows, the second install will move all its boot files to the install with the boot flag. 
Windows does not see Linux partitions and sometimes it partitioning tools do not rewrite partition table correctly. Best to backup partition table and all your data first. 
With gparted create a NTFS partition for Windows to install into. 
Is your system new enough to also boot with UEFI. You must have all systems installed in BIOS mode or all in UEFI mode.

       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by 123u on 2013-04-04
[COLOR=#000000]but i dont see widows install setup it inserting a windows install disc display a blank screen no ubuntu also but when i remove it boots directly into ubuntu i can create a ntfs part with boot flag but dont acatly understand ,please explain easily ,i dont know much aboutit please help.[/COLOR]

---

### Post by 123u on 2013-04-04
> **oldfred said:**
> Windows only boots from primary partitions (sda1 thru sda4) formatted NTFS with the boot flag. If a second install of Windows, the second install will move all its boot files to the install with the boot flag. 
Windows does not see Linux partitions and sometimes it partitioning tools do not rewrite partition table correctly. Best to backup partition table and all your data first. 
With gparted create a NTFS partition for Windows to install into. 
Is your system new enough to also boot with UEFI. You must have all systems installed in BIOS mode or all in UEFI mode.

       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)
 but i dont see widows install setup it inserting  a windows install disc display a blank screen  no ubuntu also but when i remove it boots directly into ubuntu i can create a ntfs part with boot flag but dont acatly understand ,please explain easily ,i dont know much aboutit please help.

---

### Post by oldfred on 2013-04-04
I do not think Windows is seeing any place to install, so it cannot do anything. Or perhaps your Windows install disk is not written correctly.
Also is it a full install or a recovery disk. It has to be the full install to work. Recovery reinstalls just erase drive and restore it to exactly as purchased.

---

