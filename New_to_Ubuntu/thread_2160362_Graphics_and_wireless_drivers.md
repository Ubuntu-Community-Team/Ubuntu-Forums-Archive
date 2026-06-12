---
title: "Graphics and wireless drivers"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by Jovan J on 2013-07-06
Hello,

I've installed Ubuntu 12.04, since this is my first time I am using Linux generally. I am not sure how to install this drivers (Graphics and wireless). My Notebook is Asus k53s. Specifications can be found here: [http://www.asus.com/Notebooks_Ultrabooks/K53SV/#specifications](http://www.asus.com/Notebooks_Ultrabooks/K53SV/#specifications)

It would be great, if any one have some free time to help me about my problem how to install, already, mentioned drivers :)

---

### Post by KARNVORbeefRAGE on 2013-07-06
The correct drivers are typically installed when the OS is installed, as all Linux drivers are included in the kernel.  If you wish to have the proprietary Nvidia drivers, then go to "Settings" then "Software and Updates", then to the last pannel on "Additional Drivers".  Since this is a newer device, I believe the correct proprietary driver is the Nvidia-304.

Is your wireless working at all?  If not post results:

```
lspci
```

---

### Post by Jovan J on 2013-07-06
> **KARNVORbeefRAGE said:**
> The correct drivers are typically installed when the OS is installed, as all Linux drivers are included in the kernel.  If you wish to have the proprietary Nvidia drivers, then go to "Settings" then "Software and Updates", then to the last pannel on "Additional Drivers".  Since this is a newer device, I believe the correct proprietary driver is the Nvidia-304.

Is your wireless working at all?  If not post results:

```
lspci
```

I get this when i write above code in terminal:

> 00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
04:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)



For Additional Drivers, I've tried already, and i get this:
[IMG]http://i.imgur.com/pZMocHQ.png[/IMG]

It's connected on wireless, I get message "Connection Established", but It's not working. Everything is fine with my wireless since, everything works perfectly on my other computer.
Also for graphic i get this when I go to, System Settings, Details:


[IMG]http://i.imgur.com/Vtdh7AJ.png[/IMG]

---

### Post by Mark Phelps on 2013-07-06
System settings are usually inaccurate about the video chipset in use.  

IF you are seeing a desktop, the video drivers are already installed.

Also, it's best not to clump problems together in one thread.  Would be better if you started a new thread in the Networking section about your wireless problem.

---

### Post by Jovan J on 2013-07-07
So actually my graphic is installed because I see desktop? :)
If that is correct, everything is fine with graphics, desktop is perfect. Oh, I am sorry, I'll make another thread then.

---

