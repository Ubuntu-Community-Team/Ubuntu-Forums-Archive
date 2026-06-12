---
title: "sis resolution"
date: 2014-08-30
forum: New to Ubuntu
---

### Post by martysween on 2014-08-30
hi guys, im in a sticky situation here lol, my niece gave me and old laptop with win vista on it and said she liked my os ''ubuntu'' could i put it on and i said yeah but the resolution is stuck at 640x480 and i havent a clue how to get the resolution set right, its an old e system 1412 dualcore laptop im using ubuntu 14.04.01 lts im pretty sure its sis graphics chip, please could you walk me through the process step by step, i was pretty good at fixing windows but im still trying to get used to linux.. any help on fixing this would be greatly welcomed :)

---

### Post by mörgæs on 2014-08-30
Hi, welcome to the fora.

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Mark Phelps on 2014-08-30
The following link has some info about SiS drivers:  [http://askubuntu.com/questions/362792/how-to-install-sis-771-671-video-drivers-on-13-10]("http://askubuntu.com/questions/362792/how-to-install-sis-771-671-video-drivers-on-13-10")

But, you first have to find out what model chipset you have.  To do that, open a terminal, enter "lspci" (without the quotes) and look for the line containing "VGA".  Post that info back here.

---

### Post by martysween on 2014-08-30
hi, im not sure where to type it, i think its a lubuntu distro so its different from mine..

---

### Post by martysween on 2014-08-30
i found it, 

lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 IDE Controller (rev 01)
00:03.0 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by mörgæs on 2014-08-30
The driver is installed by default in 14.04.

Have you seen this?
[http://ubuntuforums.org/showthread.php?t=2215422](http://ubuntuforums.org/showthread.php?t=2215422)

Besides, I would give the old iron Lubuntu in stead of Ubuntu.

---

