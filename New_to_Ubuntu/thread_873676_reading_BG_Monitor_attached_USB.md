---
title: "reading BG Monitor attached USB"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by cuddy on 2008-07-29
In Ubuntu Heron I have tried to read recorded Blood Glucose results but the device does not seem to be seen. I would like to read into Gnumeric which was recommended. I have tried on diabetic forums but getting nowhere as there seems little use of Linux. In XP I used a driver supplied by the manufacturer, Abbott, but they have none for Linux, also another graphing etc pgm which was crude but worked.

I was asked for the results of these commands:
brendan@brendan-laptop2:~$ dmesg | tail
[   90.524910] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   90.525386] [drm] Initialized radeon 1.28.0 20060524 on minor 0
[   65.555459] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   65.555875] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   65.556167] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   93.607136] eth1: no IPv6 routers present
[   94.262053] [drm] Setting GART location based on new memory map
[   94.262127] [drm] writeback test succeeded in 2 usecs
[ 4355.668640] usb 1-2: new full speed USB device using uhci_hcd and address 2
[ 4355.852838] usb 1-2: configuration #1 chosen from 1 choice
brendan@brendan-laptop2:~$brendan@brendan-laptop2:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0483:2015 SGS Thomson Microelectronics 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 002: ID 1a61:3410  
Bus 001 Device 001: ID 0000:0000  
brendan@brendan-laptop2:~$ 

This and my Palm M130 are really giving me headaches. I am almost going to start again and have dual boot. Any help would be most appreciated. 
Thanks,
Cuddy.

---

