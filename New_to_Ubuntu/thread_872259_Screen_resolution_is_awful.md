---
title: "Screen resolution is awful"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by flyer4100 on 2008-07-27
Hello all, this is my first post and I am very new to Ubuntu in fact this is my first foray away from XP. I have loaded8.04 onto two machines, my Toshiba laptop as a clean install with no partition. Everything is sweet as and even the wireless network runs ok.

However, I ham having a problem with my desk top and screen resolution. I originally had a gigabyte radeon 9200se video card but it only allowed a maximum 800x600 resolution. After doing many google searches for updated drivers I gave up. Further searches led me find drivers for nvidia graphics cards. 

I now have a FX5500 installed. Now Update Manager has found drivers for this and it loads ok. But I appear to be worse off as I can only select from "Preferences>Screen Resolution either

640x480 or 320x240 and a refresh of 50Hz.

If I disable the nvidia drivers i can select

800x600/640x480/400x300/320x240 and refresh 60Hz/56Hz

All very frustrating as you can well imagine.

Anyone have any help /suggestions for a newbie/novice?:(

---

### Post by tuxxy on 2008-07-27
The driver should of installed the nvidia manager, where resolution is displayed also.

run this at terminal;

```
nvidia-settings
```

---

### Post by UbuntuNerd on 2008-07-27
if you have no luck try editing your xorg file 
look in this link it may help

[http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

---

### Post by flyer4100 on 2008-07-27
I have managed to load  nvidia -settings and this gives me Nvidia XServer settings in "Administration" (I write this using a 640x480 resolution)

But I cannot select anything in XServer Display Configuration
it shows CRT-0 640x480
Model: CRT-0 (CRT-0 ON GPU-0)
Configuration: Separate X screen
Resolution: Auto

Whenever I try to select another resolution the screen just moves (remember I am on a 640x480) and I cannot see the whole screen (I am using a 17" LCD)

---

### Post by tuxxy on 2008-07-27
Mkae sure you are using the correct driver, type this into terminal;
```

glxinfo | grep 'OpenGL vendor'
```

---

### Post by flyer4100 on 2008-07-27
respons is NVIDIA Corporation

---

### Post by flyer4100 on 2008-07-27
$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:06.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
00:06.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0a.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

---

