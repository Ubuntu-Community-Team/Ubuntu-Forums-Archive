---
title: "SD Card Isn't Appearing"
date: 2016-12-09
forum: New to Ubuntu
---

### Post by yeva.e.a on 2016-12-09
Hi, I'm very new to Linux and I don't think I know what I'm doing. I installed Lubuntu 16.10 on my low-end laptop via USB. Unfortunately, my laptop's built-in SD card reader isn't picking up anything. The port worked fine before installing Lubuntu. I've tried following other threads on here about SD cards, but none have worked for me. I've also tried downloaded different tools in the Synaptic Pack Manager and making sure my software is up to date. A related issue I've had that might be part of this is that no USB devices show up despite the LED on them lighting up, but I'd rather save that for another thread if this isn't related. I'm only familiar with Linux enough to copy+paste terminal stuff.

---

### Post by Bucky Ball on 2016-12-09
Welcome. For larger SD cards you need exfat-utils and exfat-fuse installed. You'll find them in Synaptic. 

The USB issue may be related to might be an idea so post a link to this thread when you post a thread about that (yes, stuff of another thread). 

Good luck. ;)

---

### Post by yeva.e.a on 2016-12-09
I tried everything again after installing those two and it looks like nothing has changed. What kind of information would you need from me to help me solve this (and maybe walk me through getting the info)?

---

### Post by Bucky Ball on 2016-12-09
That was a stab in the dark and about all I got. Bump your thread by posting 'bump' if there is no other response within 12 hours. Good luck. ;)

---

### Post by Geoffrey_Arndt on 2016-12-09
Please bring up a terminal (ctrl+alt+t), and input "lsusb" after inserting an SD card and usb flash-stick into their respective ports.

Please post the results. 

Also, do you have the program "disks" installed?  If not install it . . . it offers a way to mount devices without memorizing terminal mount/unmount commands.

---

### Post by yeva.e.a on 2016-12-09
Disks is installed, but that doesn't seem to help any. Only my hard drive appears on the left column. Off the top of my head, my laptop's CPU is an AMD A4-6210. Not sure if that helps. Anyway, here's what the terminal says:

```
Bus 002 Device 003: ID 5986:0367 Acer, Inc 
Bus 002 Device 008: ID 0bda:0177 Realtek Semiconductor Corp. ay
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0489:e07a Foxconn / Hon Hai 
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Geoffrey_Arndt on 2016-12-10
That all looks OK.   One thing to do is verify is your usdisks install:

You can try this in a terminal:   sudo apt install --reinstall udisks2     . . . then reboot and try again.

---

### Post by wildmanne39 on 2016-12-10
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by yeva.e.a on 2016-12-10
I reinstalled udisks 2 and rebooted, but nothing seems to have changed yet. Sorry about the code tags, I was wondering how people were doing that. I'll use them for now on. Is there a setting that I may have accidentally changed somewhere else that could be stopping access my flash drives and SD card? My wireless USB mouse has been working just fine all along.

---

### Post by Geoffrey_Arndt on 2016-12-12
Are these standard media cards & usb flash-sticks with the msdos fat32 filesystems?    Were they ever used in a Mac machine?

---

### Post by yeva.e.a on 2016-12-12
They're fat32 and they worked with Windows perfectly fine. I've never plugged them into a Mac.

---

### Post by yeva.e.a on 2016-12-12
I discovered something new as well. Booting my laptop with the flash drive plugged in detects it and mounts it automatically. It just won't work if I plug it in after my laptop is already on.

EDIT: Please lock this. I've switched to Manjaro, which doesn't have the problems I've been working my way through. My voume keys and I/O ports work and my keyboard no longer randomly cuts/pastes in the middle of typing. Steam also works on my laptop again. Thanks for everyone's help regardless!

---

