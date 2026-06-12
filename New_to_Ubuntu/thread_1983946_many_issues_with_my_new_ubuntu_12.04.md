---
title: "many issues with my new ubuntu 12.04"
date: 2012-05-21
forum: New to Ubuntu
---

### Post by bldrofshadows on 2012-05-21
First off I'd like to say greetings,
I am in every way a noob when it comes to the ubuntu os.
and so far from what I have been able to see of it, is a challenge and a vast new environment to explore. but to do that I need two things which has me about to pull my hair out. 
     
          1.wusb600n wireless internet card driver/ how to install and make it work.

          2.Ati 2600 hd xt driver/ where to get it and how to make it work with ubuntu 12.04

I have serched, and tried many thing. eather dosn't work or im doing something wrong. as for the driver for the video card I am at a loss.I just cant find the driver for it.

any ideas??

---

### Post by carl4926 on 2012-05-21
Post the result of this
```
lspci -nnk
```
from that we can see what you have in hardware and drivers

---

### Post by carl4926 on 2012-05-21
[http://homecommunity.cisco.com/t5/Wireless-Adapters/UBUNTU-WUSB600N-v2-WORKS/td-p/318026](http://homecommunity.cisco.com/t5/Wireless-Adapters/UBUNTU-WUSB600N-v2-WORKS/td-p/318026)

[http://ubuntuforums.org/showthread.php?t=1861579](http://ubuntuforums.org/showthread.php?t=1861579)

---

### Post by 3rdalbum on 2012-05-21
Procedure for installing graphics drivers:

Click on the Ubuntu logo on the left side of the screen, or hit the Windows key. Type "drivers" and click on the Additional Drivers icon.

If no driver is listed, then you already have the only driver available. If there is one listed, click the Activate button and it will download and install.

Of course, you need an internet connection... so get the wifi working or plug your computer into the router with an Ethernet cable, then click the Check button in Update Manager to get a list of available software, THEN look in Additional Drivers.

---

### Post by bldrofshadows on 2012-05-24
> **carl4926 said:**
> Post the result of this
```
lspci -nnk
```
from that we can see what you have in hardware and drivers

shaun@ubuntu:~$lspci -nnk
00:00.0 memory controller [0580]: NVIDIA Corporation CK804 Memory Controller [10de:005e](rev a4)
00:01.0 ISA bridge [0601]: NVIDIA Cororation CK804 ISA Bridge [10de:0050] (rev f1)
        Subsystem: Elitegroup Computer Systems Device [1019:1b13]
00:01.1 SMBus [0c05]: NVIDIA Corporation CK804 SMBus [10de:0052](rev a2)
        Subsystem Elitegroup Computer Systems Device [1019:1b13]
        Kernel driver in use:nforce2_smbus
        Kernel modules: i2c-nforce2
00:02.0 USB controller [0c03]:NVIDIA Corporation CK804 USB Controller [10de:005a](rev a2)
        Subsystem:Elitegroup Computer Systems Device [1019:1b13]
        Kernel driver in use: ohci_hcd
00:02.1 USB controller [0c03]: NVIDIA Corporation CK804 USB Controller [10de:oo5b](rev a4)
        Subsystem:Elitegroup Computer Systems Device [1019:1b13]
        Kernel driver in use: ehci_hcd
00:04.0 Multimedia audio controller [0401]:NVIDIA Corporation CK804 AC'97 Audio Controller [10de:0059](rev a2)
        Subsystem: Elitegroup Computer Systems Device [1019:1b13]
        Kernel driver in use:snd_intel8x0
        Kernel modules:snd-intel8x0
00:06.0 IDE interface [0101]: NVIDIA Corporation CK804 IDE [10de:0053](revf3)
        Subsystem: Elitegroup Computer Systems Device [1019:1b13]
        Kernel driver in use:pata_amd
        Kernel modules:pata_amd
00:07.0 IDE interface [0101]: NVIDIA Corporation CK804 Serial ATA Controller [10de:0054](rev f3)
        Subsystem: Elitegroup Computer Systems Device [1019:1b13]
        Kernel driver in use: sata_nv
        Kernel modules: sata_nv
00:09.0 PcI bridge [0604]: NVIDIA Corporation CK804 PCI Bridge [10de:oo5c](rev f2)
00:0a.0 Bridge [0680]:NVIDIA Corporation CK804 Ethernet Controller [10de:0057](rev f3)
        Subsystem: Elitegroup Computer Systems Device [1019:1b13]
        Kernel driver in use: forcedeth
        Kernel modules: forcedeth
00:0b.0 PCI bridge [0604]:NVIDIA Corporation CK804 PCIE Bridge [10de:005d](rev f3)
        Kernel driver in use:pcieport
        Kernel modules:shpchp
00:0c.0 PCI bridge [0604]: NVIDIA Corporation CK804 PCIE Bridge [10de:005d](rev f3)
        Kernel driver in use:pcieport
        Kernel modules:shpchp
00:0d.0 PCI bridge [0604]:NVIDIA Corporation CK804 PCIE Bridge [10de:005d](rev f3)
        Kernel driver in use:pcieport
	Kernel modules: shpchp
00:18.0 Host Bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon/Opteron] DRAM Controller [1022:1102]
	Kernel modules: amd64_edac_mod
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon/Opteron] Miscellaneous Control [1022:1103]
	Kernel driverin use:k8temp
	Kernel modules: k8temp
