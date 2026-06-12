---
title: "Display and wifi problems."
date: 2012-05-15
forum: New to Ubuntu
---

### Post by bnorman1993 on 2012-05-15
I installed ubuntu 11.10 i cant seem to get the display driver to work on my laptop nor can i get the wifi card to work its a broadcom and my computer is a hp dm4 1060us i have tried the sudo commands and activating the wifi card but it still wont connect as if its not installed and i cant carry the laptop to anywhere else to try and connect because my display driver dont work unless plugged into my crt monitor through the vga port please help thanks in advance

---

### Post by codingman on 2012-05-15
hello and welcome to Ubuntu Forums!

So it doesn't give you any screen?

Just blank?

Give us some information.

---

### Post by Lisiano on 2012-05-15
Please open a terminal (Ctrl+Alt+T) and copy paste this command, this will tell us more about your GPU and your WiFi chip.
```
lspci
```

---

### Post by bnorman1993 on 2012-05-16
well the crt monitor isnt blan but my laptop one is after the ubuntu starts loading like where it says ubuntu with the dots at the bottom and thanks for the welcomingi have worked with ubuntu before in school and just decided to try something new but this is getting annoying fast had to wait to get back from work to post, 
[EMAIL="brandon@brandon-HP-Pavilion-dm4-Notebook-PC:~$"]brandon@brandon-HP-Pavilion-dm4-Notebook-PC:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by bnorman1993 on 2012-05-16
wow i am an idiot i cant believe what i did it didnt turn up the brightness on ubuntu and my wifi was from joikuspot so i was supposed to set the channel on my phone from 11 or auto to 1or 6 for some reason but it works now thanks for the help guys

---

### Post by chamber on 2012-05-17
Use the thread tools to mark as solved then.

---

