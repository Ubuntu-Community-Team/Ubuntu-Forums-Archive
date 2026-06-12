---
title: "Sound Problems with left side speaker."
date: 2008-09-06
forum: New to Ubuntu
---

### Post by EternalBuntu on 2008-09-06
I am getting no sound from my left Headphone/speaker. I triple checked the hardware and its fine, works perfectly in windows. I dont know what else to do Im lost with only sound coming out the right side, none on the left. The sound card is a PPA Model # 1424v 8 Channel PCI Sound Card.
Heres the link to the card itself
[http://www.ppa-usa.com/products/soundcard/1424v.htm](http://www.ppa-usa.com/products/soundcard/1424v.htm)

So can someone please help me, I need my sound :(





Here are my specs.



00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller (rev 01)

---

### Post by Corrupt3d on 2008-09-06
Have you tried changing the settings of the Alsa _software_ making sure that the left speaker isn't muted?

Bring up the sound interface by typing "**gnome-volume-control**" into your terminal.
You can make it show the different setting by going to 'Edit>Preferences' and ticking all the boxes.

---

### Post by EternalBuntu on 2008-09-06
Tried that still no luck sometimes when I mess around with the  Multi track internal clock settings I reboot and it seems to work, but then I reboot again and Im back to the same problem. :(

---

### Post by EternalBuntu on 2008-09-06
Help????  :(

---