05:00.0 VGA comatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV630 [Radeon HD 2600 XT][1002:9588]
	Subsystem: PC Partner Limited Device [174b:2e42]
	Kernel driver in use:radeon
	Kernel modules:radeon
05:00.1 Audio device [0403]: Advanced micro Devices [AMD] nee Ati Rv630 audio device [Radeon HD 2600 Series]{1002:aa08]
	Subsystems:PC Partner Limited Device [174b:aa08]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel



I have done what the other links have sugested, now as find and try to connect to the internet I get a black screen and my whole screen goes fuzzy. lol all but my mouce.
I am not understanding, where did I go wrong???

---

### Post by traditionalist on 2012-05-24
Don't install any ATI drivers at all. Just use the generic drivers ( you dont need to do anything!).

This nearly drove me crazy. I have been using 12.04 for three weeks and since I managed to get it set up right it is absolutely fantastic, but it was not easy, I spent up to ten hours a day trying various stuff, until it all worked perfectly.

The second thing to do, once the machine is running is install Gnome Shell from the Ubuntu Software Centre;

[[IMG]http://img442.imageshack.us/img442/558/ubuntusoftwarecenter013.th.png[/IMG]]("http://img442.imageshack.us/i/ubuntusoftwarecenter013.png/")

and then uninstall unity. It was causing most of my problems and crashes. My system is now running stable and extremely well.

Use "Gnome Classic" at the log in panel.

I have switched completely from Windows to Ubuntu as a result of this, the system is fantastic once you get set up. but I still have Windows X64 Ultimate in a virtual box.

It is quite hard to get the information you need when starting, not least because there is tons of it available and a lot of it will do you no good.

---

### Post by recap on 2012-05-24
maybe try the update manger...?

---

### Post by bldrofshadows on 2012-05-25
> **traditionalist said:**
> Don't install any ATI drivers at all. Just use the generic drivers ( you dont need to do anything!).

This nearly drove me crazy. I have been using 12.04 for three weeks and since I managed to get it set up right it is absolutely fantastic, but it was not easy, I spent up to ten hours a day trying various stuff, until it all worked perfectly.

The second thing to do, once the machine is running is install Gnome Shell from the Ubuntu Software Centre;

[[IMG]http://img442.imageshack.us/img442/558/ubuntusoftwarecenter013.th.png[/IMG]]("http://img442.imageshack.us/i/ubuntusoftwarecenter013.png/")

and then uninstall unity. It was causing most of my problems and crashes. My system is now running stable and extremely well.

Use "Gnome Classic" at the log in panel.

I have switched completely from Windows to Ubuntu as a result of this, the system is fantastic once you get set up. but I still have Windows X64 Ultimate in a virtual box.

It is quite hard to get the information you need when starting, not least because there is tons of it available and a lot of it will do you no good.

one of my main issues is my usb 600n wireless card...
no internet. and bad Ethernet card.

---

### Post by bldrofshadows on 2012-09-28
solved, with new install of ubuntu
12.04

---

