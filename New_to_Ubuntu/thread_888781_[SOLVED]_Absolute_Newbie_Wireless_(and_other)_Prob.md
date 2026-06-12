---
title: "[SOLVED] Absolute Newbie Wireless (and other) Problems"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by CorvusViridis on 2008-08-13
Hi everyone, I'm new, this is my first post and I've only switched to Ubuntu (8.04) today.
After trying to find solutions to my problems in the faq's etc., I've decided to ask for help here. Here's the situation:

- I'm trying to connect to the internet via my school's wifi (wlan).

- My laptop has a BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller. When I was testrunning Ubuntu from CD, the OS complained about not having the right firmware for the driver installed (that's what I understood, at least), but after the complete switch from XP, I'm not getting that error message anymore, so I don't suppose that's the problem; I'm not finding anyway to confirm that, though. I can't read the terminal well enough yet ...

- I can get online using lan, but only if I tell Ubuntu to roam, not when I try manually. the wifi doesn't work when set to roam, or manually. I can't even tell if it's not trying to connect at all, or if the problem lies with my school's network, which is DHCP and hex key protected.

- Every time I use the network manager to turn the wireless on, the next time I open the manager it's turned off again.

Here's the output the guide to asking questions tells me to post:
klp@KLP-Cassiopeia:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8T890 I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8T890 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. [K8T890 North / VT8237 South] PCI Bridge
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.2 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0a.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

klp@KLP-Cassiopeia:~$ lsusb
Bus 005 Device 003: ID 18a5:0214  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c03e Logitech, Inc. Premium Optical Wheel Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

klp@KLP-Cassiopeia:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 10
       serial: 00:03:0d:35:0c:df
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.37.186 latency=64 maxlatency=64 mingnt=32 module=r8169 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:0c:f4:b7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

If anyone has any ideas about this, please help me. Maybe I'm overlooking something very stupid (the wireless switch on the outside of my laptop is turned ON, though), but maybe it's more complicated...

One other (smaller) problem: I can't seem to install the Adobe Flash Player (or one of the two other plugins Firefox suggests): If I try using the Firefox Plugin Finder Service and try to install one of the suggestions, I get a (long) error message, which doesn't help me:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy Release: The following signatures were invalid: NODATA 2

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/hardy/Release](http://de.archive.ubuntu.com/ubuntu/dists/hardy/Release)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.bz2](http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.bz2](http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2](http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.bz2](http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.bz2](http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.bz2](http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2](http://de.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.

I'm sorry this post is so long, but I would appreciate any help you could give me.

Thanks, CorvusViridis

---

### Post by cariboo on 2008-08-13
Have a look at this howto:

[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

Follow the howto exactly and don't try to jump any steps.

Jim

---

### Post by appi2012 on 2008-08-13
Go to System -> Administration -> Software Sources

Make sure all the checkboxes are checked on the first tab. (Not the CD one, though)
That might fix the problem with downloading flash player.
[_Click Here_]("apt:flashplugin-nonfree") to download it.
Also, let me get this straight, you have wireless, but not in your school network?

---

### Post by CorvusViridis on 2008-08-13
Thanks for your replies. I'll try the Software Sources right after writing this.
I don't think I have any wireless. But I don't believe there are any other strong ones in the area, so I'm only assuming the problem is with my receiving all wifi and not only my school's wifi.

I followed the HOWTO in [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102), but the only thing that shows up in the Hardware Drivers box is ATI accelerated graphics driver, which I can't enable either :-(

---

### Post by CorvusViridis on 2008-08-13
I think I can't download any packages at all. The software sources panel told me it needed to download new information about software, but then I again got a long error message:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: NODATA 2

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release: The following signatures were invalid: NODATA 2
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

(...)

W: Some index files failed to download, they have been ignored, or old ones used instead.

Any ideas?

---

### Post by CorvusViridis on 2008-08-13
Also, clicking on the link you posted, appi2012, just gets me an error message: Can't find flashplugin-nonfree. weird...

---

### Post by Ryadt on 2008-08-13
> **CorvusViridis said:**
> Also, clicking on the link you posted, appi2012, just gets me an error message: Can't find flashplugin-nonfree. weird...

Type in terminal```
sudo apt-get install flashplugin-nonfree
```

---

### Post by CorvusViridis on 2008-08-13
> **Ryadt said:**
> Type in terminal```
sudo apt-get install flashplugin-nonfree
```

Same problem, I guess:

klp@KLP-Cassiopeia:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

I think something's wrong, I can't seem to download any software correctly. Having a similar problem with the ATI graphics driver.

---

### Post by Ryadt on 2008-08-13
> **CorvusViridis said:**
> Same problem, I guess:

klp@KLP-Cassiopeia:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

I think something's wrong, I can't seem to download any software correctly. Having a similar problem with the ATI graphics driver.

```
sudo apt-get update && sudo apt-get upgrade
```
then try to reinstall.

---

### Post by CorvusViridis on 2008-08-13
> **Ryadt said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```
then try to reinstall.

Still more problems :-) Hmm, this is a learning experience:

klp@KLP-Cassiopeia:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
98% [Connecting to archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US
49% [2 Translation-en_US bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US               
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US               
33% [3 Translation-en_US bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US                 
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US             
25% [4 Translation-en_US bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US               
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]               
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US
22% [6 Translation-en_US bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_US             
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US     
18% [7 Translation-en_US bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_US       
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US       
15% [8 Translation-en_US bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_US         
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US     
13% [9 Translation-en_US bzip2 0] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg [189B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg [189B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release.gpg [189B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US
13% [Connecting to archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Translation-en_US            
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US   
12% [14 Translation-en_US bzip2 0] [Connecting to archive.ubuntu.com (91.189.88bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Translation-en_US      
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US     
11% [15 Translation-en_US bzip2 0] [Connecting to archive.ubuntu.com (91.189.88bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Translation-en_US        
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US   
10% [16 Translation-en_US bzip2 0] [Connecting to archive.ubuntu.com (91.189.88bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Translation-en_US      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release [58.5kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                          
  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
87% [19 Sources bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources                    
  Sub-process bzip2 returned an error code (2)
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources                   
87% [Connecting to archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources                      
  Sub-process bzip2 returned an error code (2)
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                  
87% [21 Packages bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                      
  Sub-process bzip2 returned an error code (2)
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                 
87% [22 Packages bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages                    
  Sub-process bzip2 returned an error code (2)
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages                  
87% [23 Packages bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Packages                 
  Sub-process bzip2 returned an error code (2)
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages            
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources             
87% [24 Packages bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Packages           
  Sub-process bzip2 returned an error code (2)
87% [25 Sources bzip2 0] [Waiting for headers]                      20.3kB/s 0sbzip2: (stdin) is not a bzip2 file.
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources                   
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources             
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/restricted Sources                
  Sub-process bzip2 returned an error code (2)
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources               
88% [26 Sources bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/main Sources                 
  Sub-process bzip2 returned an error code (2)
88% [27 Sources bzip2 0] [Waiting for headers]                      20.3kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Sources                
  Sub-process bzip2 returned an error code (2)
88% [28 Sources bzip2 0] [Waiting for headers]                      20.3kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Sources                  
  Sub-process bzip2 returned an error code (2)
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages              
88% [29 Packages bzip2 0] [Connecting to archive.ubuntu.com (91.189.88.45)]bzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/universe Packages             
  Sub-process bzip2 returned an error code (2)
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages            
88% [30 Packages bzip2 0]                                           20.3kB/s 0sbzip2: (stdin) is not a bzip2 file.
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security/multiverse Packages               
  Sub-process bzip2 returned an error code (2)
Fetched 35.7kB in 7s (4780B/s)                                                 
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: NODATA 2

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release: The following signatures were invalid: NODATA 2
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by nicedude on 2008-08-13
Hello and although you gave some nice info with your first post, I can think of a few more that might help you in the future as you are trying to troubleshoot this or other Wifi problems. My guess is though that you first will need to read a broadcom guide for your model and follow that to get your driver working right & then you may or may not have further trouble with setting up a WPA connection ( your school will most certainly use WPA encryption to secure its Wifi network which may cause you further headaches ). Here are some commands that might help you figure this out

Run this command to list wifi enabled adapters
iwconfig

This command will tell you if there are any wireless networks nearby and will also tell you your adapter is at least able to see things

iwlist ath0 scan 

you must change the ath0 in that command to whatever your wifi adapter is called when you ran the iwconfig command.


Hope this helps

---

### Post by CorvusViridis on 2008-08-13
I don't know what I did, but something made the wireless driver show up in the hardware drivers, where it wasn't 10 minutes ago. However, when I tell it to "fetch and install firmware", I get this error message:

E: b43-fwcutter: subprocess post-installation script returned error exit status 2

I will reboot once more to see whether it might make a difference. Does one DO that in Linux?

---

### Post by Ryadt on 2008-08-13
Can you go in System > Administration > Software sources, click on 'Download from', choose other then select best server. Then retry the commands.

---

### Post by CorvusViridis on 2008-08-13
> **Ryadt said:**
> Can you go in System > Administration > Software sources, click on 'Download from', choose other then select best server. Then retry the commands.

Tried it; got the same error messages, only this time with the new server. The problem seems to be on my side. No idea what it is though.

@all:
I have to go now, but I'll be back here first thing in the morning, and I really appreciate your effort in helping me! Thanks

---

### Post by Ryadt on 2008-08-13
Can you post ```
sudo gedit /etc/apt/sources.list
```

---

### Post by appi2012 on 2008-08-13
First of all, you won't be able to download any software and update the available software list unless you have wifi. So, if are connected to the  internet through a cable, you have to type this in terminal:
```
sudo apt-get update
```
That will reload the list of available software. Now, the link should work, and it should install flash player. (Assuming you have all the checkboxes in software sources checked)

For wireless, you may have to resort to ndiswrapper (a utility that runs windows XP drivers in linux) 

See this post for a guide: [http://ubuntuforums.org/showpost.php?p=5384727&postcount=7](http://ubuntuforums.org/showpost.php?p=5384727&postcount=7)

Follow it and make sure you use XP drivers. You should be able to find them on the internet.

---

### Post by CorvusViridis on 2008-08-14
> **Ryadt said:**
> Can you post ```
sudo gedit /etc/apt/sources.list
```

There it is:

# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
deb-src [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy universe
deb [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe #Added by software-properties
deb [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/) hardy-security multiverse

---

### Post by CorvusViridis on 2008-08-14
> **appi2012 said:**
> First of all, you won't be able to download any software and update the available software list unless you have wifi. So, if are connected to the  internet through a cable, you have to type this in terminal:
```
sudo apt-get update
```

I tried, and got this:

klp@KLP-Cassiopeia:~$ sudo apt-get update
[sudo] password for klp: 
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy Release.gpg
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy/main Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy/restricted Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy/universe Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy/multiverse Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy-updates Release.gpg
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy-updates/main Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy-updates/restricted Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy-updates/universe Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy-updates/multiverse Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy-security Release.gpg
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy-security/main Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy-security/restricted Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy-security/universe Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Err [http://www.mirrorservice.org](http://www.mirrorservice.org) hardy-security/multiverse Translation-en_US
  Could not resolve 'www.mirrorservice.org'
Reading package lists... Done           
W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Failed to fetch [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'www.mirrorservice.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
klp@KLP-Cassiopeia:~$ 

> **appi2012 said:**
> That will reload the list of available software. Now, the link should work, and it should install flash player. (Assuming you have all the checkboxes in software sources checked)

I tried, but after the error messages, I didn't think it would work. So I checked the software sources box again. All boxes are checked, except for the CD, AND the Source Code Box, which can't be checked, only marked with a [-], which it is. I then tried to find the best download server again, as I was advised yesterday, and I got the message "No suitable download server was found. Please check your internet connection."

So, something seems to be wrong with my downloading. I AM connected to the internet via LAN, I am using this connection to post this post.

---

### Post by CorvusViridis on 2008-08-14
> **CorvusViridis said:**
> I then tried to find the best download server again, as I was advised yesterday, and I got the message "No suitable download server was found. Please check your internet connection."

I tried this again. It got me a download server. When I then close the Sources Box, I get the message: "The information about available software is out-of-date. To install software and updates from newly added or changed sources, you have to reload the information about available software.You need a working internet connection to continue." I apparently have some kind of internet connection, so I continue. Then I get the message:

"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

And the further details:

"GPG error: [http://mirror.csclub.uwaterloo.ca](http://mirror.csclub.uwaterloo.ca) hardy Release: The following signatures were invalid: NODATA 2GPG error: [http://mirror.csclub.uwaterloo.ca](http://mirror.csclub.uwaterloo.ca) hardy-updates Release: The following signatures were invalid: NODATA 2GPG error: [http://mirror.csclub.uwaterloo.ca](http://mirror.csclub.uwaterloo.ca) hardy-security Release: The following signatures were invalid: NODATA 2Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/main/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/restricted/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/main/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/main/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/restricted/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/restricted/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/multiverse/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/universe/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/universe/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/universe/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy/multiverse/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/restricted/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/universe/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/universe/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-updates/multiverse/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/main/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/restricted/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/restricted/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/main/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/multiverse/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/multiverse/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/universe/source/Sources.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/universe/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/universe/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.bz2](http://mirror.csclub.uwaterloo.ca/ubuntu/dists/hardy-security/multiverse/binary-amd64/Packages.bz2)  Sub-process bzip2 returned an error code (2)
Some index files failed to download, they have been ignored, or old ones used instead."

:-(

---

### Post by CorvusViridis on 2008-08-14
Does it make any sense to completely reinstall ubuntu? Or will I just sit there again with the same problems?

---

### Post by Ryadt on 2008-08-14
Have a look at these thread 
[http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error](http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error)
[http://ubuntuforums.org/showthread.php?t=192770](http://ubuntuforums.org/showthread.php?t=192770)
Hope this solves it.

---

### Post by CorvusViridis on 2008-08-14
> **Ryadt said:**
> Have a look at these thread 
[http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error](http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error)
Hope this solves it.

Wow, this seems to be exactly my problem. My school is also using the Dans Guardian they are talking about in the post. I'm not exactly sure how to implement the solution, though... I will see if I manage to change to ftp: in the sources.list file ...

THANKS!

---

### Post by CorvusViridis on 2008-08-14
I'm not sure about the sources list yet, but I asked it-support to allow complete access to one of the mirrors without regard to .bz2, and it's working!

[http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error](http://ubuntuforums.org/showthread.php?t=9944&highlight=gzip+bzip2+error) had the answer! Thanks a lot, Ryadt! I'm not sure if EVERYTHING is working now, but for now I've got 105 updates to download, and it's working! So I will mark this as solved and open up a new thread in case of need.

Again: Thank You!

---

### Post by Ryadt on 2008-08-14
Your welcome...Glad to have helped ;)

---

