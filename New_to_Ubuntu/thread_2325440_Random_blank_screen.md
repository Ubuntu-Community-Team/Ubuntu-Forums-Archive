---
title: "Random blank screen"
date: 2016-05-22
forum: New to Ubuntu
---

### Post by Hosam_Mohamed on 2016-05-22
[COLOR=#111111][FONT=Ubuntu]I installed Ubuntu 16.04 (dual booting with Windows 10). The problem I am facing is, everything is OK, then suddenly, the screen becomes black and nothing is responsive
Update:
Sometimes I get blank black screen and sometimes blank white screen

Update 2:
I cleanly installed Ubuntu 15.10. That did not solve the problem

Hardware:
OS: Ubuntu 15.10 64x
Motherboard:
Processor: AMD Athlon II X2 250
RAM: 4GB
Display: [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]AMD 760G ([/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Built in)[/FONT][/COLOR]

---

### Post by RobGoss on 2016-05-22
Hello welcome to the forum, would you mind giving us some info on your machine like specs it will help others help you better

---

### Post by RobGoss on 2016-05-22
> **Hosam_Mohamed said:**
> [COLOR=#111111][FONT=Ubuntu]I installed Ubuntu 16.04 (dual booting with Windows 10). The problem I am facing is, everything is OK, then suddenly, the screen becomes black and nothing is responsive
Update:
Sometimes I get blank black screen and sometimes blank white screen

Update 2:
I cleanly installed Ubuntu 15.10. That did not solve the problem

Hardware:
OS: Ubuntu 15.10 64x
Motherboard:
Processor: AMD Athlon II X2 250
RAM: 4GB
Display: [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]AMD 760G ([/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Built in)[/FONT][/COLOR]

I'm trying to understand which OS are you running 15.10 or 16.04 if in fact you're using 15.04 I believe it's almost at it's ending of life for that distribution
But you also stated this problem was also present with Ubuntu 16.04 correct?

if this is happening with both distro's it may be a graphic card issue

Run this command:
```
[COLOR=#111111][FONT=Consolas]lspci[/FONT][/COLOR]
```

Also run this command:
```
 [COLOR=#111111][FONT=Consolas]lspci | grep VGA[/FONT][/COLOR]
```

And post the output using the code tags

---

### Post by Hosam_Mohamed on 2016-05-22
Now I am using 15.10

```


00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS780L [Radeon 3000]
02:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
03:06.0 Ethernet controller: Qualcomm Atheros AR2417 Wireless Network Adapter [AR5007G 802.11bg] (rev 01)




```

---

### Post by RobGoss on 2016-05-22
Are you using a **DVD** or **USB** for your installation and if so how did you create it and what programs are you using to create them with

Try [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) to create your **bootable USB** that's what I also use and it works great each and every time, it's worth a shot, I would also download another ISO file just in case there's some issues with the one you are using I recommend Ubuntu 16.04 LTS

---

### Post by Hosam_Mohamed on 2016-05-23
I use Unetbootin. This is the first to install Ubuntu from flash memory, but it is the first to find such problem

---

