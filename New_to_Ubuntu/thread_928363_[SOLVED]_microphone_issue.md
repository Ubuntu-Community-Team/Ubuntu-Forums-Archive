---
title: "[SOLVED] microphone issue"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by economy on 2008-09-23
Hi all,

Trying to get Skype running on Ubuntu Hardy 8.04

My laptop has a built-in microphone and webcam. skype found the webcam no problem, it works well. the microphone, though, doesn't seem to register. skype has 5 options in the sound options tab under Sound In (Default, HDA Intel (hw,0), HDA Intel (hwplug, 0), HDA Intel (hw,6) and HDA Intel (hwplug,6))...

When I try using Sound Recorder it doesn't record either, no matter which option I choose (Front Mic Boost, Line In Boost, Capture, Mic Boost).

In the Sound Mixer, I have the Front Mic Boost all the way up, the Mic Boost all the way up, the Capture halfway with both capture options on, and I haven't turned up the Line In Boost because I'm fairly sure it's for the headphone jack in the front of the laptop (right?).

My sound settings seem to work for everything else, HDA Intel ALSA is my chosen hardware setup.

Any ideas?

---

### Post by Crafty Kisses on 2008-09-23
What are the results of this command?
```
lspci
```

---

### Post by economy on 2008-09-23
economy@economy-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by economy on 2008-09-23
sorry for the bump, 

i feel like this is a simple issue but i can't find help elsewhere

---

### Post by rascalbvi on 2008-09-25
if u have alsa-utils installed you can use 'alsamixer' to configure source, levels, capture, etc.. play with them whist trying to record some sound. its all about the correct capture channel with correct mic, front (built in) and mic (plug in)

---

### Post by economy on 2008-09-29
Hah, I solved the issue. Much easier than I had imagined. Anyone searching this post:

Find the Volume Controls by right clicking the speaker in the upper-right. In Edit > Preferences, find and check Input Source as well as Capture and Front Mic (if you're using a built-in like me) . This should pull up two new tabs in the Volume Controls: Recording and Options. In the Recording tab, pull Capture level up to about 80%, make sure you're not muted or disabled by using the buttons below the level. Now in Options choose your Input Source (again, in my case Front Mic is the correct option). Now make sure Front Mic's level isn't muted or below 50% and it's time to test.

To test, go to Applications > Sound > Sound Recorder and make sure you switch the input from Digital to Front Mic (or whatever's applicable). Record and playback for the test. Mess with levels in Volume Controls as necessary. 

Hopefully Skype will work now.

---

### Post by letank on 2008-09-30
> **rascalbvi said:**
> if u have alsa-utils installed you can use 'alsamixer' to configure source, levels, capture, etc.. play with them whist trying to record some sound. its all about the correct capture channel with correct mic, front (built in) and mic (plug in)

Thanks, that solved my skype lower than low sound signal, and other recordings

Michel

---

