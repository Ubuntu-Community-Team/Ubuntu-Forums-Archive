---
title: "glitchy scrolling/resizing in applications"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by brak3000 on 2008-09-06
Hi,
I'm running Ubuntu 8.04 on a compaq pc with 512Mb ram, a 3100 AMD Sempron, and...I'm not sure what the graphics card is. It was the standard one if that helps. I'll look it up after I post this and turn off the pc.

My problem is that whenever I scroll or resize an application window it doesn't refresh the screen. Resizing will make the window "disappear" and scrolling won't change the window at all. If I run my mouse over it, the dynamic parts of the window (i.e. buttons, links, text boxes, etc) will refresh, but I'm left with a sort of glitchy mess that is unsightly and hard to work with. If I change windows and come back, it will usually fully refresh itself.

I'll attach a picture to show what I'm describing.

I'm relatively new to Ubuntu, and new to these forums. I tried looking for similar previous posts, but no luck. Any help would be greatly appreciated. Thank You!

---

### Post by knix on 2008-09-06
can you post your lspci results
type "lspci". look for anything about vga compatible, ati, or nvidia. chances are you have an intel graphics adapter though.

Edit: i'm sorry for being vague. got to applications>accessories>terminal. type "lspci" and press enter. then copy the output into the forum.

---

### Post by brak3000 on 2008-09-07
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:09.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by knix on 2008-09-08
OK, your video is an SiS integrated adapter.
There is no available 3d driver for SiS. However, there is a better 2d driver that makes normal usage possible.

For hardy: [http://rs297.rapidshare.com/files/118140763/sis_vga_150508_ubuntu_8.04.tar.bz2]("http://rs297.rapidshare.com/files/118140763/sis_vga_150508_ubuntu_8.04.tar.bz2")

For feisty:[http://rapidshare.com/files/72690205/sis_vga_200807_ubuntu_7.04.tgz.html]("http://rapidshare.com/files/72690205/sis_vga_200807_ubuntu_7.04.tgz.html")

what you have to do is move sis_drv.* to /usr/lib/xorg/modules/drivers/ and modify your /etc/X11/xorg.conf driver line from vesa to sis.

---

### Post by brak3000 on 2008-09-11
Hey Knix,

Thanks for all the help!
Sorry to sound like an idiot, but I can't seem to mv those files. It says permission denied. I never really learned how to deal with permissions, so could you tell me how to work with this?

Thanks again!

---

### Post by BlakeKent on 2008-09-11
Hi I have the same problem. I have an IBM R51 with ubuntu 8.04. i had 7.10 and deleted that and re-installed 8.04 and now there's this weird graphics glitch. Heres my "lspci" result:

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

please help!

---

### Post by brak3000 on 2008-09-20
Ok, so I moved the files to where you wanted me to using sudo mv(I hope that was the right way).

I'm trying to modify the xorg.conf from vesa to sis, but i don't see anything in the file that says vesa. Where should I modify this?

I know it's been a while since I first brought this problem to light, but if anyone could help me it'd be greatly appreciated!

---

### Post by brak3000 on 2008-09-20
Ok, so I tried to do what you said. I moved the files into the location and went to etc/X11 and modified the xorg.conf file. 

Apparently I did something wrong because now my screen is running on low-res 800x600 and I don't know how to revert it!

Please Help!

Thanks again.

---

