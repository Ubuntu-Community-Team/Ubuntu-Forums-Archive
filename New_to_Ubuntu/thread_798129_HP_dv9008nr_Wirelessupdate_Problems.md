---
title: "HP dv9008nr Wireless/update Problems"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Snyper_Vash on 2008-05-17
Ok, i have just recently installed Ubuntu 6.06 dapper i believe its called. I just need to know how to get my wireless working. Here is my lspci>>

vash@vash-laptop:~$ lspci
0000:00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
0000:00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
0000:00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
0000:00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
0000:00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
0000:00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
0000:00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
0000:00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
0000:00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
0000:00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
0000:00:10.1 0403: nVidia Corporation MCP51 High Definition Audio (rev a2)
0000:00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:03:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)
0000:07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd: Unknown device 0832
0000:07:05.1 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
0000:07:05.2 System peripheral: Ricoh Co Ltd: Unknown device 0843 (rev 01)
0000:07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
0000:07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)vash@vash-laptop:~$


And my second problem is that my Update Manager isnt working. I had another post a few days ago about my wireless and someone said it would be easier on 8.04 Hardy. Thing is, it wont let me update through the system with my update manager. When i try to load it, i click the check button, and it says it downloads like 18 files, then it just sits there. 

If anyone could help it would greatly be appreciated.

---

### Post by cardinals_fan on 2008-05-17
[http://bayu.freelancer.web.id/index.php/2007/05/05/setting-broadcom-wireless-device-in-kubuntu-in-detail-part-1/](http://bayu.freelancer.web.id/index.php/2007/05/05/setting-broadcom-wireless-device-in-kubuntu-in-detail-part-1/)

---

### Post by Inxsible on 2008-05-17
If you have really installed Dapper (6.06), I would advise you to upgrade to Hardy Heron (8.04). 8.04 is also a LTS version-- if that was your primary reason for going with 6.06.

The latest version has a lot more support for wireless than its predecessor.

---

### Post by Snyper_Vash on 2008-05-17
Yeah, i really want to update to Hardy, But can i only do that by downloading the disc? And if i can, is there an upgrade option when i load the disc or do i have to do a whole new install?

---

### Post by Inxsible on 2008-05-17
> **Snyper_Vash said:**
> Yeah, i really want to update to Hardy, But can i only do that by downloading the disc? And if i can, is there an upgrade option when i load the disc or do i have to do a whole new install? I am not really sure I understand your question, but you can install Hardy by burning a Hardy install disc. If you plan to upgrade, you will have to install 6.06-- then upgrade to 6.10 -- then upgrade to 7.04 -- then to 7.10 and then finally to 8.04. A Long drawn process, I would say !!!!

You cannot skip a version during the upgrade process. It would be much easier to just do a new install using a Hardy install disc.

You can get the Hardy disc from 

[www.ubuntu.com/download](www.ubuntu.com/download)

---

### Post by Snyper_Vash on 2008-05-17
Ok, i cant get past the first command in that guide. Heres what happens.

vash@vash-laptop:~$ sudo ndiswrapper -i /home/vash/ndiswrapper-1.52
sudo: ndiswrapper: command not found

---

### Post by Ayuthia on 2008-05-18
> **Snyper_Vash said:**
> Ok, i cant get past the first command in that guide. Heres what happens.

vash@vash-laptop:~$ sudo ndiswrapper -i /home/vash/ndiswrapper-1.52
sudo: ndiswrapper: command not found
If I recall correctly, you will have to download ndiswrapper from [http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net).  You will also have to install build-essential and linux-headers-`uname -r`.  build-essential should be on your install CD, but I think that you will have to go to [http://packages.ubuntu.com](http://packages.ubuntu.com) (sorry-I tried to get the direct link to the file, but the page is stalling) and get the linux-headers-2.6.15-23-386 from there.

Once you get those installed, you will then have to compile ndiswrapper.  After that, you can follow those steps.

It might be possible that ndiswrapper-common and ndiswraper-utils is on the install CD, but I can't remember if that version works with your wireless card (I have the same card).

---

